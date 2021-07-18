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

One of the features of pagePark is that it knows how to serve a variety of different file formats. For example, I am writing and storing this page in markdown but if you view source you will see the HTML code that pagePark has generated so that this page displays in your web browser nicely.

Pagepark also does this for the outline file format, OPML. To render an OPML an OPML file pagePark generates the HTML using a template file that contains several script source entires that have URLS using http. Because Digital Ocean app platform automatically deploys apps with https the result of the default configuration is that most browsers will not render the OPML because of mix of secure and non-secure content. 

The browser co's enforcement of HTTPS is rearing its head here.  If you view source you see Pagepark is dynamically generating HTML for OPML files that includes Javascript sources from "non-secure" HTTP sites, and browsers are no longer displaying non-secure content by default. Chrome, Edge, and Firefox do not provide an obvious way for a user tell it to display non-secure content. 

For now, in Chrome, one can click the lock to the left of the URL, then click Site settings, scroll down to Insecure content and change it from Block(default), to Allow. At this the browser will display a "Not secure" Indicator to the left of the URL. Most likely Google will remove this ability in the future and the other browser companies will follow suite.

As an experiment I set out to see if I could configure a deployment of pagePark on Digital Ocean platform that gets past the "mixed content" issue, and I did the following:

1. Downloaded all of the non-secure source files to a code subdirectory of pagepark.frankmcpherson.net domains subdirectory. 
2. I copied the templates directory to /domains/pagepark.frankmcpherson.net
3. I edited opml/template.txt file so that all the <script src=></script> links used the https://pagepark.frankmcpherson.net/code URL created in step 1 above
4. I changed the value of urlDefaultOpmlTemplate in config.json to http://pagepark.frankmcpherson.net/templates/opml/template.txt

NOTE: The full URL of urlDefaultOpmlTemplate must be prefixed with http. I originally used https and it did not work, the browser would appear to just continuously try to load. I also tried various forms of local file system directory paths that also did not work, it wasn't until I provided a URL format as shown above that I finally got this instance of pagePark to successfully render an OPML file.

To see the results the tweaks outlined above to make this work, open https://pagepark.frankmcpherson.net/tech.opml and view source in a browser. To see the config.json load https://pagepark.frankmcpherson.net/status

## Now what?

Map your own domain or subdomain to the application by creating a CNAME record with your DNS provider. Finally, create a directory that has the same name as the URL you just configured via DNS in the domains directory of your repo, and put an index.md file in it to display a page.

At this point you have a web server deployed that can host your content. To add content simply create files using any one of the formats that pagePark can render into your domains folder. 

Finally, in terms of cost, the lowest cost option is $5 per month for 512MB of RAM and 1 vCPU, which should be plenty of capacity unless get slash-dotted. With this plan you also get 40 GB of outbound transfer and 400 build minutes. Digital Ocean calls this the prototype option, "production" applications may warrant more outbound data transfer and build minutes that will cost $12 per month. 

BTW, if you are looking to host a static site, basically HTML files that you build by hand, you can do so for free (up to three) on Digital Ocean.