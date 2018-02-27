## CI

> "Continuous Integration is the process of merging changes from developer’s code quickly back into the release candidate code, rather than waiting until all changes are made in all developers’ code."

- CI promotes collaborative working
- Developers work on copies of the source code to develop features/fix issues
- Changes must be integrated into the master asap
- CI is enabled by `git` and _automated testing_ to ensure that one developer's changes don’t have unwanted impact up- or down-stream


## CD

- is about automating deployments
- Changes pushed into the master are tested, and pushed out to the end-user automatically
- Enabled by Jenkins that looks for changes to the source, triggers tests, builds the software and pushed it out
