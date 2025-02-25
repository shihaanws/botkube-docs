---
menutitle: "Communication"
title: "Communication"
weight: 10
---

The communication settings contains:

- Communication platforms configuration,
- Option to toggle notification type to short or long.

## Syntax

```yaml
# Communication mediums configuration
communications:
  # Settings for Slack
  slack:
    enabled: false
    channel: 'SLACK_CHANNEL'            # Slack channel name without '#' prefix
                                        # where you have added BotKube and
                                        # want to receive notifications in
    token: 'SLACK_API_TOKEN'            # Slack token received after installing
                                        # BotKube Slack app to a workplace
    notification:
      type: short                       # Change notification type short/long.
                                        # Type is optional and default is short.

  # Settings for Mattermost
  mattermost:
    enabled: false
    url: 'MATTERMOST_SERVER_URL'        # URL where Mattermost is running.
                                        # e.g https://example.com:9243
    token: 'MATTERMOST_TOKEN'           # Personal Access token generated by BotKube user
    team: 'MATTERMOST_TEAM'             # Mattermost Team to configure with BotKube
    channel: 'MATTERMOST_CHANNEL'       # Mattermost Channel for receiving BotKube alerts
    botName: 'BotKube'                  # Bot username    
    notification:
      type: short                       # Change notification type short/long.
                                        # Type is optional and default is short.

  # Settings for Microsoft Teams
  teams:
    enabled: false
    appID: 'APPLICATION_ID'
    appPassword: 'APPLICATION_PASSWORD'
    botName: 'BotKube'
    port: 3978
    notification:
      type: short                       # Change notification type short/long.
                                        # Type is optional and default is short.

  # Settings for Discord
  discord:
    enabled: false
    token: 'DISCORD_TOKEN'	            # BotKube Bot Token
    botID: 'DISCORD_BOT_ID'             # BotKube Application Client ID
    channel: 'DISCORD_CHANNEL_ID'       # Discord Channel id for receiving BotKube alerts
    notification:
      type: short                       # Change notification type short/long.
                                        # Type is optional and default is short.

  # Settings for ELS
  elasticsearch:
    enabled: false
    awsSigning:
      enabled: false                    # enable awsSigning using IAM for Elastisearch
                                        # hosted on AWS, if true make sure AWS
                                        # environment variables are set.
                                        # Ref: https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html
      awsRegion: 'us-east-1'            # AWS region where Elasticsearch is deployed
      roleArn: ''                       # AWS IAM Role arn to assume for credentials,
                                        # use this only if you dont want to
                                        # use the EC2 instance role or not
                                        # running on AWS instance
    server: 'ELASTICSEARCH_ADDRESS'     # e.g https://example.com:9243
    username: 'ELASTICSEARCH_USERNAME'  # Set creds if using Basic Auth
    password: 'ELASTICSEARCH_PASSWORD'
    # ELS index settings
    index:
      name: botkube
      type: botkube-event
      shards: 1
      replicas: 0

  # Settings for Webhook
  webhook:
    enabled: false
    url: 'WEBHOOK_URL'                 # e.g https://example.com:80
```

The default configuration for Helm chart can be found in [values.yaml](https://github.com/kubeshop/botkube/blob/main/helm/botkube/values.yaml).
