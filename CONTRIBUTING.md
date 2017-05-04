# Contribution guidelines for Project Cognoma repositories

## Project Philosophy

Project Cognoma is an open source community-based project.
Beyond our immediate scientific aspirations, we want to engage as many individuals as possible in doing cool work.
Project Cognoma is a place to learn and grow as a community.
So don't be shy.
Cognoma wants [your contribution](https://opensource.guide/how-to-contribute/ "How to Contribute to Open Source · Open Source Guides")!

## Background

Git is a version control system.
It allows you to create repositories to track the contents of a directory over time.
Git was designed for collaborative software development.

GitHub is a cloud hosting service for git repositories.
It provides additional features for repositories, including a web interface, issues, and a pull request framework for suggesting changes.

## Issues

We use [GitHub Issues](https://guides.github.com/features/issues/) to discuss everything and anything including bug reports, feature requests, brainstorming, and questions.
New issues should be opened on the most relevant [repository](https://github.com/cognoma "Repositories of the Cognoma Organization").
Before opening a new issue, please search through existing issues to avoid duplication.
However, to keep discussion focused, it's better to open a new issue than divert the topic of an existing one.
You can always link to related issues for context.

## Contribution Workflow

Contributions happen through _pull requests_, where contributors propose changes to Cognoma repositories.
This section will describe the pull request workflow.
 We'll use the [`cognoma/sandbox`](https://github.com/cognoma/sandbox) repository, which is designed for practicing this workflow, as an example.
Finally, let's pretend your GitHub username is `username`.

To create a pull request, you will first need to make a change.
Since you can't write directly to `cognoma/sandbox` or other Cognoma repositories, you'll need [to fork](https://help.github.com/articles/fork-a-repo/) `cognoma/sandbox` through the GitHub interface.
Forking `cognoma/sandbox` will create `username/sandbox`, a personal copy of the `sandbox` repository on your GitHub.

Next, you'll need to clone `username/sandbox`, which downloads a copy to your computer.
In a terminal, run:

```sh
# Clone your fork locally
git clone https://github.com/username/sandbox

# Change directory into the new repository
cd sandbox

# Add the original cognoma repository as a remote repository named upstream
git remote add upstream https://github.com/cognoma/sandbox.git
```

The final command makes git aware of `cognoma/sandbox`, so you can retrieve upstream changes in the future by running `git fetch upstream`.

Now you have a local directory of the git repository.
Any changes to the contents of the directory can now be tracked using git.
But before you make your desired change, we recommend creating a branch.
When you clone a repository, you will, by default, be on the `master` branch.
However, you don't want to make changes on your `master` branch, since it's best to keep it synced with the `upstream` repository.
Therefore, you will create a new branch for making your change.
So say I wanted to add my name to `cognoma/sandox`, I would create a new branch named `add-username` with the following command:

```sh
# Create a new branch named add-username and switch to it
git checkout -b add-username
```

Now you will be on your `add-username` branch.
You should now make your change, which in this example will be adding a new file but can also be modifying an existing file.
Let's say you create the file `people/username.md` in your text editor of choice.
Now you will have to stage your change by running:

```sh
# The following two commands show what changes git detects.
# Since they don't change the repository in any way, they're optional.
# But it's best practice to look at changes before adding them.
git status
git diff

# Add the file you've created
git add people/username.md
```

Next you will have to make a commit, which takes a snapshot of everything that's been staged (using `git add` above).
To commit, run `git commit`.
A text editor should appear that allows you to write a [commit message](https://chris.beams.io/posts/git-commit/) where you should describe the changes in the commit.
Alternatively, you can specify your commit message using the command line:

```sh
# Specify commit message, no text editor will appear
# The first --message (-m for short) creates commit message subject
# and the following --message arguments create the commit message body.
git commit --message "Add people/username.md" --message "Closes URL_TO_GITHUB_ISSUE"
```

If all succeeds, you will have added to the git repository and your commit will be visible when you run `git log`.

Next you will push your commit to GitHub, which means add it to `username/sandbox` on GitHub.
To do this, run:

```sh
# This will only have to be run once per computer
# It adopts the Git 2.0, removing a confusing message
git config --global push.default simple

# Push your current branch to GitHub
# If this is the first time you're pushing this branch,
# you will receive an error suggesting you specify --set-upstream.
# If so, use the suggested command. Then future git push attempts will work.
git push
```

Now you are ready to create your [pull request](https://help.github.com/articles/about-pull-requests/).
The GitHub webpage for either `cognoma/sandbox` or `username/sandbox` should have a new button to "Compare & pull request." Click it and write a title and description for your requested changes.
Then submit.
Soon (hopefully), another Cognoma contributor will review your pull request.
Usually, pull requests will require some changes before they are ready to merge (incorporate into Cognoma repository).
You can add additional changes to a pull request by adding commits to the branch its based on, which is this example is `add-username`.

Once your pull request passes review, it will be merged by a repository maintainer.
Before starting on any new pull requests, you will want to sync your fork, so you're not starting from an outdated version of the codebase, by running:

```sh
# Fetch all new changes on the cognoma repo
git fetch upstream

# Make sure you're on your master branch.
git checkout master

# Fast forward your master branch with upstream changes.
git merge --ff-only upstream/master
```

### Pull request advice

1. Focus a pull request on a single feature.
Smaller pull requests are easier to review and will thus get merged quicker.
If you want to change multiple things, create multiple pull requests.
One feature, one branch, one pull request!

2. Open incomplete pull requests but put WIP in the title for "work in progress".
This enables early stage feedback to save time later and helps coordinate efforts.
Once you feel the pull request is ready, remove WIP from the title.

3. Please help **review open pull requests**.
Even if you don't fully know the topic, the dialogue will often be productive.
As a reviewer, it's helpful to note the type of review you performed: did you test the code, look it over, or are you just supporting the concept?

4. Repository maintainers are encouraged to [squash merge](https://help.github.com/articles/about-pull-request-merges/#squash-and-merge-your-pull-request-commits) pull requests when appropriate.
This will compact all of the commits into one, helping keep the commit history clean.

**Happy contributing!**

## Maintainers

Maintainers are individuals with commit access to Cognoma repositories and are responsible for reviewing and merging pull requests.
In addition, maintainers help keep repositories organized and issues up to date.
Maintainers are selected based on a sustained, positive history of contribution to Cognoma and mastery of the GitHub-based workflow.
