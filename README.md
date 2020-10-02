# ansible-role-webhook
Ansible role to install [adnanh webhooks server](https://github.com/adnanh/webhook)

Fork from https://github.com/andsild/ansible-webhook-role.

This webhook has configurable variables that are missing from the original fork

# Role Variables

- `webhook_version`: Sets the version of webhook to install `2.7.0`
- `webhook_checksum`: Sets the checksum for the version to install defaults `md5:8bb63914f4ead672ff43191e91b0249f`
- `webhook_user`: Set the user that webhook will use dafaults `webhook`
- `webhook_group`: Set the group that webhook will use defaults `webhook`
- `webhook_extra_groups`: sets any additional groups webhook requires
- `webhook_port`: sets the port that webhook will listen defaults `9000`
- `optional_args`: Optional arguments, see: [Webhook-Parameters](https://github.com/adnanh/webhook/blob/master/docs/Webhook-Parameters.md)
- `githubhooks:[]`: Required for Github hooks
- `gitlabhooks:[]`: Required for Gitlab hooks
- `httphooks:[]`: Required for http hooks

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
