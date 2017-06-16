# git-stash-timestamp

A script for stocking the file update date in the CSV file and restoring it when the file update date is updated by GIT


## Features

- Record the target file in ".gittimestamp.csv"
- Restore to the file to be recorded by the file update date recorded in ".gittimestamp.csv"
- Make the following file in the local repository git / hooks so that the script automatically runs when git is operated
    - .git/hooks/pre-commit
        * Execute `stash-timestamp` command before executing commit to generate".gittimestamp.csv "
    - .git/hooks/post-commit
        * If ".gittimestamp.csv" changes after commit execution, add csv and run `git commit --amend'
    - .git/hooks/post-checkout
        * Execute the `pop-timestamp` command after checkout execution. and restore the file update date based on ".gittimestamp.csv"
    - .git/hooks/post-merge
        * Execute the `pop-timestamp` command after the merge. and restore the file update date based on ".gittimestamp.csv"


## Requirement

- bash(git bash)
- perl5

## Installation

~~~
$ git clone git@github.com:YasKamito/git-stash-timestamp.git
$ ./setup.sh
~~~

## Usage

#### Preparing the development environment

* Register to `.git/hooks` to call the script at commit / merge / checkout

~~~
$ git clone git@xxxxxx.com:user/sample.git
$ cd sample
$ git-setup-timestamp
~~~

#### Record file update timestamp in ".gittimestamp.csv" file

* Manually record the file update timestamp.

~~~
$ cd path_to_repos
$ stash-timestamp
~~~

#### Restore to the file to be recorded by the file update date recorded in ".gittimestamp.csv"

* Manually Apply file update timestamp.

~~~
$ cd path_to_repos
$ pop-timestamp
~~~


