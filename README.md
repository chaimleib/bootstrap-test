# Bootstrap Test

This Rails app is a barebones test to get bootstrap installed on Heroku.

## Setup

Rails 4.2, Ruby 2.1.5, MySQL and the heroku toolbelt are required.

After cloning this repo, some additional setup is required.

```bash
bundle
heroku create
heroku addons:create cleardb:ignite
heroku config:set "$(heroku config |
    grep CLEARDB_DATABASE_URL | 
    sed -e 's/^.*\/\//DATABASE_URL=mysql2:\/\//')"
git push -f heroku
```
