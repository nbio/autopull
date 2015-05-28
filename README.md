# autopull

1. `git pull`
2. Do something
3. Create a pull request
4. Profit!

## Configuration

This script uses several environment variables for configuration. Most must be set.

- `AP_REPO` — The GitHub repository, in the form of `user/repo`, e.g. `rails/rails`
- `AP_BRANCH` — The branch to check out. Default: `master`
- `AP_SETUP_CMD` — An optional command to run before running the update command.
- `AP_CMD` — The update command to run that mutates the repository. Default: `make update`
- `GH_USER` — The GitHub username (yours or a bot)
- `GH_TOKEN` – The GitHub access token (not your password!)
- `GIT_AUTHOR_NAME` and `GIT_COMMITTER_NAME` — The name of the user or robot doing the committing. Both must be set.
- `GIT_AUTHOR_EMAIL` and `GIT_COMMITTER_EMAIL` — The email address of the user or robot doing the committing. Both must be set.

## Quickstart on Heroku

1. Fork this repository
2. Create a new Heroku app
3. Set environment variables (see above)
4. Add the Heroku Scheduler add-on: `heroku addons:create scheduler:standard`
5. Configure the work schedule: `heroku addons:open scheduler`
6. Push your fork to Heroku: `git push heroku`
7. Test: `heroku run ./autopull`

## Credits

© 2015 nb.io, LLC
