# Ubuntu 18.04

Check whether the dm-integrity and dm-crypt modules are loadable; otherwise, the kernel shall be recomplied the required configuration.

[dm-verity]

```bash
$ sudo grep VERITY /boot/config-$(uname -r)

CONFIG_DM_VERITY=m                   -> "m" implies that it is loadable using `insmod`
# CONFIG_DM_VERITY_FEC is not set
```

[dm-crypt]
sudo grep CRYPT /boot/config-$(uname -r)

```bash
$ sudo grep CRYPT /boot/config-$(uname -r)

CONFIG_ARCH_HAS_MEM_ENCRYPT=y
CONFIG_AMD_MEM_ENCRYPT=y
# CONFIG_AMD_MEM_ENCRYPT_ACTIVE_BY_DEFAULT is not set
CONFIG_LIB80211_CRYPT_WEP=m
CONFIG_LIB80211_CRYPT_CCMP=m
CONFIG_LIB80211_CRYPT_TKIP=m
CONFIG_BLK_DEV_CRYPTOLOOP=m
CONFIG_DM_CRYPT=m                -> "m" implies that it is loadable using `insmod`
CONFIG_RT2X00_LIB_CRYPTO=y
CONFIG_RTLLIB_CRYPTO_CCMP=m
...
```

[dm-integrity]
```bash
$ sudo grep INTEGRITY /boot/config-$(uname -r)

CONFIG_BLK_DEV_INTEGRITY=y
CONFIG_DM_INTEGRITY=m                     -> "m" implies that it is loadable using `insmod`
# CONFIG_BTRFS_FS_CHECK_INTEGRITY is not set
CONFIG_INTEGRITY=y
CONFIG_INTEGRITY_SIGNATURE=y
CONFIG_INTEGRITY_ASYMMETRIC_KEYS=y
CONFIG_INTEGRITY_TRUSTED_KEYRING=y
# CONFIG_INTEGRITY_PLATFORM_KEYRING is not set
CONFIG_INTEGRITY_AUDIT=y
```


