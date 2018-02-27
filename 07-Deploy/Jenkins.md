## Jenkins

- In a nutshell, Jenkins is an _advanced scheduler._
- It triggers tasks on connected machines by reacting to events
  - Typically on source code changes or time events.
- Jenkins allows you to introduce and automate tasks, increasing productivity and quality of your pipeline.


### Example: Using Jenkins to check if our application/package builds successfully.

We automate the installation and deploy to a production-like test environment using Jenkins for every single commit to the package's source code. Tests ensures that changes made don't break things.

###

A short list of things we can delegate to Jenkins

1. Static analysis of code quality (lint and warnings)
2. Unit tests, including coverage
3. Automatic deployment of built software to application servers
4. Functional tests (with real GET/POST requests)
