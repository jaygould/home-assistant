# Home Assistant

This repo is an example for how to integrate third party add ons to Home Assistant that is installed using Kubernetes.

## Example config

A sample `configuration.yaml`:

```
# Loads default set of integrations. Do not remove.
default_config:

# Load frontend themes from the themes folder
frontend:
  themes: !include_dir_merge_named themes

automation: !include automations.yaml
script: !include scripts.yaml
scene: !include scenes.yaml

http:
  use_x_forwarded_for: true
  trusted_proxies:
    - 10.42.1.0/24
    - 127.0.0.1
    - ::1

meassistant:
  auth_mfa_modules:
    - type: totp

alexa:
  smart_home:
    filter:
        exclude_entity_globs:
          - automation.*
          - update.*
          - select.*
          - switch.*_do_not_disturb_switch
          - switch.*_repeat_switch
          - switch.*_shuffle_switch
          - sensor.*_linkquality
          - sensor.*_battery
```
