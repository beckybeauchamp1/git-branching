# Git-Branching

## Learning Objectives

- Explain what a branch is in git
- Create, merge and delete branches on local and remote repositories
- Describe how branching and merging allows for collaboration during development
- Describe Github Workflows using issues, branches, and pull-requests
- Resolve a merge conflict

## Opening Framing (5 min; 10:00-10:05)

Quickly review the basics of git:

1. What is the most common workflow for committing while working
locally?

2. What commands are used to share changes (commits) between local and remote repos?

3. Describe the differences between a fork and a clone.

4. What are the differences between Git and Github?

---
> Answers:

> Question 1:
  1. $ git init
  2. $ git add <file-name>
  3. $ git commit -m "commit message"

> Question 2:
  1. Add Remote Repo: $ git remote add [remote_name] <remote_repo_url>
  2. Push Commits: $ git push origin [branch_name]
  3. Pull Changes/Commits: $ git pull origin [branch_name]

> Question 3:
  1. Fork: make a copy of a repo on github under a different account, used for OSS collaboration
  2. Clone: download an entire remote repository, to be used as a local repository

> Question 4:
  1. Git: Git is the version control software we use locally on our computers in order to keep track of our files, directories, and our modifications to them in a central repository.
  2. GitHub is a public hosting site for storing repositories. It's a place where all of our repos are stored remotely on a server.

## What are Branches? (5 min; 10:05-10:10)

  A branch in git is just a label on a particular commit in a repository, along
  with all of it's history (parent commits). Branching helps us as developers to make experimental changes!

## You Do: Research Git Branching (15 min; 10:10-10:25)

- Read the "Using Branches" of
* [Atlassian - Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)
  - Let me know when you have reached the "git merge" section
  - You will see references to Subversion(SVN).  SVN is an older version control system.  You will not need to know more than that regarding SVN to understand the comparisons.

## Think/Pair/Share-1/3/6: Why Branches?  (10 min; 10:25-10:35)

You've had a brief overview.  Let's take a minute to think about why they are important, then share with your neighbor, and we'll share what we feel is important.

Q. Why is branching an important part of git?
---
> A. Branches are useful for many reasons, but some of the most common ones:

> 1. To allow experimentation. By switching to a new branch, we can experiment,
and if the experiment fails, we can delete it and easily switch back to master
(or another branch of our choice). If it succeeds, we can merge those changes
into master.
2. To allow work to proceed on multiple features (or by multiple people) without
interfering. When a feature is complete, it can be merged back into master.
3. To allow easy bug fixes on a stable version while features are being developed.

## How Git Branching Works (5 min; 10:35-10:40)

What makes a branch special in git, is that we're always *on* a
specific branch, and when we commit, the current branch label moves forward to
the new commit. Another way to say that is the branch label always stays at the
tip of the branch.

![Git Branch Diagram](Git_Branching.jpg)
> The diagram above visualizes a repository with two lines of development, one is the master branch, and the other a feature branch. By developing in branches, it’s not only possible to work on branches in parallel, but it also keeps the main master branch free from questionable code.

> From [Atlassian - Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches/git-branch)

## You Do: Branching Exercise (15 min; 10:40-10:55)

We are going to start with a [brief tutorial](http://pcottle.github.io/learnGitBranching/).  This is an introduction to branching.

- Do Levels 1-3.  Stop at 4: "Rebase Introduction".
- Take your time:
  - Read all the dialogs.  They are part of the tutorial.
  - Think about what you want to achieve
  - Think about the results you expect *before* you press enter.
- Whenever you see/type `git commit`, it may help to assume changes have been made and staged.  Why else would you "commit"?

## Common Commands for Managing Branches

* `git branch <new_branch_name>` - create a new branch
* `git checkout <branch_name>` - switch to a specific branch (checks out tip commit and makes branch active)
* `git checkout -b <new_branch_name>` - create a new branch and check it out in one step
* `git branch` - list local branches (`-a` lists local and remote)
* `git branch -d <branch_to_delete>` - delete a branch
  * will not let you delete if branch isn't merged into another branch (i.e. would cause data loss)
  * `git branch -D <branch_to_delete>` - over-rides and deletes a non-merged branch
* `git merge <branch_name>` - merges `<branch_name>` into the current branch, creating a new merge commit in the process

## Break? (10 min; 10:55-11:05)

## You Do: Pushing and PRs from Branches (10 min; 11:05-11:15)

Many OSS projects request that you create pull requests from a non-master branch.

1. Fork and Clone https://github.com/ga-dc/git-tricks.
2. Create and switch to a branch called `<your_name>_suggestion`.
3. Add your own "trick".
4. Commit, and push that change to your remote called 'origin' (your fork)
5. Create a pull request from that branch to the upstream (ga-dc) master branch

## Overview of GitHub Workflow (10 min; 11:15-11:25)
> From [Github Guides](https://guides.github.com/introduction/flow/)

To Recap, In Software Development, Github is very useful in managing and tracking updates and changes to our code.

![Github Workflows](github_workflows.jpg)

### Discuss

Discuss an idea for a new feature or any question about our project/application with our team and agree on what needs to be done.

### Create an Issue

An Issue is a note on a repo regarding some matter that needs attention. It could be a bug, a suggestion for a new feature, a question about the repo or code, etc! On GitHub you can also label, search and assign issues, which help with managing projects.

Create a Github Issue for the feature. It's often useful to write the issue as brief functional spec, documenting the requirements as user stories.

### Create a Branch

Create a feature branch off the master to work on this issue. Our branch name should have meaning to the issue we are working on.

```
$ git checkout -b [name of branch that solves issue]

```
### Work and commit onto your branch

Make changes/commits commits locally, then push your branch up to our remote repository

### Open a Pull-Request or PR

By making a PR, you’re requesting that someone pull in your changes and merge them into their branch. A PR allows you to compare the content on two branches, and all the changes or diffs (differences) are highlighted in green and red.

As soon as you make a change, you can open a Pull Request. People use Pull Requests to start a discussion about commits (code review) even before the code is finished. This way you can get feedback as you go or help from other developers/team members!

<!-- It's good practice to even make a Pull Request for branches in your own repository and merge it yourself to get more comfortable with PRs! -->

### Merge Branch into Master

## Git Merging (5 min; 11:25-11:30)

If our feature branch and work is complete, we need to merge our changes back into our master branch. All we need to do is check out the master branch and then run the git merge command to integrate our feature branch:

```
$ git merge <feature_branch_name>

```
Git creates a new snapshot from this merge and automatically creates a new commit that points to it (the merge commit).

Additionally, we can merge our Remote Repos as well by issuing a PR, and merging on Github. If one of our team members are the ones merging their branches, we can pull down the changes and merge locally into our master:

```
$ git pull <name_of_remote> <branch>

```

Once merged, you can close the issue on github (if an issue was created), and delete the branch:

```
$ git branch -d <feature_branch_name>

```

## You Do: A new project (10 min; 11:30-11:40)

1. Create the structure
   - In ~/wdi/sandbox.  Create a directory and initialize a new repository
   - Create an index.html and commit
   - Fill out html boilerplate and put some elements on the page then commit
2. Add some styling
    - Create and Checkout a branch called "style"
    - Create a stylesheet link it to your html and add some styling to your page then commit
3. Checkout back to your master branch
    - Merge Changes From our style branch Back into our master branch

## Merge Conflicts (10 min; 11:40-11:50)

When we try to merge two branches (or commits from the same branch from a remote), changes may conflict. In this case, git will stop and ask us to fix the issues manually.

A ‘conflict’ occurs when the commit that has to be merged has some change in the same place as the current commit.

To do so:

1. Locate which files contain conflicts using `git status`
2. Open those files and fix the conflicts. (Look for the '<<<<', '====', and '>>>>' which will guide you to the conflict)
3. Commit the fixes.

```
<<<<<<< HEAD:file.txt
This is the original text in your current branch
=======
This is the modified text
>>>>>>> 77976da35a11db4580b80ae27e8d65caf5208086:file.txt

```
>The HEAD is a reference to the last commit in your current checked out branch. Anything between <<<<< HEAD and ===== is the original code from your checked out branch, while anything beneath from ===== to >>>>>> are the changes introduced by the commit you are trying to merge

## Break? (10 min; 11:50-12:00)

## You Do: Merge Conflicts (25 min; 12:00-12:25)

1. Pair up with someone.
- Pick someone as the 'primary', and the 'secondary'.

2. Create a New Repo

  Primary Student Instructions:
  - In your ~wdi/sandbox directory, create a new directory named merge-conflicts.
  - Initialize merge-conflicts as a git repository and create an index.html file
  - Work with the Secondary student to fill out the basic structure for the index.html file.   
  - Create a New Repo on Github called merge-conflicts and add this repo locally as a remote repo for your merge-conflicts directory.
  - Make sure to save and commit local changes and push up to the Remote Repo
  - Add the Secondary student as a Collaborator (search github for how to do this)

  Secondary Students Instructions:
  - After they are added as a Collaborator, they should clone the same repo. Do not fork the Repo.

3. Both the Primary and Secondary should make changes locally on the same "master" branch
  - Modify the index.html
  - Add and Commit Changes Locally.

5. Merging commits:
  - The Primary Student should push up their changes first
  - Then, the Secondary Student should do the same and try pushing up their changes

6. Merge conflicts:
  - When the Secondary Student Tries to Push their commits, there should be merge conflicts
  - The Secondary Student should work locally (with the Primary) to resolving the merge conflicts.
  - Once completed, commit and push up changes to the remote repo

7. Pulling Changes:
  - Now, the Primary student should pull down the changes from the remote repo and work to resolve any merge conflicts

## Closing (5 min; 12:25-12:30)

Review Learning Objectives:
* Explain what a branch is in git
* Create, merge and delete branches on local and remote repositories
* Describe how branching and merging allows for collaboration during development
* Describe Github Workflows using issues, branches, and pull-requests
* Resolve a merge conflict

Quiz Questions:
* What is a feature branch in Git?
* How can you check what branch your are currently working in?
* How can you bring a new feature in the main branch?
* What is a conflict in git? How can a conflict be resolved?

### Homework

From this point on, all homework submissions should be a pull request from a feature (or 'topic') branch, named `<your_name>_solution`.


## `git mergetool` (An exercise for the reader)

Some merge conflicts can be quite confusing.  Git provides a way to use a visual tool to assist in resolving the merge conflicts.

If you have installed XCode, an decent tool (opendiff) is used.  For this class, we will use [KDiff3](http://kdiff3.sourceforge.net/).  Here's an [example, with images](http://www.gitguys.com/topics/merging-with-a-gui#Merging_with_kdiff3), including a way to try it first.

- Install via homebrew: `brew install kdiff3`
- Setup KDiff3 as your merge too using [these instructions](http://naleid.com/blog/2012/01/12/how-to-use-kdiff3-as-a-3-way-merge-tool-with-mercurial-git-and-tower-app).  
  - Be sure to skip the "Installation" steps.
  - Stop at "Git Tower Integration"
- When you have a merge conflict, you can type `git mergetool` to see a 3-way merge and the merge results.  Like this: ![](http://naleid.com/images/2012/01/kdiff3_merge_window_fixed.png)

## References & Additional Resources

* [Git-Guide](http://rogerdudler.github.io/git-guide/)
* [Git Book - Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
* [Atlassian - Git Branching Tutorial](https://www.atlassian.com/git/tutorials/using-branches)
* [Interactive Git Branching Tutorial](http://pcottle.github.io/learnGitBranching/)
* [Git Sandbox](http://pcottle.github.io/learnGitBranching/?NODEMO)
