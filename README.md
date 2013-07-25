flash_debug_64_ubunutu_13_04
============================

Install Flash Player 11 debug version in Ubuntu 13.04 64 bit


# no 64 bit version of the flash debug player is available, thus we will use the 32 bit version and use nspluginwrapper to make it work
 
sudo killall -9 firefox
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo apt-get install ia32-libs nspluginwrapper libcurl3 libnss3-1d libnspr4-0d
cd ~
wget http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz
mkdir flashplayer_11_plugin_debug.i386
mv flashplayer_11_plugin_debug.i386.tar.gz flashplayer_11_plugin_debug.i386
cd flashplayer_11_plugin_debug.i386
tar zxvf flashplayer_11_plugin_debug.i386.tar.gz
cd ..
sudo cp flashplayer_11_plugin_debug.i386/libflashplayer.so /usr/lib/mozilla/plugins/
sudo chmod +rx /usr/lib/mozilla/plugins/libflashplayer.so
sudo mkdir /usr/lib/nspluginwrapper/plugins
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

 
 

ls /usr/lib/nspluginwrapper/noarch
cat /usr/lib/nspluginwrapper/i386/linux/npviewer

the last line should have ".sh" at the end if you have "npviewer.sh" in "/usr/lib/nspluginwrapper/noarch" folder.
Edit npviewer by adding missing ".sh"

sudo nano /usr/lib/nspluginwrapper/i386/linux/npviewer

This how it looks the last line for me now.

. /usr/lib/nspluginwrapper/noarch/npviewer.sh
