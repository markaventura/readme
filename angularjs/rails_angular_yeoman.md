# Rails + Angular + Yeoman
Steps in creating web app using **Rails** as server-side framework and
**Angular** as the client-side framework using **Yeoman** for the client
side dependency management, building, testing and workflow management.

## Pre-requisites
* Rails
* Node.js

### Setup
1. Create rails app
    ```
    rails new myapp && cd myapp
    ```
2. Create folder where your client-side app will go:
    ```
    mkdir angular && cd angular
    ```
3. Install Yeoman, Grunt, and Bower
    ```
    npm install -g yo grunt-cli bower
    ```
4. Install Generators for Angular
    ```
    npm install generator-angular generator-karma
    ```
5. Install all the Yeoman stuff:
    ```
    yo angular
    npm install && bower install
    ```
6. Change **dist** in Gruntfile.js to **../public**


### Note
The benefits of not including the angular files into the rails app:

1. Configures test environment (karma)
2. Organized folder structure made using generator-angular plugin
3. Live Reload right out of box.
4. Easy to integrate frontened frameworks such as Foundation or
   Bootstrap.
