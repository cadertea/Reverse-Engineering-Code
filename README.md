# Unit 14 Sequelize Homework: Reverse Engineering Code

## server.js
In this file you require packages which are in the top portion of the file to run the program appropriately. Uses Heroku and or local server and then also requires the models folder.
Also gets the routes for our Html pages, and syncs the sequelize table.

## package.json
This file shows the packages we are requiring to run our program.

## config/config.json
This file is where you  enter your username and password. We also must make sure when doing so that we are entering it in the appropriate envoironment.
ie(development,test,production). User must place thier database as well as host requirements.

## config/passport.js
This files requires the models file. In here we require the user to log in with a password and username and or an email. This file is also placing parameters on what will occur when email and password are ran properly and incorectly.

## config/middelware/isAuthenticated.js
This file allows the user to access the site if the credentials are met, if not the user is redirected back to the log in page.

## models/index.js
This file requires packages in the beggining to run properly. Once packages are set as variables then this file using the fs method grabs the directory name of
the host you are using and add it to the file name you have for your files. The object.key then grabs the database you created and links it to the models that were created.

## models/users.js
This files is creating, the otherwise created table in mysql, using sequelize, and for each column it is adding criteria to that column. For example email has 4 different criterias: type: DataTypes.STRING, (defining what the input is)
      allowNull: false, (can not be left blank)
      unique: true, (must be a unique email not used by anyone else)
      validate: {
        isEmail: true (must also be an email, not some other entry)
      }.

## routes/api-routes.js
Requires packages in the top portion. the first portion says if the users credentials are correct in the login page then allow them access if not send the user an error code.
The app the post sign up creates a users log in using the configuration in the models that we created with sequelize. Once the sign up features are validated based on the criteria we set in the models/users.js then we send the user to the login page. Then we have a logout directory. Then we have client side routes where we can see client information.

## routes/html-routes.js
server routes for each html page after authentication of the users credentials.

## public/js/login.js also signup.js
grabs the inputs of the forms and or ids/classes used in the html pages using jquery. If we have a username and email in file clears the form also when logging in the username and password gets sent to the api/login directory (similar for signup.js api/signup). If they log in succesfully they are sent to the members page (window.location.replace("/members")

## public/js/members.js
 This file just does a GET request to figure out which user is logged in and updates the HTML on the page

 ## login/members/signup html
 All front end html. log in html has inputs for users to log in, sign up has inputs for users to sign up where they do not have previous credentials and members is where all users are redirected to when they have logged in or signed up.

 ## public/stylesheets/style.css
 all the syling for the:
 form.signup,
form.login {
  margin-top: 50px;
}