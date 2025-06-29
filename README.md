# Local GitLab

This repo contains GItLab configuration to make your own local GitLab server using docker. It also has a configuration for gitlab runner

## Installation

To install ypur local GitLab server in docker, please, follow this steps:

1. Clone this repo to your local PC
2. Open terminal in repo folder
3. Use this command ```docker-compose up -f .\local-gitlab.docker-compose.yml -d```
4. Wait until both gitlab and runner will installed. Usually it takes about 10-20 mins depend on your PC hardware
5. Open your [gitlab](http:gitlab.local:8888) and login with following credits - username: root, pass: 42314231
6. Congratulations!

## Setting up runner

To connet your local runner use following steps:

1. Move to your local repo or create empty if you don't have one in GitLab
2. Move to Settings > CI/CD
3. Expand "Runners" Tab and hit "Create project runner"
4. Set "Run untagged jobs" checkbox to true. Optionally u also may set other fields like description and tags
5. Hit "Create runner" button
6. Then gitlab will give you instructions how to finish your runner setup. You just need to copy generated key. It located in step 1. You should get something like this ```gitlab-runner register  --url http://gitlab.local:8888  --token {HERE_WILL_BE_YOUR_TOKEN}```
7. Copy token and move to ```./your_repo/config/runner_config.tml```
8. Change ```token = {some_token}``` setting at line 10 of configuration with your token
9. Restart runner container

After this steps try to run test pipeline to ensure your runner succesfully connected and it can successfully run your pipelines
