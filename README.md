# kuroAntiSpam

kuroAntiSpam.py is a python script that uses your Mastodon instance's api to ban bots who make posts that match ALL of the following conditions:

- Post has "ja" set in language field
- Post @-mentions more than 3 accounts
- Post author has no avatar set
- Post body contains "https://荒らし.com/" OR "https://ctkpaarr.org/"

If these conditions are met, a report is filed for the user, the user is suspended, and the instance it came from is blocked if there is no follower/following relationship between any users on your instance and the bot's.


## Required permissions:

These permissions are required for the script to function:

- read:statuses - Check the public timeline
- write:reports - Write a report on the bot
- admin:read - Check if your instance shares any follow/ers between your instances
- admin:write:accounts - Suspend the bot
- admin:write:domain_blocks - Block the domain if there are no follow/ers (only needed if you want to silence or suspend the domain)
- admin:write:reports - Close the report


The permissions are needed for these api calls:

- /api/v1/timelines/public
- /api/v1/reports
- /api/v1/admin/measures
- /api/v1/admin/accounts/:id/action
- /api/v1/admin/domain_blocks


## Use

Edit kuroAntiSpam.py to change the YOUR_DOMAIN and ACCESS_TOKEN variables. You may also change how often the script checks the timeline, and how many posts it checks.
You can change `DOMAIN_ACTION` to say what should happen to the domain of the instance the spam was detected on.

``python kuroAntiSpam.py``
