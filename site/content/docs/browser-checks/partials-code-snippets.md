---
title: Partials and code snippets
weight: 5
menu:
  docs:
    parent: "Browser Checks"
---

You can reuse commonly used parts of code by referencing code snippets in any browser check. To do this, you use the 
[Handlebars](https://handlebarsjs.com/partials.html) partial notation `{{> my_code_snippet }}`.

This comes in very handy when you have multiple browser checks targeting the same site or web app that share a:
 
- common login procedure 
- common navigation flow
- common setup and/or teardown procedures

Using partials is very straightforward. Any code snippets are just copied inline as is.

### Example: Github login

Say we want to validate some parts of the Github website only available to logged in users. We want to have separate, small
browser checks to have granular feedback whether each part functions.  

1. Create a snippet named **github_login** in the "code snippets" section with the code below.

    ```javascript
    const puppeteer = require('puppeteer')     
    const browser = await puppeteer.launch()
    const page = await browser.newPage()
    
    await page.goto('https://github.com/login')
    await page.type('#login_field', process.env.GITHUB_USER)
    await page.type('#password', process.env.GITHUB_PWD)
    await page.click('[name="commit"]')
    ```

    Notice we are referencing the `GITHUB_USER` and `GITHUB_PWD` environment variables. All environment variables are available
    in partials / snippets, just like in "normal" browser check scripts. Your snippet should look like the screen shot below.

    ![browser check code snippet](/docs/images/browser-checks/code-snippet.png)

2. Create a new browser check. Reference the code snippet you just created as a partial. After this, just continue with the normal check.
During execution, the code snippet will be inlined before the script is run.

    ```javascript   
    {{> github_login}}
    
    // your normal check code
    await page.waitForSelector('.application-main')
    await page.click('.header-search-input')
    ```
