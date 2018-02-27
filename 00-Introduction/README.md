## What is Software?

- formalizes and abstracts the implementation details of functionality away from the user
- exposes well-defined, easy-to-use interface (well understood inputs and outputs) to the user
- reliable because reproducible
- objectively, software is a collection of
  - modules (which are collections of functions/classes)
  - documentation (syntax and examples/tutorials)

  Thinking sequentially, the software engineering process looks something like this:

 Design -> Infrastructure setup -> Code -> Build -> Test -> Package -> Release -> Monitor

 With a few exceptions, that’s how software is done. Data Science is somewhere in there during the Code phase, usually. And in most cases, there are clearly defined boundaries for what gets done by whom. For instance, developers write the code after the business sends over requirements. The deployment team handles packaging and releasing. And the operations team (Ops) handles monitoring and updating. Maybe it’s a little different in your organization, but in general each team has an area they are responsible for. And that's mostly all they focus on.

## Motivation, or, Why Models go Unused?

- Stakeholders want to address a business problem in a data driven manner, so they contact you.
- Usually, you follow OSEMN or CRISP-DM, start with understanding the data, feature engineering and model selection.
- You present the results to your clients using PowerPoints slides. They all say 'Great job', and the slides remain unused.
- On the other hand, IT just created an iPhone app that lets them filter some reports in real-time. They use it daily.

> Often in enterprises, ML models go unused because the tools used by Data Scientists differ from the ones Software Engineers  use to create production ready applications.

In most cases, the engineers don’t even have an understanding of Data Science techniques or even languages like R or SAS - just like most data scientists don't know how to build applications in React or Play.


## Why Should You Care?

Data scientists often come from diverse backgrounds and frequently don't have much, if any, in the way of formal training in computer science or software development. But sooner or later, they find themselves talking to DevOps/Engineering and then these things happen?

> _DS: Can you please take my notebook and put that model into production?_
_SE: Wait, did you just check your code without tests into the master without a code review! It won't work?_
_DS: Checked my model without what into what!? Why do I need that? It works on my machine!_

Let's face it: **Data Scientists do not know how to collaborate effectively.**
Many have only ever worked alone or in tiny groups and they just don't know how to write code in an environment where many people will be looking at, trying to understand and using/applying your code or the output produced by your code.

It is a little unnerving to have to check your code into a repository when most data scientists are used to keeping their code on their hard-drive or on Dropbox.

- Any one can code. That university course/MOOC you took taught you **syntax**. But there is a lot more to coding than merely assembling a set of instructions in a programming language.
- Data Science students are not taught good coding practices or effective methodologies to collaborate with other people.
- What software engineering aims to accomplish is making the code portable, concise, relatively bug free, secure, performant within given constraints, and reusable, with limited man-power and budget.
- Proper software engineering is an art + science on to it self, of which coding skills are an important but nonetheless only a small piece.
- The code you write ...
  - It may not be portable on account of using non-portable APIs/Libraries
  - It may not be optimized/concise and as a result non performant at scale.
  - It may have a large surface area for bugs and security vulnerabilities.
  - It may not be maintainable in the long run
  - It may prevent you from reproducing your results in the future

## Motivations

> Help data scientists build data products through collaborative-reproducible research, taking advantage of the tools available in our ecosystem.
Move from Exploratory Data analysis in notebooks to a classic Reproducible Software Engineering workflow where you have Python Packages with tools other people can download, import and use.

- Make life easier for other people and your future-self.
  - If your work is organized, people trying to understand your work will save more time than you'd invest in tidying up.
  - Moreover, as time goes on, you may forget the details about what you are working on now. So, tidy up now and thank yourself later.  
- Most data scientist are heavily into the habit of just sharing Jupyter notebooks. Jupyter notebooks are good for self-contained exploratory analyses, but notebooks alone are not effective to create a product.


## Workflow

- Typical Data Science Workflow follows OSEMN
  - Obtain, Scrub, Explore, Model, INdustrialize
  - One tidy way to do this: keep a Jupyter notebook for each stage
  - But notebooks aren't production-environment friendly
    - most of your colleagues in DevOps won't even know how to open a .ipynb file

- We wish to
  - Write Exploratory Code in Notebooks
    - increases code complexity
  - Package/Refactor to Production Code in Python Files
    - decreases complexity by organizing and moving exploratory code into the production codebase

> Iterate over Explore-Package cycles until you reach the DoD.

- Benefits
  - Engineers/DevOps will love you
  - Future-you will love you (automation everywhere!)
  - ipynbs are JSON files, are not git-friendly to spot diffs

## Our Workflow

- BEFORE
  - Get Infrastructure
    - Remote Machine (Big RAM vs. Cluster)
    - Docker
    - Environment
  - Get Data
    - Flat Files
    - Database Connections
  - Get Code
    - if exists, Clone/Branch a repository
    - if not, use a Cookiecutter template

  - DURING
    - Write Exploratory (messy) Code in Notebooks
    - Package Tidy Code into Modules
      - Write Documentation
      - Write Tests
      - Automate
    - Maintain list of dependencies
    - Rinse. Repeat.

  - AFTER
    - Automate deployment pipeline
    - Build an API
    - Publish reports

## References

  - http://engineering.pivotal.io/post/api-first-for-data-science/
