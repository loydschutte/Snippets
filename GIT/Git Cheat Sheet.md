Set up new repo:
>git init

Stage changes
>git add --A
or
>git add .

List all branches
>git branch

Start a new branch
>git checkout -b newbranch

Switch back to branch
>git branch oldbranch

Merge branches
1) Switch to master branch
2) Run command
>git merge newbranch

Add a remote branch (upstream)
>git remote add upstream https://www.github.com/username/repo-name

View remote
>git remote

Clone the repo to make changes
>git clone https://www.github.com/username/repo-name

Check your repo's status
>git status

Commit your files
>git commit -m "Commit message."

Download changes from your remote repo(upstream) to your working local repo
>git fetch upstream

Push your changes to the remote server
>git push origin master

Fetch and merge any remote commits
>git pull