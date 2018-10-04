# Omega Dev Playbook


What follows is a description of development practices which should improve the quality of our work, reduce risk around deployments and increase your happiness.

## Development practice

### Use a dependency management system

For any application you should not copy any dependencies to the project codebase, 
rather use dependency management tools to get the required project dependencies, declared in manifest, from the server.
e.g. Maven, npm, yarn


### Keep it simple

Use a consistent coding style
Keep it DRY
Break out into separate methods
Refactor


### Think about security

As easily as an XSS attack can be carried out against an unprotected website, protecting against them is just as easy.

Never trust data coming from the user or from any other third party sources. Every bit of data must be validated on input and escaped on output. This is the golden rule of preventing XSS.

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


### Write accpetance tests

Acceptance tests are user stories turned into code. This code is run against the application. When executed for the first time, the test will fail. The developer writes application code until the test passes.

The code is then run on the Continuous Integration server to make sure the acceptance test still passes in an environment that matches the production environment.

Meanwhile, the code is pushed to the staging environment and the developer and customer representative smoke test it in the browser.

When the acceptance test is green for the CI server and you and any other designers, developers, or clients are satisfied that the jobs story is complete on staging, the feature can be deployed to production at will. This can result in features being pushed to production very frequently, and therefore more value is being delivered to customers sooner.


### Coding style

Prefer ES6 classes over prototypes.
Use strict equality checks (=== and !==) except when comparing against (null or undefined).
Prefer arrow functions =>, over the function keyword except when defining classes or methods.
Use semicolons at the end of each statement.
Prefer single quotes.
Use PascalCase for classes, lowerCamelCase for variables and functions, SCREAMING_SNAKE_CASE for constants, _singleLeadingUnderscore for private variables and functions.
Prefer template strings over string concatenation.
Prefer promises over callbacks.
Prefer array functions like map and forEach over for loops.
Use const for declaring variables that will never be re-assigned, and let otherwise.
Avoid var to declare variables.
Use a trailing comma after each item in a multi-line array or object literal, including the last item.



## Code reviews

Code reviews offer many benefits:

The whole team learns about new code as it is written
Mistakes are caught earlier
Coding standards are more likely to be established, discussed, and followed

Moves code failure to earlier in the development process. 
It's better to have a failing test on your development machine than in production. 


## Refactoring

The process of improving the design of existing code without altering its external behavior. It's a critical step in the process, but often overlooked. 
Make time for it.


## Test across a range of browsers

We default to supporting the newest and the last previous two releases of popular browsers (Edge, Safari, Chrome, Firefox, and Android Browser) for mobile and desktop devices. 
We also support Internet Explorer 11 but not older versions of Internet Explorer, as Microsoft no longer supports these browsers.

Older versions are much harder, more time consuming and hence more expensive to design for, develop for and support.

In limited special cases, user demographics will dictate that supporting a less common or older version of a browser is required. 
Those special cases should be identified early on so we can plan for additional time to support the version.

We use
Browserstack

## Browser matrix






# Deployment








