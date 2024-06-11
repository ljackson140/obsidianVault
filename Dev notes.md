Tags: [[React]]
* if you have more than 10 env created, remove the oldest ones and re-run the pipeline in ADO (this is if it's failing on Azure SWA step)
* UI on port 3000 id for "npm start"
- api backend port 7071
- all together when running backend and frontend "swa start", all together will be under wrapper swa cli on port 4280
- authN/authZ:
	- frontend leverages azure static web app - authN via SSO of AAD; authZ via AAD groups 
	- backend leverages azure app services (for hosting the rest api) - authN via SSO of AAD; authZ via AAD groups 
	- data leverages azure sql db - authN via AAD
- why is the frontend creating entities/models again? wouldnt that be accessible through the api?
- do we have a feature toggle (hide our unfinished feature from the user)?
- Trunk-based Strategy ([Real Programmers Commit To Master - Jakob Ehn - YouTube](https://www.youtube.com/watch?v=hL1OZfgoZGk&t=2s&ab_channel=Swetugg))
	- We can create a branch to get our commit merged to master, these branches are short lived 
	- Only allowed to commit to master 
	- Release branch is created and if theirs a bug found in release ->fix the bug in master ->it is then cherry picked into release 
	- Master will always be stable and any fixes/hot-fixes are then applied to release branches to prevent regression bugs (user fixes bug in release branch instead of master)
	- ![[Pasted image 20230711101008.png]]
	- if their is bug in production -> create a branch on the commit that was released to prod    -> it is then cherrypicked back to master and production 
	- To hiding unfinished feature can be done by the feature toggle considerations -> currently we do not have this so a new feature branch is created then merged into master after it has been completed 
- Azure Static Web App Tutorial
	- Create an shopping list application that allows you to store your web assets on the cloud storage, create and assign your own SSL certificate, create your API on a cloud server, establish reverse proxy that allows your app to make API calls, distribute the app globally, and set up your own CI/CD pipeline (These are all available when using Azure SWA)
- Testing 
	- npm run test for jest to run
	- make sure to write test if building new features or configuring 
	- 