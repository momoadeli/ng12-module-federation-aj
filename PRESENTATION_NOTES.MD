!BRANCH! change branch to NOT SINGLETON

1. create apps (eg left nav) to the broader workspace
2. ng add angular-architects ALL <app name> to update
3. ALL apps: leftnav, remote, container
   1. the webpack.config.json files (all apps)
      1. since using ngx-build-plus the proper entries are added
      2. exposes: host vs remote vs components vs modules and routes
      3. remotes: host vs remote vs components vs modules and routes
      4. shared: packages (eg angular) that are shared: can be versioned
   2. add main and within import bootstrap.ts file finstead of origfina main.ts (makes mf work)
   3. updates angular.json]

Start with module format in remotes webpack.config.json

1. goto remote webpack.config.json
2. uncomment the expose modules: TWO MODULES are exposed!!
3. describe romoute.module.ts and remote routes
4. describe remote.component.html
5. !!!!! describe remote app.comonent.html (comment/uncomment components)

Now go to container webpack.config.ts
1. describe how we won't use remotes here because we will be able to get hosts at runtime via an api service call
2. talk about dynamic loader service and feature provided by angular-architects
   1. the data can come via an api for suite configuration of available remotes/mfes
   2. now go to app.component.ts and uncomment loadmodules in ngOnInit() (TWO modules regular + animate!)
      1. use the dynamic loader services!
   3. go to app.component.html and use router outlet
   4. go to route.ts and HERE is where the different new mfe route will be injected by the dynamic loader service!!!

Now build container: nx s

Now build remote app: 
1. nx build --configuration=development remote

Now But not enough...need to SERVE it:
1. go to dist/app and run http-server .
2. !!!run local:4200 and see the 'search route'!!!!

GOTO network tab and show remoteEntry.js is being served from local:8080

Goto lib/sharedservice and discuss singleton or not via Angular devtools
2. 3. goto container -> app.component.ts: ctor: this.sharedService.id = 'container';
4. goto: remote -> remote.component.ts ctor this.sharedService.id = 'remote';
   1. show in devtools
!BRANCH! change branch to singleton
SINGLETON: no code change duplicated (mm: 14:09)
1. SINGLETON: 
   1. show in devtools

!BRANCH! change branch to nav-component

1. goto remote webpack.config.ts
2. note module has been replaced by component
   1. note refer to remote.component.ts instead of remote.module.ts
3. goto leftnav webpack.config.ts
   1. note compoenent has been exposed
   2. note it points to app.component.ts
4. So now we have TWO remote components we can add to our host container
   1. goto container --> app.component and show how router-outlet has been replaced by  mdirectives
   2. describe the directive and how it uses the loadComponent call in the dynamic loader service

REBUILD:
1. remote: nx build --configuration=development remote
2. levtnav: nx build --configuration=development leftnav
3. restart http-server

RUN: 
1. note the navigation component that is served from 8080 server is now running on 4200 (container)
2. 2. Note this navigation can be a breadcrumb that can be custom called by client apps.

