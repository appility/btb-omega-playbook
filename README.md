
# Omega Dev Playbook

What follows is a description of development practices which should improve the quality of our work, reduce risk around deployments and increase our happiness.

## Development practice

### Use a dependency management system

For any application you should not copy any dependencies to the project codebase, rather use a dependency management tools to get the required project dependencies, declared in manifest, from a server.
e.g. Maven, npm, yarn


### Keep it simple

Use a consistent coding style
Keep it DRY
Break long methods out into separate methods
Refactor


### Think about security

As easily as an XSS attack can be carried out against an unprotected website, protecting against them is just as easy.

**Never trust data coming from the user** or from any other third party sources. Every bit of data must be validated on input and escaped on output. This is the golden rule of preventing XSS.

https://www.owasp.org/index.php/XSS_%28Cross_Site_Scripting%29_Prevention_Cheat_Sheet

Don't put secret keys in source code, store them in environment variables.


### Use a linter

This catches syntactical errors early.

Add linting to the CI so errors cannot be progressed beyond local development machine.


### Write unit tests

Unit tests are really just the documentation of how your code should behave. 
If you cannot tell from looking at the code what it is trying to do, you at least have the unit tests to tell you the story. 
This is especially helpful if you are working with someone else's code or if you're returning to a codebase, how well will you remember all the edge cases in six months?

Add the running of unit tests to the CI so code that breaks tests cannot be progressed beyond local development machine.


### Write acceptance tests

Acceptance tests are user stories turned into code. This code is run against the application. When executed for the first time, the test will fail. The developer writes application code until the test passes.

The code is then run on the Continuous Integration server to make sure the acceptance test still passes in an environment that matches the production environment.

Meanwhile, the code is pushed to the staging environment and the developer and customer representative smoke test it in the browser.

When the acceptance test is green for the CI server and you and any other designers, developers, or clients are satisfied that the jobs story is complete on staging, the feature can be deployed to production at will. This can result in features being pushed to production very frequently, and therefore more value is being delivered to customers sooner.


### Coding style

#### Javascript

 - Prefer ES6 classes over prototypes.
 - Use strict equality checks (=== and !==) except when comparing
   against (null or undefined)
 - Prefer arrow functions => over the function keyword except when
   defining classes or methods.
 - Use semicolons at the end of each statement.
 - Prefer single quotes.
 - Use PascalCase for classes  lowerCamelCase for variables and
   functions, SCREAMING_SNAKE_CASE for constants
   _singleLeadingUnderscore for private variables and functions
 - Prefer template strings over string concatenation
 - Prefer promises over callbacks.
 - Prefer array functions like map and forEach over for loops.
 - Use const for declaring variables that will never be re-assigned, and
   let otherwise. Avoid var to declare variables.
  - Use a trailing comma after each item in a multi-line array or object
   literal, including the last item

## Code reviews

Code reviews offer many benefits:

The whole team learns about new code as it is written
Mistakes are caught earlier
Coding standards are more likely to be established, discussed, and followed

Moves code failure to earlier in the development process. 
It's better to have a failing test on your development machine than in production. 


## Refactoring

This is the process of improving the design of existing code without altering its external behavior. It's a critical step in the process, but often overlooked. 
Make time for it.


### Test across a range of browsers

We default to supporting the newest and the last previous two releases of popular browsers (Edge, Safari, Chrome, Firefox, and Android Browser) for mobile and desktop devices. 
We also support Internet Explorer 11 but not older versions of Internet Explorer, as Microsoft no longer supports these browsers.

Older versions are much harder, more time consuming and hence more expensive to design for, develop for and support.

In limited special cases, user demographics will dictate that supporting a less common or older version of a browser is required. 
Those special cases should be identified early on so we can plan for additional time to support the version.

(See Browser Matrix)
(See BT Business User demographics)

### Create a browser matrix

This helps:
To limit the scope (and cost) of web development to a specific set of browsers and devices.
To limit the scope (and cost) of testing to specific set of browsers and devices.

A browser matrix can also be used during project planning to help the team decide what technical approach to take. If you have a high level of IE 8/9/10/11 usage, you might want to shy away from building a JS-heavy app. Likewise, if you have a high percentage of mobile users you might decide to prioritise mobile UX or performance.

Crafting a browser matrix is not an exact science. But taking a data-driven approach can help you to make informed decisions during development and testing. It’s also important to update your matrix on a regular basis, to keep track of upcoming browsers (e.g. Edge), declining browsers (e.g. IE) and mobile trends. An up-to-date browser matrix helps you and your team to develop and test with users in mind. It also ensures that your technology and design choices reflect market realities.

**Definition of support levels**

Browser support falls into one of three classes:

Level A:  Aim to proactively fix these browsers and provide an equal experience across all.
Level B:  Make a best effort to ensure there is at least one way to do any action.
Level C:  No guarantees. We will accept fixes, but only if they are low risk. This is the default unless a browser/version is listed.


### BT Business User demographics

#### General observations

Desktop usage is slightly higher than usual, 66.3% compared to 51.89%
Mobile Phone usage is lower than usual, 27.6% compared to 36.4%
Tablet usage is lower than usual, 6.1% compared to  11.71%

#### Desktop

Of desktop usage Windows on desktop Windows 10, Windows 8.1 & Windows 7 
make up 83.8%
( either IE11 or Edge is available in those )

#### Mobile

By far the most popular browser is Mobile Safari 11.0, it acounts for 42.8%, next next most popular Chrome Mobile 68.0 at 14.6%

Chrome Mobile v67 and up and Safari Mobile v10 up combined, account for 85.6& of mobile traffic

The last two versions of Samsung Browser (based on Chromium)
7.4 & 7.2 account for 5.7% of mobile traffic

 *all stats year to Sept 2018
 
[\[Browser stats - business.bt.com - generated Oct 2018\]](https://docs.google.com/spreadsheets/d/1vNsC1HfRzo3Eg-Onwd-TqKnApFw7fWhxKSrYQXzgT2Q/edit?usp=sharing)

####  Git

Use the Gitflow Workflow
https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow

Gitflow is ideally suited for projects that have a scheduled release cycle. This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact. In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.


### Deployment









