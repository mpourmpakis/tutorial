# GitHub team work flows
There are different ways of working in teams using GitHub. The two main types are:

**Fork and pull model**

In the fork and pull model, anyone can fork an existing repository and push changes to their personal fork without needing access to the source repository. The changes can be pulled into the source repository by the project maintainer. When you open a pull request proposing changes from your fork's branch to a branch in the source (upstream) repository, you can allow anyone with push access to the upstream repository to make changes to your pull request. This model is popular with open source projects as it reduces the amount of friction for new contributors and allows people to work independently without upfront coordination.

**Shared repository model**

In the shared repository model, collaborators are granted push access to a single shared repository and topic branches are created when changes need to be made. Pull requests are useful in this model as they initiate code review and general discussion about a set of changes before the changes are merged into the main development branch. This model is more prevalent with small teams and organizations collaborating on private projects.

## Fork and pull model

### Main repository
All the finished codes will go here and everyone working on the project will create pull requests here.

### User repository
The user repositories will have the main repository as their remote. When a change is gonna be made the users will create a new branch from their *master* branch (which points to *master* branch of *main repository*). After all changes are commited and pushed to the *feature* branch, a pull request (PR) is created. When the PR is discussed with the team further changes can be requested or if the changes are accepted the *feature* branch can be merged with main repository *master* branch.

#### Account setup
Setting up user name and email address.

```bash
git config --global user.name "username"
git config --global user.email "email@example.com"
```
The email and user name can be confirmed by:
```bash
git config --global user.name
username

git config --global user.email
email@example.com
```

If you wish to link your password as well you can generate a new SSH key and add it to the ssh-agent as described [here](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/).

#### Adding remote repository
To add a new remote, use the *git remote add* command on the terminal, in the directory your repository is stored at.

The *git remote add* command takes two arguments:

A remote name, for example, *origin*
A remote URL, for example, *https://github.com/user/repo.git*
```bash
git remote add origin https://github.com/user/repo.git
# Set a new remote

git remote -v
# Verify new remote
origin  https://github.com/user/repo.git (fetch)
origin  https://github.com/user/repo.git (push)
```

#### Branching
**Create a new branch from another branch**

```bash
git checkout -b newFeature dev
```
Creates newFeature branch off dev.
In the fork and pull model users would branch off their *master* branch which should point to the *master* branch of the main repository.

**Deleting a brnach**
```bash
# Delete remote branch
git push origin --delete <branch_name>

# Delete local branch
git branch -d <branch_name>
```
If there are unmerged changes which you are confident of deleting:
```bash
git branch -D <branch_name>
```
#### Example work flow
- Direct to master branch and pull from the main repository
```bash
git checkout master
git pull upstream
```
where *upstream* is the name of the remote repository.

- Create new feature branch:
```bash
git checkout -b newFeature master
```
- Make changes and commit with a message
```bash
git add .
git commit -m "Made some changes"
```
- Push changes to *newFeature* branch of user repository
```bash
git push origin newFeature
```
- Create pull request

## GitHub cheat sheets
[Official GitHub cheat sheet](https://services.github.com/on-demand/downloads/github-git-cheat-sheet/).

[Another useful GitHub cheat sheet](https://github.com/jakubpawlowicz/git-cheat-sheet).