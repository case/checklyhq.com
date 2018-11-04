---
title: Environment variables
weight: 3
menu:
  docs:
    parent: "Browser Checks"
    identifier: variables-browser-checks
---

When creating browser checks, you probably run some code locally, store it in a Git repo or copy and paste it around
a bit. This means the credentials in the script are at risk of being exposed.  
You should therefore **replace any confidential data in your browser check scripts with environment variables.**  

## Managing variables

For browser checks, you can create environment variables at two hierarchical levels:

- **Local** or check level:
- **Global** level

Local variables are added on the **Variables** tab for each browser check. Any data you "lock" is
encrypted at rest and in flight on our back end and is only decrypted when needed.

![add local variables](/docs/images/browser-checks/add-local-variable.png)


Global variables are added on the **Variables** tab in the **Account** section. The variables stored here are globally accessible 
throughout Checkly, hence the "Global environment variables" title*. 

![add global variables](/docs/images/api-checks/add-variables.png)

{{<info >}}
Whenever possible, store variables at the global level. This DRY's up your code.
{{</info>}}

## Accessing variables

Both local and global environment variables are accessible in your code using the standard Node.js `process.env.MY_VAR` notation. 
For example, the code snippet below show how you can log into Github. We have more [examples of login scenarios on this page.](/docs/browser-checks/login-scenarios/)

```js
const browser = await puppeteer.launch()
const page = await browser.newPage()
await page.goto('https://github.com/login')
await page.type('#login_field', process.env.GITHUB_USER)
await page.type('#password', process.env.GITHUB_PWD)
await page.click('[name="commit"]')
browser.close()
``` 

## Variable hierarchy

As browser checks are scheduled, Checkly merges the local and global environment variables into one data set and exposes them
to the runtime environment. During merging, any local variable with the same name as a global variable **overrides the global variable.**  

Or in another words, local variables trump global variables.  

You can make use of this by providing a default value for a specific variable at the global level, but allow that variable to 
be overridden at the local level.

> *We are working on a "Group" feature, where we will allow variables per group of checks for finer grained control. This is why the variables in the account section are explicitly named "Global"


