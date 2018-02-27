# Motivation

- Save snapshots of your work on the cloud so
  - you can share it with other people
  - invite others to collaborate
  - if something goes wrong, go back to a version that worked.


# Example

> "Continuous Integration is the process of merging changes from developer’s code quickly back into the release candidate code, rather than waiting until all changes are made in all developers’ code."

 Assume three developers (Jane, Bob, and Sandra) are working on a data product that accepts a picture input from a user’s cell phone camera, runs an image recognition algorithm against it, and returns a label to the user – something like “Cat” or "Pizza".  The main part of the code is created, and “checked in” to a code repository system like `git`. This is called the “main branch” – it’s where all the work is complete as of a given point in time.  

 - Jane uses a git command to copy *all* of the code in the main branch to her local system. She then creates a “branch” of her own, perhaps calling it “JaneBranch” that now has a copy of the code as well. She then begins to alter the code in JaneBranch to have a better User Interface for the program. At this point, the master branch has not changed, and Bob and Sandra have done the same on their systems, building new features or working on issues.

- After she makes changes and tests to make sure they work, she can 'request' that her code be integrated (or 'pulled') into the master branch using something called a “Pull Request”. The request is reviewed, and if approved, her changes go to the master branch. If Bob and Sandra have not 'pulled' these updates down, they are still working on “old” code.

- This works fine until you have lots of changes, some of which might conflict. For instance, if Jane alters the code in the User Interface that sends the image to the prediction algorithm, Bob might have a dependency on that call. That would cause a break. And then if Sandra’s code depended on things that both Bob and Jane are doing, that would also cause her code to break. If they all waited to merge to the main branch, all these errors (and probably more) would show up at once, like a pile-up on a freeway.

- To avoid _merge conflicts_, as soon as Jane’s code tests well, it should be pushed into the master branch, and Bob and Sandra should pull that new master branch back down, to test their code against. And as soon as Bob has made a change, he should also push that back into the master branch, as should Sandra. The key is that with little changes being merged back into the main branch, failures show up faster. If you fast-forward that to almost any functional change being made in any part of the code, you get Continuous Integration.

If changes “break” our inputs or outputs, we need to know that as soon as possible. In some cases, it can be as dramatic as retraining the original model or even creating a new one using a different algorithm. In practice most development shops will put Automated Testing together with Continuous Integration, but in a Data Science algorithm, it’s a bit tricky to create an automated test
