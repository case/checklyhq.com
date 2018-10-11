---
title: Installation
weight: 2
menu:
  docs:
    parent: "Puppeteer Recorder"
---

To install Puppeteer Recorder, go to the [Chrome Webstore](https://chrome.google.com/webstore/detail/puppeteer-recorder/djeegiggegleadkkbgopoonhjimgehda)
and install it as follows:

![](/docs/images/browser-checks/chrome-webstore.png)

1. Navigate to the [Chrome Webstore](https://chrome.google.com/webstore/detail/puppeteer-recorder/djeegiggegleadkkbgopoonhjimgehda) with your Chrome browser.
2. Click the "Add to Chrome" button. You will see a camera icon appear in your toolbar.
3. Clicking the camera icon will pop open Puppeteer Recorder.

![](/docs/images/browser-checks/puppeteer-recorder-installed.png)

## Setup for Checkly

By default, Puppeteer Recorder generates code that is wrapped in an `async` helper function. This is handy when you want
to save the generated code directly to a file on your local machine and run the code with a simple `node myscript.js`.

However, Checkly already wraps your code when running browser checks. You therefore need to uncheck the option **wrap code in 
async function**. After this, all code generated by Puppeteer Recorder can be directly copy & pasted into Checkly.

![](/docs/images/browser-checks/recorder_asyncwrap.png)


## Options

Open the options tab by clicking the cog wheel icon. In this tab you will find a set of configuration options that impact
how Puppeteer Recorder generates Puppeteer code. Most options are self explanatory, byt two very important options are:

- **add waitForNavigation lines on navigation**: this determines if extra statements are added to wait for browser reloads
when navigating from page to page. Turning this options off can result in failing or hanging scripts.
- **add waitForSelector lines before every page.click()**: Setting this options generates a `waitForSelector` statement before
each `page.click()` statement, effectively always guarding for clicking on elements that are not (yet) available on a page.

It is recommended to leave both options checked in all cases.