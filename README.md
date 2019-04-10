# heroku-static:  Static files demo repository for Heroku presentation

Related repo: <https://github.com/lisadean/heroku-static>

## Prepare repo for Heroku deployment

To deploy to Heroku, you have to apply a buildpack to tell it how to handle the application. The buildpacks are basically a bundle of shell scripts that will do things like running `npm install` for you. Heroku is intended to deploy applications, so it does not have a buildpack for deploying a static website. You can trick it into thinking your site is a PHP application very easily though.

* Run these two commands. They will create two files that will make Heroku think you are deploying a PHP application. (You technically could just rename index.html to index.php but this gives you more flexibility.)
  * `echo '{}' > composer.json`
  * `echo '<?php include_once("index.html"); ?>' > index.php`

* Commit and push your changes.

## Create the app and deploy

* From your Heroku dashboard, create a new Heroku app
* Add the PHP buildpack under Settings > Buildpacks
* You can deploy a few different ways: automatically or manually via github or via the Heroku CLI. We're going to do the latter.
  * Install the Heroku CLI. There's a link on the Deploy tab of your app. You can download and run the installer or install via homebrew.
  * Run `heroku login`
  * Run `heroku git:remote -a <your heroku app name>`. This gives you a second remote. Github is your other remote.
  * Run `git push heroku master` While developing, you'll push to the github remote, but when you are ready to deploy, you push to the Heroku remote.
* Now, your app should be deployed. You can click the 'Open App' button to verify.