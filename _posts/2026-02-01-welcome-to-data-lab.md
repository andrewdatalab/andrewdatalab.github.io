---
title: Welcome to Andrew's Data Lab
date: 2026-02-01 20:00:00 +1100
categories: [General, Introduction]
tags: [welcome, chirpy]
---

## Introduction
This is my first post on my new Chirpy blog. I'll be sharing my journey through networking, cloud, and AI.

### My Goals
1. Document technical projects.
2. Share insights on **AI** related topic including automation.
3. Explore **AI Agents** in automation.

> This blog is a playground for learning and sharing.

### How to Chirpy on Github
1. Use the Template: On the Chirpy Starter page, click the green "Use this template" button and select "Create a new repository".
2. Name it: Name the new repository andrewdatalab.github.io.
3. Initialize: Click "Create repository from template".
4. Critical Configuration for the Sidebar. Once the repo is created, open _config.yml and update these lines immediately so your site builds correctly:
<pre># Site Settings
title: Andrew Data Lab
tagline: IP, Network, and Automation Journey
url: 'https://andrewdatalab.github.io' # No trailing slash
baseurl: '' # Must be empty for your username repo

# Identity
author: Andrew Nam
timezone: Australia/Sydney # Set for correct post dating
</pre>
5. Enable the "About" Page. In Chirpy, the "About" link in the sidebar is controlled by the tabs/ folder.
<pre>
  ---
layout: about
icon: fas fa-info-circle
order: 4
---

This is the personal blog of Andrew Nam...
</pre>
