```
git clone --depth 1 https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
curl -L https://github.com/leohearts/kmod-iwlwifi-disablelar/raw/refs/heads/master/patch > patch
patch -p1 -i ./patch
make defconfig-iwlwifi-public
sed -i 's/CPTCFG_IWLMVM_VENDOR_CMDS=y/# CPTCFG_IWLMVM_VENDOR_CMDS is not set/' .config
make -j4

sudo make install

reboot
```
