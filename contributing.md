# Contributing

Contributions are **welcome**.

Please read and understand the contribution guide before creating an issue or pull request.

## How to get started

Hey there! You're probably here because you want to help out. Thanks for joining us!

In this document we'll try to outline how to get started contributing and how to perform common tasks, like keeping your local fork up to date.

### Set up your own fork of the repository

In order to contribute you'll want to make a "fork" of this repository.

Click the `fork` button at https://github.com/placetopay-org/code-guidelines and wait for it to complete.

Once the fork is done, clone your fork to your computer by navigating to a folder you'd like to put the site in, and then replacing `[username]` in this snippet with your GitHub username and running it from the terminal:

```bash
git clone git@github.com:[username]/code-guidelines.git
```

In order to keep your fork up-to-date with the original repository, you'll also want to add an extra git "remote" that points to the original repo.

Your fork will already be connected to your local repo as the remote named `origin`.

Let's add your link to the original repo by running the following command after navigating to the `code-guidelines` folder in your local repo:

```bash
git remote add upstream git@github.com:placetopay-org/code-guidelines
```

This added a remote named `upstream` that points to Placetopay's repo.

You can fetch the upstream branches by running the following command:

```
git fetch upstream --prune
```

Now you have this set up, run the following commands to install the dependencies:

```bash
composer install
npm install 
npm run dev
```

# How to perform common tasks

## Keep your fork up to date

Using the git remote we set up earlier, we first need to fetch changes that were made upstream:

```bash
git fetch upstream --prune
```

Next, change to your local main branch:

```bash
git checkout main
```

And merge the changes that were made upstream into your local branch.

```bash
git merge upstream/main --no-ff
```

## Prepare your pull request

Before actually creating a pull request, you have the chance to clean up your code. Remove debug statements, clean up commented code and refactor if needed.

Look to [this blog post](https://chris.beams.io/posts/git-commit/) for how to write a good git commit message.

## Create a pull request

When you have your changes ready in your own branch on your fork, it's time to create a pull request.
Try to describe what kind of changes you have made and why you have made them. This helps us in understanding why you are suggesting this change and what your reasoning behind it is.

Look to [this blog post](https://tighten.co/blog/building-a-great-pull-request/) for how to create a great pull request.
