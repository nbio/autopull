# autopull

Bash script that auto-creates Pull Requests for a given repo.

## How it works

1. Clones the to-be-updated repo (`AP_REPO`) into a tmp dir
1. Does stuff (`AP_CMD`)
1. Creates a PR for the changes
1. Profit!

## Configuration

This script uses environment variables for configuration; most must be set. Examples are from the [ZoneDB](http://zonedb.org/) project, which updates its data daily.

- `AP_REPO` — GitHub repository to auto-update, in the form of `user/repo`, e.g. [`zonedb/zonedb`](https://github.com/zonedb/zonedb)
- `AP_BRANCH` — Branch to check out. Default: `master`
- `AP_SETUP_CMD` — Optional command to run before running the update command, e.g. for installing dependencies.
- `AP_CMD` — Update command that mutates the repository. Default: `make update`
- `GH_USER` — GitHub username (yours or a bot)
- `GH_TOKEN` – GitHub [access token](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) (not your password!)
- `GIT_AUTHOR_NAME` and `GIT_COMMITTER_NAME` — Name of the user or robot doing the committing. Both must be set.
- `GIT_AUTHOR_EMAIL` and `GIT_COMMITTER_EMAIL` — Email address of the user or robot doing the committing. Both must be set.

## Heroku quickstart

1. Clone (or fork) this repository
1. Create a Heroku app, which will run the `autopull` script
1. Set the above environment variables
1. Add the Heroku Scheduler add-on: `heroku addons:create scheduler:standard`
1. Configure the work schedule: `heroku addons:open scheduler` and command to run (`./autopull`)
1. Push your fork to Heroku: `git push {your Heroku app's git remote}`
1. Test: `heroku run ./autopull -a {your Heroku app name}`

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/weppos/autopull)

## Python example

- `AP_CMD` — `python3 script.py`
- `AP_SETUP_CMD` — `pip3 install -r requirements.txt`

## Credits

© 2015 nb.io, LLC
