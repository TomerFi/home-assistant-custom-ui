# Home Assistant Custom UI Components</br>![Maintenance](https://img.shields.io/maintenance/no/2019.svg)

**NOT MAINTAINED!**

I'm no longer maintaining this repository, this was a pre lovelace ui solution.</br>

You can still use the files :point_up:, if you want.</br>
These :point_down: are the instructions.

__________________________________________


This repository contains various Custom UI cards I've made for use with [Home Assistant](https://home-assistant.io/).</br>

My current developing environment is HassIO 0.65.5.</br>

## My Custom UI Components TOC
- [Script with Custom Text](#script-with-custom-text) for allowing custom text as script activation instead of the usuall ACTIVATE.

### Script with Custom Text
**Version** 20180419</br>
**Tested** with HA ios app, safari, chrome and internet explorer.</br>
[Community Discussion](https://community.home-assistant.io/t/change-the-activate-value-of-the-script-entities-custom-ui/50864)</br>
[Picture](/pics/state-card-script-custom-text.jpg)</br>

#### Installation
For installation of this custom ui, place the following files in your HA config/www/custom_ui:
- [config/www/custom_ui/state-card-script-custom-text.html](/www/custom_ui/state-card-script-custom-text.html)
- [config/www/custom_ui/state-card-script-custom-text-es5.html](/www/custom_ui/state-card-script-custom-text-es5.html)</br>

Open you *configuration.yaml* file and find the [*frontend* component](https://www.home-assistant.io/components/frontend/) (add it if you can't find it), configure it as such:
```yaml
frontend:
  extra_html_url:
    - /local/custom_ui/state-card-script-custom-text.html
  extra_html_url_es5:
    - /local/custom_ui/state-card-script-custom-text-es5.html
```

Next, in *configuration.yaml* find *homeassistant* and in it find the *customize_domain* key (add it if you can't find it), configure it as such:
```yaml
homeassistant:
  customize_domain:
    script:
      custom_ui_state_card: state-card-script-custom-text
```

**VERY IMPORTANT** after adding the custom ui card and restarting your Home Assistant, you'll need to clear the cache of your web-browser in use and refresh the page a couple of times so your web-browser will get the latest version of the card.</br>

#### Usage
For changing the ACTIVATE value for **specific** scripts, in *configuration.yaml* find *homeassistant* and in it find the *customize* key (add it if you can't find it), add a *custom_text* key for each script entity you want:
```yaml
homeassistant:
  customize:
    script.my_first_script:
      custom_text: "WHATEVER1"
    script.my_first_script:
      custom_text: "WHATEVER2"
```

For changing the ACTIVATE value **globaly** for all of your script, add the following line to the already configured *customize_domain* key:
```yaml
homeassistant:
  customize_domain:
    script:
      custom_ui_state_card: state-card-script-custom-text
      custom_text: "WHATEVER"
```
