### Useful git commands
	
	- If you remove the HEAD in origin (ADO) - basically deleted the branch, you can then push the local branch to be the new origin 
	git push origin HEAD
	
	- removing commits already pushed 
	git rebase -i <commit-id>
	
	- Squash your branch:
	git rebase -i main --> do daily or rebase after each PR has been merged to main 
	
	- Rebase without squashing:
	 git rebase main
	 git rebase feature/azeem/38253-Return-button-for-Endorser
	
	- un-commit changes that were committed and havent been pushed yet
	 git reset --soft HEAD^
	
	- copy branch using commit:
	git branch branch_name <commit-hash>
	 git branch branch_name <co
	
	- Copy branch: 
	 git checkout -b ADO-23651-Add-Visx-Chart-Copy feature/ADO-23651-Add-Visx-Chart
	 git checkout -b ADO-25419-remove-additional-fields-Copy bugfix/ADO-25419-remove-additional-fields
	 git checkout -b feature/ADO-2854/Block-a-Plan-copy	feature/ADO-2854/Block-a-Plan
	
	- Stash commits and bring them back:
	 git stash save "rebase PR branch"
	 git stash list
	 git stash apply 0 --> check which one you want to reapply to your branch via 2nd step 
	
### NEW BRANCH
	feature/laku/ADO-
	bug/laku/ADO-	

### Useful Migration Commands

	Adding a migration
	Add-Migration [insertMigrationName i.e. ADO-23651-Add-Visx-Chart]
	
	Updating your database (if a PR already has a migration run this command)
	Update-Database [if i am unable to run this then theirs; 
	1. An Error, 
	2. Forgot to use my DB connection string, 
	3. didn't change 'default project:' to infrastructure ]
	
	Removing a migration 
	Remove-Migration [insertMigrationName i.e. ADO-23651-Add-Visx-Chart]
	
	
### Dialing in on phone thing
1. Find a local Phone number 
2. Dial AUS,Sydney => 00 first then the 3 digit and so on...........]
3. Then enter Conference id followed with # 
For visual representation go to QPP DEV chat and search "for the weird and old polycom"
	
### FORMAT
	
```CTRL + K, CTRL + D in Visual Studio ```
```Shift + Alt + F in Visual Studio Code ```


### Change user FE
  
```js
const contextValue = {
    userId: "594b8151-fde6-4ffc-a788-dbd2cec74e13",
    name: "Pather, Nathaniel (IST)",
    username: "Nathaniel.Pather@riotinto.com",    
  };
```
