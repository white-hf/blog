This article documents how I installed a USB Wi-Fi adapter on a MintBox running Linux.
I purchased a used MintBox to use as a Linux server for development. Unfortunately, it could only access the internet via a network cable because the previous owner had lost the antennas. To solve this, I bought a USB Wi-Fi adapter on Temu for $10. However, as the saying goes, "cheap things aren’t always cheap"—the driver code provided was outdated and couldn’t be compiled on the newer kernel.

Here’s how I finally got it to work:
- I found an alternative driver on GitHub, which worked perfectly. You can find it [here](http://https://github.com/gglluukk/rtl8188eus "here").
- I configured the Wi-Fi using the following Linux commands:
  1. Check the network devices: "ifconfig -a"
  2. Enable the wireless network card: "ifconfig yours up"
  3. Scan for available wireless networks: "iwlist yours scan"
  4. Generate configure file for wpa_supplicant: "sudo wpa_passphrase yours >> /etc/wpa_supplicant.conf"
  5. Connect to a wireless network: "wpa_supplicant -B -i yours -c /etc/wpa_supplicant.conf"
  6. Set static IP adress: sudo ip addr add $IP_ADDRESS dev $INTERFACE

To ensure the system would connect to a static IP upon startup, I created a service to run a shell script.
In the end, the MintBox has become a perfect Linux server for my needs.


