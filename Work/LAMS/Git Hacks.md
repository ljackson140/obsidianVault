### Useful git commands
	
	- If you remove the HEAD in origin (ADO) - basically deleted the branch, you can then push the local branch to be the new origin 
	git push origin HEAD
	
	- removing commit already pushed in local but not in origin
	git rebase -i <commit-id>
	- Revert already pushed commit
	git revert <commit-id>
	
	- Squash your branch:
	git rebase -i main --> do daily or rebase after each PR has been merged to main 
	
	- Rebase without squashing:
	 git rebase main
	 git rebase feature/azeem/38253-Return-button-for-Endorser
	- -i = interactive
	- git rebase -i HEAD~{#ofCommits}
	
	- un-commit changes that were committed and havent been pushed yet
	 git reset --soft HEAD^
	
	- copy branch using commit:
	git branch branch_name <commit-hash>
	 git branch branch_name <co
	
	- Copy branch: 
	 git checkout -b ADO-23651-Add-Visx-Chart-Copy feature/ADO-23651-Add-Visx-Chart
	 git checkout -b ADO-25419-remove-additional-fields-Copy bugfix/ADO-25419-remove-additional-fields
	 git checkout -b feature/ADO-2854/Block-a-Plan-copy	feature/ADO-2854/Block-a-Plan
	 git checkout -b feature/laku/ADO-63981-Revert-Last-Permit-Copy feature/laku/ADO-63981-Revert-Last-Permit
	
	- Stash commits and bring them back:
	 git stash save "rebase PR branch"
	 git stash list
	 git stash clear --> deletes all stash 
	 git stash drop --> drops latest stash 
	 git stash drop stash@{0} --> select a stash to drop
	 
	 git stash apply 0 --> check which one you want to reapply to your branch via 2nd step 
	
	- Check differences between 2 branches
		git diff main..feature/ADO-blahblahblah
	
	- Git cherry pick commit
		git cherry-pick <commit-hash>
		git cherry-pick bug-ado-86101-incorrect-attribute
		
	- Find out who made changes in x lines
		git blame -L <line1, line2> <file location> 
		git blame -L 55,57 C:\Users\laku.jackson\source\repos\arcs\src\web\src\components\fields\AppFormSelect.tsx
	
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
### LAMS DB:	
	
	My ID:
		CreatedBy								|	CreatedByName
		4b847046-14b9-428e-86fa-8918c2e711ca	|	Jackson, Laku (IST)
		
	[System.Environment]::SetEnvironmentVariable('mydbc','RT.ARCS.Infrastructure.Common.Persistence.ARCSDbContext')
	Add-Migration SeedPOWInstruments -c $env:mydbc
	Remove-migration -c $env:mydbc
	Update-Database -context $env:mydbchttps://www.sqlshack.com/recover-lost-sa-password/
	Update-Database  -context $env:mydbc -migration {MigrationName}
	Get-Migration  -context $env:mydbc
	
	These 2 are the main ones;
	[System.Environment]::SetEnvironmentVariable('mydbc','RT.ARCS.Infrastructure.Common.Persistence.ARCSDbContext')
	Update-Database -context $env:mydbc


	NT Service\MSSQL$LAMSLOCAL

### EF Core migration funcs 
- migrating **up** = applying a migration
- **down** = reverting it
	
	
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

### Rebasing Vim
- to type `pree i`
- `esc` brings you out of editing mode 
- `shift + :` takes you to command 
- `wq` to save the file and close vim

### Restarting Instance 
- Option A: Restart laptop/pc
- Option B: 
	- Navigate to Computer Management via search bar
	- Select correct instance –> right click –> select restart option
	- ![[Pasted image 20251201110906.png]]

### Deploy to dev
- Get artifact from here => [ARCS - Azure Artifacts (visualstudio.com)](https://ist-pandsd.visualstudio.com/ARCS/_artifacts/feed/ARCS)
- Copy artifact name (it’ll be next to the ui or api)
- Head to Pipelines => paste artifact name into the Variables and select your environment  

### Use Dev DB
- Find this line in ConfigureARCSDbContext.cs and update to this `connectionString = configuration.GetConnectionString("DEV_CONNECTION");`
- Change appSettings and appsettings.dev/test to this 
```
"DEV_CONNECTION": "Data Source=sql-rt-psd-lams-np.database.windows.net;Initial Catalog=sqldb-rt-psd-lams-np-dev;Authentication=Active Directory Default;Encrypt=True;",

    //"ARCS_DB_CONNECTION": "Data Source=.\\;Initial Catalog=RT.ARCSDb;Integrated Security=True;Connect Timeout=30;Encrypt=False;TrustServerCertificate=False;",

    "PI_GROUNDDISTURBANCE_REQUESTS_DB_CONNECTION": "Data Source=AUPERSQL65;Initial Catalog=PI_GroundDisturbance_Requests;Integrated Security=True;Connect Timeout=30;Encrypt=False;TrustServerCertificate=True;"

```

## MSSM Connect to dev db

    [How do I use cascade delete with SQL Server? - Stack Overflow](https://stackoverflow.com/questions/6260688/how-do-i-use-cascade-delete-with-sql-server)
    [entity framework - Rider. EF Code First Migrations - Stack Overflow](https://stackoverflow.com/questions/48086047/rider-ef-code-first-migrations)
