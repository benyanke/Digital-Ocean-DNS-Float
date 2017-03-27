# Digital Ocean DNS Update

This script allows remote devices to update DNS A records without needing to give them complete access to the Digital Ocean account with API keys on the client side.


To set up, rename info-example.json to info.json, and add keys and domains.


## Example Set Up

Given the details in the example file, a call to this URL:

http(s)://[location-of-script]/?statictoken=pick-any-token-you-wish

Would update server1.example.com and thething.example.org to the public IP address of the client requesting the URL using the API keys listed in the top of the file.

Additionally, if you want to specify an IP explicitly, you can set the *ip* attribute in the url. For example: 

http(s)://[location-of-script]/?statictoken=pick-any-token-you-wish&ip=1.2.3.4
