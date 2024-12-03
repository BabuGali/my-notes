#### Angular.json
- ANGULAR.JSON is the file which has various properties and configuration of your Angular project. This is the file which is first referred by the builder to look for all the paths and configurations and to check which is the main file.
- It has a reference to the **main.ts** file which tells the builder to start the app from there.
#### main.ts
- This file acts as the entry point of the application. This entry point is defined in the internals of webpack that is used by Angular to support the modular functionality. The path/name of the main file can be changed but it should also be changed in angular.json file. Main.ts helps in creating the browser environment for the application to run. This is done by:

import { platformBrowserDynamic } from ‘@angular/platform-browser-dynamic’;

After this, main.ts file calls the function **bootstrapModule(AppModule)** which tells the builder to bootstrap the app.
#### APP.MODULE.TS
-From the main.ts file, it is very clear that we are bootstrapping the app with **AppModule**. This AppModule is defined in APP.MODULE.TS file which is found in
#### APP.COMPONENT.TS
- From the app.module.ts file above, we can clearly see that the module asks to bootstrap the app component. This app component is in **app.component.ts** file. This is the file which interacts with the html of the webpage and serves it with the data. The component is made by using **@Component** decorator which is imported from **@angular/core**. The component has a selector, which is like a custom html tag which we can use to call that component. It then has **template** or **templateUrl** which contains the html of the page to be displayed. It also has the **styleUrls** array where component specific style sheets can be placed. This is how a component file looks

#### index.html
- Now, since angular is well aware of the modules, components, styles, scripts etc. which are required to display the page, **it’s show time!**
-  It is found in the **src folder** of the app. Compiler dynamically adds all the javascript files at the end of this file. Since all the components are now known, the html file calls the root component that is **app-root**. The root component is defined in app.components.ts which targets app.component.html
 #### APP.COMPONENT.HTML
 - This is the file which contains all the html elements and their binding which are to be displayed when the app loads. Contents of this file are the first things to be displayed.