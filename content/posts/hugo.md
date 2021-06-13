---
title: "Hugo"
date: 2021-06-12T12:49:17-07:00
draft: false
---

After reading [Julia Evans' notes](https://jvns.ca/blog/2016/10/09/switching-to-hugo/) on using Hugo for a blog , I decided to give it a try for myself. Part of the reason I didn't use my old blog is that publishing required editing the html manually. That meant a lot of work whenever I wanted to add a new post. Hugo automates a lot of that work for me. 

Of course, Hugo still requires some initial setup. Setting up Hugo itself is a breeze though, and installing most themes is as simple as a git pull. The hard part comes when you want to take a theme and customize it further. I'm really ~really~ bad when it comes to CSS/HTML editing, but I know enough to take an existing theme ([Console](https://github.com/mrmierzejewski/hugo-theme-console)) and to tweak it. 

## Styling

The Console theme makes home page editing really easy. Setting up the menu requires some parameters to be set in the config file. Tweaking the format of the main page required copying the theme index.html page to the project layouts directory and then making the changes. Changing the footer was easy too; just change the footer file directly in the theme directory. 

## Deploying

I used AWS Amplify for deployment. It made it super easy to deploy. All I had to do was link up my Github repo, and then configure the domain settings (under 'domain management') to use my Route53 domain. It automatically updates when I push code to the main branch. 

## Trouble

I didn't run into many problems during this project. The hardest one took 10-ish minutes to fix. I ran into a bug where Hugo wasn't showing my theme correctly, but that was because I didn't have the baseURL set correctly in my config file. Once that was solved, everything worked like a dream. 

I'd recommend Hugo for anyone starting a blog. It even works with [Github Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/), if you don't want to pay for hosting. Although Amplify is free for the first year and 0.02 cents a month after that, you can't beat free. I probably would have used Github Pages if I didn't already have my old homepage on it already (I want to leave the old pages domain up to point to my new one). 