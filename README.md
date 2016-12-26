# To Connnect the Drone to an SSID:

## Connect to the Drone's Hotspot
### In terminal
`telnet 192.168.1.1`
`cd bin`
`vi wifi_setup.sh`

#### Add the following line to wifi_setup.sh
#### 1. Replacing $Name with name of wireless network you want the drone to connect to.
#### 2. Replace the ip address with a static ip address for your network
Example:  Phone is broadcasting a hotspot called $Name.  When drone boots, it will connect to the network rather than try and be it's own hotspot.  It will request the static ip set 192.168.2.7.

`killall udhcpd; iwconfig ath0 mode managed essid #Name; ifconfig ath0 192.168.2.7 netmask 255.255.255.0 up;`


## IP-Address Jargon:
The official parrot mobile app looks for the drone on 192.168.1.1, thus most node.js implementations do the same by default.  In the example above, we set the ip address to 192.168.2.7.  So we set the ip-address on the node client to that

### Node-JS Implementation
### Where the ip is the address specified above.
var arDrone = require('ar-drone');
var drones = [
  arDrone.createClient({ip: '192.168.2.7'})

];



