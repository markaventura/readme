# Rails + Angular + Yeoman
Creating web app using **Rails** as server-side framework and
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
6. Change **dist** in Gruntfile.js to **../publi**
