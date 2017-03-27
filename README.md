# Digital Ocean DNS Update

This script allows remote devices to update DNS A records without needing to give them complete access to the Digital Ocean account with API keys on the client side.


To set up, rename info-example.json to info.json, and add keys and domains.


## Example Server Setup

Given the details in the example json file, a call to the URL below would update server1.example.com and thething.example.org to the public IP address of the client requesting the URL using the API keys listed in the top of the file, and associated with the entry.

~~~~
http(s)://[location-of-script]/?statictoken=pick-any-token-you-wish
~~~~

Additionally, if you want to specify an IP explicitly, you can set the *ip* attribute in the url. For example: 

~~~~
http(s)://[location-of-script]/?statictoken=pick-any-token-you-wish&ip=1.2.3.4
~~~~


## Example Client Setup
Because it's simply a web request, a curl command in your cron file can be all you need. For example, the following command would update the IP every 5 minutes. Or, you could pipe the output to a log file if you wish.

~~~ bash
# Update dynamic ip
*/5 * * * * curl http(s)://[location-of-script]/?statictoken=pick-any-token-you-wish >/dev/null 2>&1
~~~


## More Advanced Setup
If you have multiple public interfaces, you could parse the output of `ifconfig` and explicitly specify the IP, to ensure it gets updated correctly, no matter which interface the request goes out. The possibilities are endless.

## Todo
* Read current record value from API instead of DNS query: more robust and lowers load (during DNS propagation delay)


## Miscellany
I simply wrote this for my own use, and provide no guarantees about it. I'll gladly accept pull requests for feature adds or bug fixes. 
