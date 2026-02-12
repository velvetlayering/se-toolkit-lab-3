# `Git workflow` for tasks

> [!NOTE]
> This procedure is based on the [`GitHub flow`](https://docs.github.com/en/get-started/using-github/github-flow).

```text
┌───────┐    ┌────────┐    ┌─────────┐    ┌────┐    ┌────────┐    ┌───────┐
│ Issue │ →  │ Branch │ →  │ Commits │ →  │ PR │ →  │ Review │ →  │ Merge │
└───────┘    └────────┘    └─────────┘    └────┘    └────────┘    └───────┘
```

Here's this workflow in the context of repos:

![Git workflow](../images/git-workflow.drawio.svg)

Outline:

- [Create a `Lab Task` issue](#create-a-lab-task-issue)
- [Switch to the `main` branch](#switch-to-the-main-branch)
  - [Switch to the `main` branch using the `VS Code Terminal`](#switch-to-the-main-branch-using-the-vs-code-terminal)
  - [Switch to the `main` branch using `GitLens`](#switch-to-the-main-branch-using-gitlens)
- [Pull changes from `origin/main`](#pull-changes-from-originmain)
  - [Pull changes from `origin/main` using the `VS Code Terminal`](#pull-changes-from-originmain-using-the-vs-code-terminal)
  - [Pull changes from `origin/main` using `GitLens`](#pull-changes-from-originmain-using-gitlens)
- [Resolve conflicts](#resolve-conflicts)
  - [Pull and rebase using `GitLens`](#pull-and-rebase-using-gitlens)
  - [Resolve conflicts using `GitLens`](#resolve-conflicts-using-gitlens)
- [Switch to a new branch](#switch-to-a-new-branch)
  - [Switch to a new branch using `GitHub`](#switch-to-a-new-branch-using-github)
  - [Switch to a new branch using the `VS Code Terminal`](#switch-to-a-new-branch-using-the-vs-code-terminal)
  - [Switch to a new branch using `GitLens`](#switch-to-a-new-branch-using-gitlens)
- [Edit files](#edit-files)
- [Commit](#commit)
- [(Optional) Undo commits](#optional-undo-commits)
- [Publish the branch](#publish-the-branch)
  - [Publish using the `VS Code Terminal`](#publish-using-the-vs-code-terminal)
  - [Publish using `GitLens`](#publish-using-gitlens)
- [Push more commits](#push-more-commits)
  - [Push using the `VS Code Terminal`](#push-using-the-vs-code-terminal)
  - [Push using `GitLens`](#push-using-gitlens)
- [Create a PR](#create-a-pr)
  - [Open the PR editor using `GitHub`](#open-the-pr-editor-using-github)
    - [Open the PR editor using a button](#open-the-pr-editor-using-a-button)
    - [Open the PR editor using `Pull requests`](#open-the-pr-editor-using-pull-requests)
    - [Open the PR editor using the branch list](#open-the-pr-editor-using-the-branch-list)
  - [Finish creating a PR](#finish-creating-a-pr)
- [Get a PR review](#get-a-pr-review)
  - [PR review rules](#pr-review-rules)
    - [As a PR reviewer](#as-a-pr-reviewer)
    - [As a PR author](#as-a-pr-author)
- [Merge the PR](#merge-the-pr)
- [Clean up](#clean-up)

## Create a `Lab Task` issue

[Create an issue](../appendix/github.md#create-an-issue) using the `Lab Task` [issue form](../appendix/github.md#issue-form).

## Switch to the `main` branch

Go to `VS Code`.

Switch to the `main` branch using any of the following methods:

- [Switch to the `main` branch using the `VS Code Terminal`](#switch-to-the-main-branch-using-the-vs-code-terminal)
- [Switch to the `main` branch using `GitLens`](#switch-to-the-main-branch-using-gitlens)

### Switch to the `main` branch using the `VS Code Terminal`

1. [Run using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal):

   ```terminal
   git switch main
   ```

### Switch to the `main` branch using `GitLens`

1. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette):
   `GitLens: Git Switch to..`.
2. Select the `main` branch (e.g., using `UpArrow` and `DownArrow` on your keyboard).
3. Press `Enter` to confirm.

## Pull changes from `origin/main`

Pull changes from the `main` branch in your fork on `GitHub`.

We call that branch `origin/main`.

### Pull changes from `origin/main` using the `VS Code Terminal`

1. [Run using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal):

   ```terminal
   git pull origin main
   ```

### Pull changes from `origin/main` using `GitLens`

1. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette): `GitLens: Pull`

## Resolve conflicts

You may see some errors and messages about conflicts after pulling.

It may happen that commits on your `origin/main` are different from commits on your local `main` branch in your cloned repo on your computer.

You can see that in the [`Status Bar`](../appendix/vs-code.md#status-bar).

<img alt="Commit Conflict" src="../images/appendix/vs-code/status-bar-commit-conflict.png" style="width:400px"></img>

You need to pull commits from `origin/main` into your local `main`.

These commits from `origin/main` will find a place somewhere among the commits on your local `main`.

However, you can get conflicts if commits from `origin/main` modified the same lines of text in files as your local commits but in a different way.

In this case, you should rebase your local branch and resolve conflicts:

- [Pull and rebase using `GitLens`](#pull-and-rebase-using-gitlens)
- [Resolve conflicts using `GitLens`](#resolve-conflicts-using-gitlens)

### Pull and rebase using `GitLens`

When you rebase, your local commits are placed on top of the commits from `origin/main`.

1. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette):
   `GitLens: Pull`
2. Select `Pull with Rebase` (e.g., using `UpArrow` and `DownArrow` on your keyboard).
3. Press `Enter` to confirm.
4. You're done if `GitLens` doesn't show any error.

### Resolve conflicts using `GitLens`

Continue resolving conflicts if you see an error like this:

<img alt="Pull Error" src="../images/appendix/gitlens/pull-error.png" style="width:400px"></img>

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Go to `Merge Changes`.
3. Click a file.
4. Click `Resolve in Merge Editor`.
5. Accept changes that you like more.
6. Click `Complete Merge`.
7. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
8. Click `Continue`.
9. This should be resolved.
10. There may be other conflicts.
11. `VS Code` can show something like `Rebasing (1/3)` and `Cancel`.
12. Click that `Cancel`.
13. Repeat steps.

## Switch to a new branch

Create a new branch and switch to it using any of the following methods:

<!-- no toc -->
- [Switch to a new branch using `GitHub`](#switch-to-a-new-branch-using-github)
- [Switch to a new branch using the `VS Code Terminal`](#switch-to-a-new-branch-using-the-vs-code-terminal)
- [Switch to a new branch using `GitLens`](#switch-to-a-new-branch-using-gitlens)

> [!IMPORTANT]
> Replace the `<branch-name>` with the actual branch name.

### Switch to a new branch using `GitHub`

1. Go to your fork on `GitHub`.
2. [Create a branch](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-a-branch-for-an-issue).
3. Copy the command provided by `GitHub`. It's something like:

   ```terminal
   git fetch origin
   git checkout <branch-name>
   ```

4. [Run the copied command using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal).

### Switch to a new branch using the `VS Code Terminal`

1. [Run using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal):

    ```terminal
    git checkout -b <branch-name>
    ```

### Switch to a new branch using `GitLens`

1. [Run using the `Command Palette`](../appendix/vs-code.md#run-a-command-using-the-command-palette):
   `GitLens: Git Create Branch..`.
2. Select `main` as the base branch (e.g., using `UpArrow` and `DownArrow` on your keyboard).
3. Press `Enter` to confirm.
4. Write `<branch-name>` to provide the new branch name.
5. Press `Enter` to confirm.
6. `Select Create & Switch to Branch` (e.g., using `UpArrow` and `DownArrow` on your keyboard).
7. Press `Enter` to confirm.

## Edit files

Edit files in the [`Editor`](../appendix/vs-code.md#editor) to produce changes.

## Commit

[Commit changes](../appendix/git-vscode.md#commit-changes) to the `<branch-name>` to complete the task.

## (Optional) Undo commits

[Undo commits](../appendix/git-vscode.md#undo-commits) if necessary.

## Publish the branch

### Publish using the `VS Code Terminal`

1. [Run using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal):

   ```terminal
   git push -u origin <branch-name>
   ```

### Publish using `GitLens`

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Click `GITLENS` to open the `GitLens` panel.
3. Click the `Commits` icon.
4. Click the `Publish Branch` icon to the right of `Publish <branch-name> to GitHub`.
5. Press `Enter` to confirm.

## Push more commits

### Push using the `VS Code Terminal`

1. [Run using the `VS Code Terminal`](../appendix/vs-code.md#run-a-command-using-the-vs-code-terminal):

   ```terminal
   git push
   ```

### Push using `GitLens`

1. [Open the `Source Control`](../appendix/vs-code.md#open-the-source-control).
2. Click `GITLENS`.
3. Click the `Commits` icon.
4. Click the `Push` icon to the right of `COMMITS`.

## Create a PR

Create a PR to the `main` branch **of your fork**.

Complete these steps:

- [Open the PR editor using `GitHub`](#open-the-pr-editor-using-github)
- [Finish creating a PR](#finish-creating-a-pr)

> [!TIP]
> You can also [create a PR using  `GitHub Pull Requests` extension](https://code.visualstudio.com/docs/sourcecontrol/github#_creating-pull-requests).

### Open the PR editor using `GitHub`

Open the PR editor using any of the following methods:

- [Open the PR editor using a button](#open-the-pr-editor-using-a-button)
- [Open the PR editor using `Pull requests`](#open-the-pr-editor-using-pull-requests)
- [Open the PR editor using the branch list](#open-the-pr-editor-using-the-branch-list)

#### Open the PR editor using a button

Go to your fork on `GitHub`.

If you see the `Compare & pull request` button, click it.

#### Open the PR editor using `Pull requests`

1. Go to your fork on `GitHub`.
2. Click `Pull requests`.
3. Click `New pull request`.
4. Click `base repository: <your-username>/se-toolkit-lab-2`.
5. Click `<your-username>/se-toolkit-lab-2` to select the base repo.
6. The PR will be created in your repo with `main` as the base branch.
7. Click `compare: main` to choose a branch to compare with the base.
8. Click `<branch-name>`.
9. Click `Create pull request`.

#### Open the PR editor using the branch list

1. Go to your fork on `GitHub`.
2. Click `main` under the `forked from ...` text.
3. Click `<branch-name>`.
4. Click `Contribute`.
5. Click `Open pull request`.

### Finish creating a PR

1. Write the PR title.
2. Write the PR description.
3. [Link the PR](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/linking-a-pull-request-to-an-issue#linking-a-pull-request-to-an-issue-using-a-keyword) to the issue, e.g. `Closes #<issue number>`.
4. Check the boxes.
5. Click `Create pull request`.

## Get a PR review

[Request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/requesting-a-pull-request-review#requesting-reviews-from-collaborators-and-organization-members) a review of the PR from the collaborator (see [PR review rules](#pr-review-rules)).

Get the collaborator's comments and address them, e.g., make fixes or ask to clarify the comment.

Get the collaborator to approve the PR.

### PR review rules

#### As a PR reviewer

1. Check the task's **Acceptance criteria**.
2. Leave at least one [comment](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/commenting-on-a-pull-request#adding-comments-to-a-pull-request) — point out problems or confirm that items look good.
3. [Approve](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/reviewing-changes-in-pull-requests/reviewing-proposed-changes-in-a-pull-request#submitting-your-review) the PR when all relevant acceptance criteria are met.

#### As a PR author

- Address reviewer comments (fix issues or explain your reasoning).
- Reply to comments, e.g., "Fixed in d0d5aeb".

## Merge the PR

Click `Merge pull request`.

## Clean up

Close the issue.

Delete the PR branch.
