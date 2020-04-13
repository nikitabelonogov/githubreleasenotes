# Git Hub release notes
Collect your release notes from github releases to file

## Installation
* Clone the repo
* Create a symlink in one of your PATHs
```sh
ln -s -f $(pwd)/githubreleasenotes/githubreleasenotes.sh /usr/local/bin/githubreleasenotes
```

## Usage
* [Creating a personal access token for the command line](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)
* Run from your git repository:
```sh
access_token=<your> githubreleasenotes
```
