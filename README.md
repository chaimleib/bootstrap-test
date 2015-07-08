# Bootstrap Test - Bower branch

This Rails app is a barebones test to get bootstrap installed on Heroku.

This branch uses bower to install bootstrap.

## Setup

Rails 4.2, Ruby 2.1.5, MySQL and the heroku toolbelt are required.

For this branch (bower), Node.js is also required.

After cloning this repo, some additional setup is required.

```bash
bundle
heroku create
heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git
heroku addons:create cleardb:ignite
heroku config:set "$(heroku config |
    grep CLEARDB_DATABASE_URL | 
    sed -e 's/^.*\/\//DATABASE_URL=mysql2:\/\//')"
git push -f heroku HEAD:master
```

## Hacking

If you make any changes, run

```bash
rake assets:precompile
rake assets:clean
git add public
git commit -m "your message here"
```

to precompile any changes to the assets. Otherwise, heroku will not update them when you deploy again using

```bash
git push -f heroku HEAD:master
```

