[![](https://img.shields.io/github/release/sermayoral/ha-samsungtv-encrypted/all.svg?style=for-the-badge)](https://github.com/sermayoral/ha-samsungtv-encrypted/releases)
[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg?style=for-the-badge)](https://github.com/custom-components/hacs)
[![](https://img.shields.io/github/license/sermayoral/ha-samsungtv-encrypted?style=for-the-badge)](LICENSE)
[![](https://img.shields.io/badge/MAINTAINER-%40sermayoral-red?style=for-the-badge)](https://github.com/sermayoral)
[![](https://img.shields.io/badge/COMMUNITY-FORUM-success?style=for-the-badge)](https://community.home-assistant.io)

# HomeAssistant - SamsungTV Encrypted Component

This is a custom component to allow control of Encrypted SamsungTV devices in [HomeAssistant](https://home-assistant.io). 
This should work on H and J 2014/2015 models (according to [PySmartCrypto](https://github.com/eclair4151/SmartCrypto) specs).
Is a modified version of the built-in [samsungtv](https://www.home-assistant.io/integrations/samsungtv/) with some extra features:

# Additional Features:

* Send keys using a native Home Assistant service (WIP)
* Customize source list at media player dropdown list (WIP)

# Installation (There are two methods, with HACS or manual)

### 1. Easy Mode

We support [HACS](https://hacs.netlify.com/). Go to "STORE", search "SamsungTV Encrypted" and install.

### 2. Manual

Install it as you would do with any homeassistant custom component:

1. Download `custom_components` folder.
2. Copy the `samsungtv_encrypted` direcotry within the `custom_components` directory of your homeassistant installation. 
The `custom_components` directory resides within your homeassistant configuration directory.
**Note**: if the custom_components directory does not exist, you need to create it.
After a correct installation, your configuration directory should look like the following.

    ```
    └── ...
    └── configuration.yaml
    └── custom_components
        └── samsungtv_encrypted
            └── __init__.py
            └── media_player.py
            └── manifest.json
            └── get_token.py
            └── PySmartCrypto
                └── pysmartcrypto.py
    ```

# Configuration

1. Use get_token.py to get your Samsung TV token (use --port 8080). Store CTX <TOKEN> and <SESSION_ID> output. Your TV must be turned on and connected to Internet with the specific IP. Terminal where you have executed get_token.py will ask for a PIN, that will be showed in your TV screen.
2. Enable the component by editing the configuration.yaml file (within the config directory as well).
Edit it by adding the following lines:
    ### Example configuration.yaml
    ```
    media_player:
      - platform: samsungtv_encrypted
        host: IP_ADDRESS
        token: TOKEN
        sessionid: SESSION_ID
        port: 8080
    ```
    **Note**: This is the same as the configuration for the built-in [Samsung Smart TV](https://www.home-assistant.io/integrations/samsungtv/) component, except for the custom variables.

    ### Custom variables

    - **token:** (string) This contains the token of your encrypted TV (got in step 1)<br>

    - **sessionid:** (string) This contains the sessionid of your encrypted TV (got in step 1)<br>
    
2. Reboot Home Assistant
3. Congrats! You're all set!

# Working Models

- **H6400**
- **H6200**
- **H5500AW**
- **HU7500**
- **HU8550**

***References***
----------------

- The code list has been folked from: https://github.com/arturleao/samsungtv_custom<br>
- If you want to buy me a coffee: https://www.buymeacoffee.com/XAF0dnBOG
