Warning: Experimental, causes problems

Doesn't work on AX210 with `Conflict between TLV & NVM regarding enabling LAR (TLV = enabled NVM =disabled)`
(This is also the reason why lar_disable got removed in 5.4)

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
