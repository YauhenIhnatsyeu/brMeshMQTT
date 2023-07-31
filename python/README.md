This is Python implementation of the gateway, had to rewrite in Python, as I was unable to figure out how to compose BLE adverisment frame with JS.

Unlike NodeJS implementation, this one talks to BlueZ using DBus.
That means we are not invoking exec() to set the advertisment every time, but it comes with a major downside:

You have to patch and recompile BlueZ.
By default Linux BlueZ would put flags at the end of the Advertising Payload, while iOS and Android would do flags in front of everything else.
Looks like Broadcom's firmware understands it only with flags being in the front, thus we need to modify BlueZ.

Please use **hack-ble-flags.patch** to compile BlueZ from source.

Credit goes to Moody https://github.com/moodyhunter/repo/blob/main/moody/bluez-ble-patched/hack-ble-flags.patch

TODO: 
* Command queueing
  