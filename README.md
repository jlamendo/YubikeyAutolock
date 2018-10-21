# YubikeyAutolock
A small task scheduler script to lock your windows computer when you unplug a Yubikey. 

You'll need to add in the SID for your user account into `YubikeyAutoLock.xml`, under Task->Principals->Principal@Author->UserId.

You can find your SID by running the following in PowerShell:
```
wmic useraccount get name,sid
```

Made for my specific environment, you may need to tune some parameters. 

Check event viewer, and take a look at the Applications and Services Log -> Microsoft -> Windows -> SmartCard-DeviceEnum log.

Plug in your yubikey, unplug it, and take a look at any events created with ID 102. 

If you are using a Yubikey model other than the Yubikey 4, you'll need to edit the string 'SWD\ScDeviceEnum\1_Yubico_Yubikey_4_OTP+U2F+CCID_0' to match the InstancePath for your particular model.

This will lock your machine whenever a Yubikey is unplugged, not a particular one, as it's just for locking and not for anything else, so messing with verifying serial numbers and such is just unnecessary.


After you've made the proper modifications, load up task scheduler, hit import, and select the `YubikeyAutoLock.xml` file.
