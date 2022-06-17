---
title: 如何刷新DNS缓存
sidebar_position: 1
---

# 如何刷新DNS缓存

## DNS缓存是什么？

DNS 缓存将访问站点的 IP 地址存储在本地计算机上，以便在下次加载时可以加载地更快。 系统不进行长时间的 DNS 查找，而是使用临时 DNS 缓存中的 DNS 记录来回答查询。

DNS 缓存包含所谓的[资源记录](https://en.wikipedia.org/wiki/Domain_Name_System#Resource_records)，他们是：

* **资源数据(或 rdata)**
* **记录类型**
* **记录名字**
* **TTL**
* **Class**
* **资源数据长度**

## 当您可能需要清除缓存时

**你经常会得到一个404的错误。**例如，该网站被转移到另一台服务器，其 IP 地址发生了变化。 要使浏览器从新的 IP 地址打开网站，您需要从 DNS 缓存中删除已经缓存的 IP。

**你想改善你的隐私。**

**你想保护自己免受黑客攻击和电脑病毒的影响。**当 DNS 缓存损坏时，浏览器可能会将您重定向到攻击者插入您计算机的 DNS 记录中的恶意网站的 IP 地址。

## 如何在不同的操作系统上刷新 DNS 缓存

### macOS

To clear the DNS cache on macOS, open the Terminal (you can find it by using the Spotlight search — to do that, press Command+Space and type *Terminal*) and enter the following command:

`sudo killall -HUP mDNSResponder`

On macOS Big Sur 11.2.0 and macOS Monterey 12.0.0, you may also use this command:

`sudo dscacheutil -flushcache`

After that, enter your administrator password to complete the process.

### Windows

To flush DNS cache on your Windows device, do the following:

Load the Command Prompt as an administrator. You can find it in the Start Menu by typing *command prompt* or *cmd*. Then type `ipconfig/flushdns` and press Enter.

You will see the line *Successfully flushed the DNS Resolver Cache*. Done!

### Linux

Linux does not have OS-level DNS caching unless a caching service such as Systemd Resolved, DNSMasq, BIND or Nscd is installed and running. The process of clearing the DNS cache depends on the Linux distribution and the caching service used.

For each distribution you need to start a terminal window. Press Ctrl+Alt+T on your keyboard and use the corresponding command to clear the DNS cache for the service your Linux system is running.

To find out which DNS resolver you're using, command `sudo lsof -i :53 -S`.

#### Systemd Resolved

To clear the **Systemd Resolved** DNS cache, type:

`sudo systemd-resolve --flush-caches`

On success, the command doesn’t return any message.

#### DNSMasq

To clear the **DNSMasq** cache, you need to restart it:

`sudo service dnsmasq restart`

#### Nscd

To clear the **Nscd** cache, you also need to restart the service:

`sudo service nscd restart`

#### BIND

To flush the **BIND** DNS cache, run the command:

`rndc flush`

Then you will need to reload BIND:

`rndc reload`

You will get the message that the server has been successfully reloaded.

### Android

The easiest way to clear your DNS cache on your Android device is to turn the Airplane mode on and off. You can enable/disable the Airplane Mode in the Quick Settings pane.

A hard reboot can also help flush the DNS cache for your device. In order to do that, press and hold the power button for at least 20 seconds. It will (usually) force your device to reboot manually and the DNS cache will be cleared.

Another option is to reset the network settings of your device in the Settings app. Open *Settings > System > Advanced > Reset options > Reset network settings* and tap *Reset Settings* to confirm.

> Note: by doing that, you will lose connections to Wi-Fi routers and other specific network settings, including DNS servers customizations. You will need to reset them manually.

### iOS

There are different ways to clear the DNS cache on your iPad or iPhone.

The simplest way is to activate the Airplane mode (for example, in the Control Center or in the Settings app) and to deactivate it again. The DNS cache will be flushed.

Another option is to reset the network settings of your device in the Settings app. Open *General*, scroll down, find *Reset* and tap on *Reset Network Settings*.

> Note: by doing that, you will lose connections to Wi-Fi routers and other specific network settings, including DNS servers customizations. You will need to reset them manually.