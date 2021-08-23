### What is Routing ?
Routing is a way of handling navigation across the application. Since angular is a SPA (single Page Appliaction) the navigation shouldn't reload the complete content instead load only part of the UI which is needed.  
To do this angular uses it's own "Routing Module" wherenin it doesn't refresh the page instead loads the partial UI and renders it in the placeholder.

### How does the routing work ?
Angualr loads the respective component when a particular path amtches. These configurations are done as shown below,
```javascript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'login', component: LoginComponent },
  { path: 'forgotpassword', component: ForgotPasswordComponent },
  { path: 'profile', component: ProfileComponent },
  { path: '**', redirectTo: '' }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
})
export class AppModule { }
```
localhost:8080/login will load the Login Component.  
Also, the placeholder should be defined in the index HTML along with the link configuration
```html
<a href="#" routerLink="/login" >Login</a>
<a href="#" routerLink="/profile/details" >Profile Details</a>

<router-outlet></router-outlet>
```

### What is wild card routing ?
The Path ``` { path: '**', redirectTo: '' } ``` defined is called as wild card routing. Wherein if any of the path configured doesn't match angular will use the wild card routing to load the mentioned component. Used to default the redirection if the apth is not recognized.

### How to do child routings in angular ?
The path can be chained and configured as below
```javascript
const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'login', component: LoginComponent },
  { path: 'forgotpassword', component: ForgotPasswordComponent },
  { 
    path: 'profile', 
    component: ProfileComponent,
    children: [
      {
        path:'details', component: ProfileDetailsComponent
      },
      {
        path:'settings', component: ProfileSettingsComponent
      }
    ]
  },
  { path: '**', redirectTo: '' }
];
```
localhost:8080/profile will load the Profile Component.  
localhost:8080/profile/details will load the Profile Detail Component.
