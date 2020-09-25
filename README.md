# ansible-webhook-role
Ansible role to install [adnanh webhooks server](https://github.com/adnanh/webhook)

Fork from https://github.com/reikjarloekl/ansible-webhook-role. Deviates by not install nginx, and making the hooks.json a partially complete jinja template.

This webhook is _not_ complete with configurable variables, so I won't document it extensively. You can have a look at ./tests/test.yml to get an idea on how to use the role yourself.

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

```
prefix_dir: ""
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





```
ansible_unit_test: False
```

```
optional_args: ""
```
