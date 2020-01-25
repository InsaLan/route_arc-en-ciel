# IP Route Arc-En-Ciel : Automated IP Route Deployment Script

## Configuration

Write your configuration in the file called `config.json` where you run Route ArcEnCiel. Your configuration will contain two tables :

```json
{
	"vlan": {
		"<vlan_number>": "<vlan_subnet>",
		...
	},
	"vpn": {
		"<table name>": "<vpn_subnet>",
		...
	}
}
```

where :
 - `<vlan_number>` is a number, like `101` or `150`, used to determine the name of a network interface.
 - `<vlan_subnet>` is a subnet in the likes of `172.16.18.0`. All of the machines with an ip address on the VLAN should have an ip in that range.
 - `<table_name>` is the name of an ip rule table. Commonly, they correspond to the names of the hosts they are associated with. These tables should be set in another script.
 - `<vpn_subnet>` is the subnet of the VPN, like `10.8.34.0`.

It is important that all subnets be written with only one digit after the last period, otherwise some string slicing boondongery in Route ArcEnCiel will not work.

## Running

Simply pipe the output to your favourite capable shell. Even error messages are written as `echo` commands, so don't worry.

```bash
./route_aec | sh
```
