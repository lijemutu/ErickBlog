---
title: "Amazon Extension"
date: 2022-11-16T22:05:26-06:00
draft: false
---

## Amazon Easy Search Extension

My father has the job of looking for code products in amazon.com, those are typically sent over messaging platform like Whatsapp, then after he does some research over the product, he paste the gathered information into said messaging platform and into a google sheets shared document.

### Solving the problem
Copy the product code, open new tab, paste and search the code in searchbar, enter first result, these are the steps involved into the manual process of collecting info from product codes.

We need a shortcut for these steps, the easiest I could think of was selecting the product code, enter a command and a popup window will appear with the amazon page search of said code.

To accomplish this I needed to develop a Chrome extension (my father's preferred browser) the chrome developer tutorials were straightforward and gave a nice jumpstart to start coding.

### The algo
Now that the problem has broken down into two tasks, we can work on them.

First we need to get the text selection from the browser and use it in our script. This code was used given the latest chrome API:

```
try {
      result = await chrome.scripting.executeScript({
        target: {tabId: tab.id},
        function: () => getSelection().toString(),
      });
    } catch (e) {

      console.log(e)
      return; // ignoring an unsupported page like chrome://extensions
    }
```
Using the ```chrome.scripting.executeScript``` method we can execute ```getSelection().toString()``` and get the content of our selected text in our current tab. Using try catch logic we can handle errors.

Now that we have the string of our selected text, we can open a new popup windows with the url of the amazon search product:

```
chrome.windows.create({
      url: 'https://www.amazon.com.mx/s?k=' + result[0].result,
      type: 'popup', width: 1000, height: 800,
   });
```

This code opens a new windows and goes directly to amazon with the search pointing to our selected text.

Both functions are called sequentially and achieves the desired goal. For quick triggering of this process we bound ``` Ctrl+M ``` hotkey to the process.

This is the full code with the manifest.js file.

### Manifest.json

```
{
  "manifest_version": 3,
  "name": "Amazon Easy Search",
  "description": "Quick search on amazon page, Select text and Ctrl+M",
  "version": "1.0",
  "icons": {
    "64": "images/CTRL+M64.png",
      "32": "images/CTRL+M32.png",
      "16": "images/CTRL+M16.png"
  },
  "background": {
    "service_worker": "background.js"
  },
  "action": {
    "default_icon": {
      "64": "images/CTRL+M64.png",
      "32": "images/CTRL+M32.png",
      "16": "images/CTRL+M16.png"
    }
  },
  "permissions": ["scripting", "activeTab","tabs"],
  "commands": {
    "_execute_action": {
      "suggested_key": {
        "default": "Ctrl+M",
        "mac": "Command+M"
      }
    }
  }
}


```

### background.js

```
// Copyright 2022 Google LLC
//
// Licensed under the Apache License, Version 2.0 (the "License");
// you may not use this file except in compliance with the License.
// You may obtain a copy of the License at
//
//     https://www.apache.org/licenses/LICENSE-2.0
//
// Unless required by applicable law or agreed to in writing, software
// distributed under the License is distributed on an "AS IS" BASIS,
// WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
// See the License for the specific language governing permissions and
// limitations under the License.

chrome.runtime.onInstalled.addListener(async(tab) => {
});

chrome.action.onClicked.addListener( async(tab) => {
    try {
      result = await chrome.scripting.executeScript({
        target: {tabId: tab.id},
        function: () => getSelection().toString(),
      });
    } catch (e) {

      console.log(e)
      return; // ignoring an unsupported page like chrome://extensions
    }
    console.log(result[0].result);
    console.log('message sent',result[0].result);
    chrome.windows.create({
      url: 'https://www.amazon.com.mx/s?k=' + result[0].result,
      type: 'popup', width: 1000, height: 800,
   });
});

```

### Future features

This can be extended by selecting multiple strings and opening one popup window each or multiple tabs into a single popup window.