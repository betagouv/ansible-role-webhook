# ansible-role-webhook
Ansible role to install [adnanh webhooks server](https://github.com/adnanh/webhook)

Fork from https://github.com/andsild/ansible-webhook-role.

This webhook is _not_ complete and is still being developed

# Tasks

- Creates Group called webhook
- Creates webhook_user and adds to webhook group

# Role Variables

Set the username that will be used by webhooks
```
webhook_user: "webhook"
```

Set the group that will be used by webhooks
```
webhook_group: "webhook"
```

Add the webhook user to additional groups
```
webhook_extra_groups: ''
```

The default port that webhook will start on
```
webhook_port: '9000'
```

Below are different hook configuration, you can have multiple of these for each hook required
```
githubhooks:
      - id: "redeploy-webhook-github"
        cmd: "./reload.sh"
        cwd: "/var/"
        branch: master
        token: supersecretpassword
        args:
          - source: "url"
            name: "name"
gitlabhooks:
  - id: "redeploy-webhook-gitlab"
    cmd: "./reload.sh"
    cwd: "/var/"
    branch: ''
    token: supersecretpassword
    args:
      - source: "url"
        name: "name"
httphooks:
  - id: "test id"
    cmd: "./reload.sh"
    cwd: "/var/"
    responseMsg: "hello, world"
    branch: master
    token: secretsuper
```

Test script
```
ansible_unit_test: False
```

Optional arguments, see: [Webhook-Parameters](https://github.com/adnanh/webhook/blob/master/docs/Webhook-Parameters.md)
```
optional_args: ""
```
