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

1. goto remote webpack.coinfig.json
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

GOTO network tab and show remoteEntry.js sis being served from local:8080

Goto lib/sharedservice and discuss singleton or not via Angular devtools
1. goto container -> app.component.ts: ctor: this.sharedService.id = 'container';
2. goto: remote -> remote.component.ts ctor this.sharedService.id = 'remote';
3. NOT SINGLETON: no code change duplicated (mm: 14:09)
4. change branch to singleton
5. SINGLETON: 
   1. goto tsconfig.base.json a path where alias and source to lib is indicated
   2. add this alias to shared mappings for both remote and 


