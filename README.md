<p align="center">
<img src="branding/network_homebridge.png" width="500px">
</p>

# homebridge-network-presence


[Homebridge](https://github.com/homebridge/homebridge) plugin that provides occupancy sensors for devices presence on your network based on mac address or IP.

### Requirements

<img src="https://img.shields.io/badge/node-%3E%3D10.17-brightgreen"> &nbsp;
<img src="https://img.shields.io/badge/homebridge-%3E%3D0.4.4-brightgreen">

check with: `node -v` & `homebridge -V` and update if needed

## Description

This plugin is a fork of the excellent [homebridge-network-presence](https://github.com/nitaybz/homebridge-network-presence) by [@nitaybz](https://github.com/nitaybz) but uses the [OPNsense](https://opnsense.org/) ARP table instead of ping.

With this plugin you can easily configure devices to monitor based on their mac address, ip address or hostname.

## Config File Example

``` json
"platforms": [
	{
		"platform": "OpnsensePresence",
		"interval": 10,
		"threshold": 15,
		"anyoneSensor": true,
		"routerDomain": "https://myrouter/",
		"routerKey": "blahvkey",
		"routerSecret": "verysecret",
		"devices": [ 
			{
				"name": "my iPhone",
				"mac": "cc:29:f5:3b:a2:f2",
				"threshold": 5
			},
			{
				"name": "my iPad",
				"ip": "10.0.0.142"
			},
			{
				"name": "my Apple Watch",
				"hostname": "joes-applewatch.local"
			}
		],
		"debug": false
	}
]
```

### Configurations Table

|             Parameter            |                       Description                       |  Default |   type   |
| -------------------------------- | ------------------------------------------------------- |:--------:|:--------:|
| `platform`  | always `"OpnsensePresence"` |     -    |  String  |
| `interval`  |  Time in seconds between status polling for connected devices   |  `10` |  Integer |
| `threshold`  |  Time in minutes to wait before updating 'disconnected' status. important for not spamming your notifications or wrongly activating automation because the device has gone from the network for short time   |  `15` |  Integer |
| `routerDomain` | Domain of your OPNsense router for API access | | String |
| `routerKey` | API Key for your router | | String |
| `routerSecret` | API Secret for your router | | String |
| `anyoneSensor`       |  When set to `true`, the plugin will create extra accessory named "Anyone" to represent if ANY of the devices is detected        |  `false` |  Boolean  |
| `debug`       |  When set to `true`, the plugin will produce extra logs for debugging purposes        |  `false` |  Boolean  |
| **Devices** | List of devices to monitor (with the below information)| | Array|
| `name`        | Name of the accessory in HomeKit  |         |  String  |
| `mac`        | Mac Address of the device e.g. `cc:29:f5:3b:a2:f2` (can use `ip` or `hostname` instead) |         |  String  |
| `ip`        | ip Address of the device (can use `mac` or `hostname` instead) |         |  String  |
| `hostname`        | Hostname of the device (can use `mac` or `ip` instead) |         |  String  |
| `threshold`  | device disconnect threshold (overrides platform threshold)   |  `15` |  Integer |

## Issues & Debug

If you experience any issues with the plugins please refer to the [Issues](https://github.com/hackherz/homebridge-opnsense-presence/issues) tab
and check if your issue is already described there, if it isn't, please report a new issue with as much detailed information as you can give (logs are crucial).<br>
if you want to even speed up the process, you can add `"debug": true` to your config, which will give me more details on the logs and speed up fixing the issue.


-----------------------

## Support homebridge-opnsense-presence

**homebridge-opnsense-presence** is a free plugin under the MIT license. it was developed as a contribution to the homebridge/hoobs community with lots of love and thoughts.
Creating and maintaining Homebridge plugins consume a lot of time and effort and if you would like to share your appreciation, feel free to "Star".
