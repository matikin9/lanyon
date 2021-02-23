---
layout: post
title: Open Data Portal - Part 2
date: 2022-02-22 23:30
tags: open-data
---

I had been thinking about Datasette all wrong.  I'm used to working with static websites where I download code, modify it at will and upload it somewhere to get served as a website.  Instead I need to think of Datasette as an application I can install.

`$ pip install datasette`

Then I install `sqlite-utils`, the library made by the Datasette creator to make it easier to manipulate sqlite databases.

`$ pip install sqlite-utils`

I got the `routes.txt` file from Metro's bus GTFS data and loaded it into a sqlite database.

`$ sqlite-utils insert routes.db routes routes.txt --csv`

[The documentation](https://sqlite-utils.datasette.io/en/stable/index.html) is a little bit vague on this but I believe the command format is:

`$ sqlite-utils insert [database-name.db] [table-name] [source-file-name.ext] --[delimiter]`

__OF COURSE__ after I go through this I find this other library from the Datasette creator... [csvs-to-sqlite](https://github.com/simonw/csvs-to-sqlite/).  It's even easier to turn a csv into a sqlite database.

`$ pip install csvs-to-sqlite`

The README doesn't mention this but it will add a new table to an existing database.

`$ csvs-to-sqlite trips.txt routes.db`
`$ sqlite-utils tables routes.db --counts`
`[{"table": "routes", "count": 134},`
`{"table": "trips", "count": 27912}]`

You can even pass it multiple files and it will bundle them into a single database:

`$ csvs-to-sqlite routes.txt trips.txt gtfs-bus.db`

Run Datasette using this new gtfs-bus.db and I see a top level heading of gtfs-bus (the database) with routes and trips listed (the tables, which are just individual files).  SQL querying worked.

## Publishing

I used the auto-updating standalone installation because the 'snap' install didn't work.

`$ curl https://cli-assets.heroku.com/install.sh | sh`

Logging in to my Heroku account was super easy. I crossed my fingers and ran the publish command... and it FAILED because the name 'datasette' was already taken.  What a dumb error, of course I need to give it a unique name.

`$ datasette publish heroku gtfs-bus.db -n datasette-gtfs-bus`

Voilà: [Datasette demo running GTFS bus data](https://datasette-gtfs-bus.herokuapp.com/)!

