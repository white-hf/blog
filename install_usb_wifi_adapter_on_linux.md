This article records how I installed a USB wifi adapter on a MintBox running Linux.
I bought a used MintBox as a Linux server for development, unfortunately, it can only access the internet via network cable, 
because the preview owner lost antennas, I bought a USB wifi adapter on Temu for $10. 
Always sure, that cheap things are not cheap, I could not compile the driver code because it was for the old kernel.

Here are the steps to finally make it work. 
- I find a substitute driver code on GitHub, [here](http://https://github.com/gglluukk/rtl8188eus "here"). It works perfectly.
- Configure the wifi. The following Linux commands helped me.
  1. Check the network devices: "ifconfig -a"
  2. Enable the wireless network card: "ifconfig yours up"
  3. Scan for available wireless networks: "iwlist yours scan"
  4. Generate configure file for wpa_supplicant: "sudo wpa_passphrase yours >> /etc/wpa_supplicant.conf"
  5. Connect to a wireless network: "wpa_supplicant -B -i yours -c /etc/wpa_supplicant.conf"


sudo systemctl enable wifi-connect.service sudo systemctl start wifi-connect.service
