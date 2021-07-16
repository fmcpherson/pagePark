# Hello world!

This is an instance of [pagePark](https://github.com/scripting/pagePark) running on [Digital Ocean's app platform](https://www.digitalocean.com/products/app-platform/). I have set this site up as an experiment to see how easy it is to deploy pagePark, which is a Nodejs app, using app platform. 

## Prerequisites:

- An account with Digital Ocean
- An account on Github
- Fork a copy of the source repo to your Github account
- Clone the repo in your personal Github account to a personal computer
- Add package-lock.json to local repo (required by Digital Ocean to deploy the app)
- Add config.json to local repo (so you can control how pagePark runs)
- Mkdir domains in local repo (so you can deploy content for pagePark to host)
- Add a readme.txt file in domains directory of local repo
- git add .; git commit; git push

At this point you have a repo in your personal Github account that will be the source for your deployment of pagePark on the Digital Ocean
App Platform. Follow the steps provided to you by Digital Ocean to deploy the app. In this example I simply used the defaults and 
selected the smallest Basic container.

## Now what?

Map your own domain or subdomain to the application by creating a CNAME record with your DNS provider. Finally, create a directory that has the sane name as the URL you just configured via DNS in the domains directory of your repo, and put a index.md file in it to display a page.

At this point you have a web server deployed that can host your content. To add content simply create files using any one of the formats that pagePark can render into your domains folder. 
