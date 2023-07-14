---
layout: single
title: Projects
permalink: /projects/
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  #change to different image
  overlay_image: /assets/images/cape-breton.JPG
author_profile: true
classes: wide

sports-stats-app:
  - image_path: assets/gif/sports-app.gif
    alt: "Football League App"
    title: "Football Stats App"
    excerpt: "A Web React application I created to display Football Stats from my 6 favourite leagues around the world. Standings data is automatically updated once every week on Mondays, done with Github Actions, on a Workflow Cron Job. Link to [live site](https://emilioroche.github.io/sports-stats/) is down until I find a replacement hosting service as Heroku got rid of free Dynos."
    url: "https://github.com/EmilioRoche/sports-stats"
    btn_label: "Demo"
    btn_class: "btn--primary"
    tags:
      - React
      - Bootstrap
      - NodeJS
      - Heroku Cloud
      - Heroku Postgres DB
      - Github Actions

twitter-bot:
  - image_path: assets/gif/twitter-bot-correct.gif
    alt: "Twitter Fruit Bot"
    title: "Twitter Fruit Bot"
    excerpt: "A twitter user can @fruta_bot asking about calories in a specific fruit, and the bot will auto reply with the correct response about the fruit and its calories. Keyword(s) is specified to 'calories', and can filter out what fruit is mentioned in the tweet."
    url: "https://github.com/EmilioRoche/twitter-bot"
    btn_label: "Demo"
    btn_class: "btn--primary"
    tags:
      - Python
      - Twitter API
      - Heroku Cloud
---

# Projects

{% include feature_row id="sports-stats-app" type="left" %}
<a name="Football Stats"></a>
{% include feature_row id="twitter-bot" type="left" %}
<a name="Twitter Bot"></a>
