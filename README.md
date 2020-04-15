# how-migrate-git-repository
# Step by step to migrate a git repository from bitbucket to githut or vice-versa
# keeping all branches and commits history

I will call your current repo as `old-repo` and the target repo as `new-repo`

### Clone your old repo
`git clone old-repo`

### Download all project branchs
`git branch -a | grep -v HEAD | perl -ne 'chomp($_); s|^\*?\s*||; if (m|(.+)/(.+)| && not $d{$2}) {print qq(git branch --track $2 $1/$2\n)} else {$d{$_}=1}' | csh -xfs`

### Rename your `old-repo` remote
`git remote rename origin old-origin`

### Add your `new-repo` remote address
`git remote add origin new-repo`

### Submit your local project data to `new-repo`
`git push origin --mirror`
