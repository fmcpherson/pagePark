# Hello world!

This is an instance of [pagePark](https://github.com/scripting/pagePark) running on [Digital Ocean's app platform](https://www.digitalocean.com/products/app-platform/). I have set this site up as an experiment to see how easy it is to deploy pagePark, which is a Nodejs app, using app platform. [Click here](http://my.this.how/frankm/myTechProjects.opml#1626449093000) to see my notes about this test.

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

## Note About OPML Files

One of the features of pagePark is that it knows how to serve a variety of different file formats. For example, I am writing and storing this page in markdown but if you view source you will see the HTML code that pagePark has generated so that this page displays in you we browser.

Pagepark also does this the outline file format, OPML. Unfortunately, if you try to open one from this server, such as [http://pagepark.frankmcpherson.net/test.opml](http://pagepark.frankmcpherson.net/test.opml) find that the page does not display in your web browser.

The browser co's enforcement of HTTPS is rearing it's head here.  If you view source you see Pagepark is dynamically generating HTML for OPML files that includes Javascript sources from "non-secure" HTTP sites, and browsers are no longer displaying non-secure content by default. Chrome, Edge, and Firefox do not provide an obvious way for a user tell it to display non-secure content. 

For now, in Chrome, one can click the lock to the left of the URL, then click Site settings, scroll down to Insecure content and change it from Block(default), to Allow. At this the browser will display a "Not secure" Indicator to the left of the URL. Most likely Google will remove this ability in the future and the other browser companies will follow suite.

## Now what?

Map your own domain or subdomain to the application by creating a CNAME record with your DNS provider. Finally, create a directory that has the sane name as the URL you just configured via DNS in the domains directory of your repo, and put a index.md file in it to display a page.

At this point you have a web server deployed that can host your content. To add content simply create files using any one of the formats that pagePark can render into your domains folder. 
