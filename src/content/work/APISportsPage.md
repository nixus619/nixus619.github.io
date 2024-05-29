---
title: ESPN Sports Schedule
publishDate: 2020-05-22 00:00:00
img: /assets/NHLExample.png
img_alt: MLB Games Today
description: |
  Use the public ESPN API to display games for the day
tags:
  - API
  - Astro
  - Sports
---

## Background

This was my first project using Astro and I just wanted to develop something quick just to get my bearings. I chose to pull ESPN API and list games across the 4 major US sports to get familiar with the API for a future project (more on that later)

## The solution

The API used is the ESPN https://site.api.espn.com/apis/site/v2/sports/ end point configured for each league. The results are then parsed to pull the games for that day and shown in a clean format, complete with logos and time of the game (in EST).

One of the issues that came up was that the time format in the query needed to be in a specific format: ```YYYYMMDD```. Unfortunately, the today object returns values in the form of ```MMMM-MM-DDTHH:mm:ss.msZ ```, so I needed to properly slice the date up to get it in the proper format that the API accepts. This caused the final api end point to be this monstrosity (using MLB as an example): 

```javascript
'https://site.api.espn.com/apis/site/v2/sports/baseball/mlb/scoreboard?dates='
+today.getUTCFullYear()
+(("0" + (today.getUTCMonth()+1)).slice(-2))+(("0" + today.getUTCDate()).slice(-2)))
```

It's ugly but it works!

Another issue that came up was that the time for each game was returned in the UTC format, which isn't very appealing. So for example, lets say a response for a days worth of games looks like this:
![image](/assets/APIResponseExample.png)

Now we're back to that date and time that's in UTC format and not very easy on the eyes. So what I needed to do for this was to loop through each item and overwrite the date to the locale time:

![image](/assets/forLoop.png)


```javascript
for (let item=0; item < events.length; item++){
	var newDate = new Date(events[item].date);
	[item].date = newDate.toLocaleTimeString([], {
		hour: '2-digit', minute:'2-digit'
  });
}
```

A big drawback of what I've implemented here is that endpoints are called at build time. This means we will see some issues if the website is running for over a day as the endpoint is only called to fetch the data when the site is built. There is a way to turn it into live server end points that can be called on request via SSR mode, but more research would be needed to support this. This roadblock has led me to pursue another project which will use the same ESPN end point to populate game data on a virtual scoreboard. More information will be on another blog post.

#### Full Page Example
![image](/assets/fullPage.jpg)