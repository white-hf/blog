layout: page
title: "How I installed a USB Wi-Fi adapter on Linux"
permalink: /diary

How I installed a USB wifi adapter on Linux

git clone https://github.com/gglluukk/rtl8188eus.git
sudo make && sudo make install

https://www.lulian.cn/download/60-cn.html

sudo apt install network-manager


sudo systemctl enable wifi-connect.service
sudo systemctl start wifi-connect.service
