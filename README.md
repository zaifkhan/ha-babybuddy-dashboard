# 🍼 Baby Buddy Dashboard for Home Assistant

A beautiful, interactive, and responsive custom dashboard for Home Assistant that tightly integrates with the [Baby Buddy](https://github.com/babybuddy/babybuddy) backend.

![Dashboard Preview](docs/babybuddy-dashboard.png) 

## ✨ Features
* **Instant Sync:** 2-way background syncing. Start a timer on your phone, and the HA dashboard updates instantly. 
* **Interactive Active Banners:** Pulsing banners show exactly what activity is running and for how long.
* **Smart Edit Popups:** Tap an active banner to edit its start time, or tap the pencil icon to edit/delete past entries right from the dashboard.
* **Orphan Timer Catching:** Warns you if an unclaimed timer is running in Baby Buddy and lets you assign it to an activity with one tap.
* **Custom Sleep & Feed Tables:** Formatted historical logs right on the UI.

## 📋 Prerequisites
You must have the following set up and installed before generating your code:

**1. The Baby Buddy Server:**
Baby Buddy must be already set up and running. You can host this in multiple ways:
* [Official Docker Container](https://github.com/babybuddy/babybuddy)
* [Home Assistant OS Add-on](https://github.com/OttPeterR/addon-babybuddy)

**2. Home Assistant Backend:**
* [Baby Buddy HACS Integration](https://github.com/jcgoette/baby_buddy) (Provides the base services and timer switches).

**3. Home Assistant Frontend (Install via HACS):**
* [Browser Mod](https://github.com/thomasloven/hass-browser_mod) (For the edit/delete popups).
* [button-card](https://github.com/custom-cards/button-card) (For the layout and UI logic).
* [flex-table-card](https://github.com/custom-cards/flex-table-card) (For the historical logs).
* [card-mod](https://github.com/thomasloven/lovelace-card-mod) (For borderless styling).

## 🚀 Installation

Because this setup requires custom helpers, REST commands, and specific entity names. Use the **Web Generator** that writes all the code for you based on your setup.

### [👉 Click here to open the YAML Generator](#) 

### Setup Instructions:
1. Open the generator and input your Baby Buddy server details and Child's name.
2. **Configure Secrets:** Open your Home Assistant `secrets.yaml` file and add your API token exactly like this:
   `babybuddy_token: "Token YOUR_ACTUAL_API_TOKEN"`
3. **Save the Package:** Create a folder named `packages` inside your Home Assistant `config` directory. Copy the **Package YAML** from the generator and save it as a new file named `babybuddy_dashboard.yaml` inside that `packages` folder.
4. **Enable Packages in Home Assistant:** If you haven't used packages before, you must tell Home Assistant to load them. Open your `configuration.yaml` file and add the following lines (ensure they fall under the main `homeassistant:` block):
   ```yaml
   homeassistant:
     packages: !include_dir_named packages
