# LUCI-APP-SER2NET

These patches which come from OpenWrt forum are used to add ser2net service for OpenWrt LuCI. I do some collection work and make the source file to patch format in order to make it easier to use.

## Introduction
**openwrt-packages-add-luci-app-ser2net-support.patch** --> This patch is the init scripts of ser2net. 
**openwrt-luci-add-luci-app-ser2net-support.patch** --> This patch adds service interface in LuCI.

## How To
1. For people who uses OpenWrt first need checkout the OpenWrt source first.

		mkdir openwrt
		cd openwrt
		svn co svn://svn.openwrt.org/openwrt/trunk trunk
		cd trunk

2. Use feeds script update the packages.

		./scripts/feeds update -a
		./scripts/feeds install -a

3. Download the two patches and patch them.
		
		cd ..    		#go back to openwrt directory
		git clone https://github.com/JiapengLi/luci-app-ser2net.git
		cd trunk/feeds/packages/
		patch -p1 < ../../../luci-app-ser2net/openwrt-packages-add-luci-app-ser2net-support.patch
		cd ../../../    #go back to openwrt directory
		cd trunk/feeds/luci/
		patch -p1 < ../../../luci-app-ser2net/openwrt-luci-add-luci-app-ser2net-support.patch

4. To use luci-app-ser2net, you need choose it in `LuCI -> 3. Application -> luci-app-ser2net`

		cd ../../      #go back to openwrt/trunk directory
		make menuconfig

5. After choose right platform, device, package, driver and all needed things. Run make to compile Openwrt. After compiling, firmware will position in `trunk/bin/xxxx` folder, `xxxx` is the platform name.
	
		make
 
6. Install the openwrt firmware, then you can find the Ser2net in Service tag with instruction there.

7. Enjoy it.

## Resources
The patch is based on this post from OpenWrt forum.  
<https://forum.openwrt.org/viewtopic.php?id=34662>  

## Thanks
Thanks **carlberg** who make the source file and **g1itch** who shows the package create procedure. Both of them are from OpenWrt forum.