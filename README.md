# Etherpad-Lite Heroku

Deploy Etherpad-Lite on Heroku. Whole Etherpad-Lite configuration, including plugins, can be specified in Heroku configuration variables (ENV).
 
## Running

### Configuration

Configuration can be specified in 2 ways:

* File (`config/local.json`) - designed for development environments where file configuration is simpler to maintain than env variables. See the example [local.json](config/local.json.example)
* Environment variables - this is where all Heroku configuration variables show up.

**NOTE:** Environment variables override `config/local.json`.

#### Etherpad-Lite configuration variables 

Standard:

* `ETHERPAD_SETTINGS` - JSON string of the whole standard Etherpad-Lite `settings.json`.
* `ETHERPAD_SESSION_KEY` - The secret stored in Etherpad-Lite `SESSIONKEY.txt`.
* `ETHERPAD_API_KEY` - The secret stored in Etherpad-Lite `APIKEY.txt`.

Non-standard:

* `DATABASE_URL` - Default database URI environment variable set by Heroku. It overrides all other DB configurations.
* `___apiKey` - The secret stored in Etherpad-Lite `APIKEY.txt`.
* `___sessionKey` - The secret stored in Etherpad-Lite `SESSIONKEY.txt`.
* `___version` - Per plugin configuration. Version of plugin to be installed by NPM.

#### Plugin configuration

Plugin version and configuration can be specified. Plugins are configured as you would normally do in Etherpad-Lite `settings.json`, but you can also specify plugin version which will be installed by NPM.

* `___version` - version of the plugin to be installed.

Example plugin config in `ETHERPAD_SETTINGS` or `config/local.json`:

```
  "ep_themes_ext": {
    "___version": "0.0.4",
    "default": [
      "https://dev.citizenos.com:3001/static/styles/etherpad.css"
    ]
  }
```

### Run

#### Heroku

Push it to your Heroku and Heroku will just run it picking up the entry point from [Procfile](Procfile)

#### Locally

* `npm run start-dev`

## Credits
 
* This project started as a fork of https://github.com/bright-star/etherpad-lite-heroku and basic concepts are borrowed from there.
* [CitizenOS](https://citizenos.com) for funding the development