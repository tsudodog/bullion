# Github

# Branches

## Clean Merged Branches

Remove all merged branches that are not master or dev.
This command uses several smaller tools to accomplish this task, namely grep for text searching and xargs to paramaterize the output into git branch. 

grep -v indicates that it should not match master and not match dev

xargs -n 1 means that 1 count will tokenize the output into git branch d. Basically since grep -v makes a list with each branch name on a line the new line character is tokenized making each branch name the argument provided to git branch -d. 

```
git branch --merged | grep -v -e master -e dev | xargs -n 1 git branch -d 
```

[link](https://stevenharman.net/git-clean-delete-already-merged-branches)
