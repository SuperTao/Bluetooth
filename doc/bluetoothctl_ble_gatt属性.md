https://blog.csdn.net/zhuo_lee_new/article/details/106626680

使用bluetoothctl连接一个ble设备，并读取其中的属性。
```
[bluetooth]# power on		# 上电
[bluetooth]# scan on		# 扫描设备，需要先扫描到设备才能进行连接
Discovery started
[CHG] Controller DC:A6:32:17:14:4B Discovering: yes
[CHG] Device 49:70:4C:66:5D:70 RSSI: -89
[CHG] Device 49:70:4C:66:5D:70 TxPower: 12
[CHG] Device A4:C1:38:AA:9A:1C RSSI: -23
[CHG] Device 65:5E:A1:B6:8F:BE RSSI: -79
[CHG] Device 65:5E:A1:B6:8F:BE TxPower: 12
[CHG] Device CC:D5:17:02:17:D6 RSSI: -95
[CHG] Device 61:01:BA:10:BE:E7 RSSI: -97
[CHG] Device 42:1E:D6:D8:0B:9D RSSI: -57
[CHG] Device 42:1E:D6:D8:0B:9D TxPower: 8
[CHG] Device 52:4B:B0:95:8B:28 RSSI: -83
[CHG] Device 52:4B:B0:95:8B:28 TxPower: 12
[CHG] Device 7A:46:3F:37:95:1D RSSI: -74
[CHG] Device 7A:46:3F:37:95:1D TxPower: 12
[CHG] Device 58:49:DE:ED:E2:1D RSSI: -85
[CHG] Device 74:63:AC:33:EE:47 RSSI: -70
[CHG] Device 74:63:AC:33:EE:47 TxPower: 26
[CHG] Device 65:B0:6E:A2:F3:32 RSSI: -94
[CHG] Device 65:B0:6E:A2:F3:32 TxPower: 12
[CHG] Device 4B:FE:0B:DF:55:B0 RSSI: -95
[CHG] Device 4B:FE:0B:DF:55:B0 TxPower: 6
[CHG] Device 41:F3:B8:96:4E:D4 RSSI: -98
[CHG] Device 41:F3:B8:96:4E:D4 TxPower: 12
[CHG] Device F4:60:E2:9F:99:61 RSSI: -51
[CHG] Device 58:49:DE:ED:E2:1D RSSI: -96
[NEW] Device 7A:DF:E4:48:CA:E7 7A-DF-E4-48-CA-E7
[bluetooth]# scan off		# 停止扫描

[bluetooth]# connect A4:C1:38:AA:9A:1C				# 连接设备
Attempting to connect to A4:C1:38:AA:9A:1C
[CHG] Device A4:C1:38:AA:9A:1C Connected: yes
Connection successful
[NEW] Primary Service
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0008
        00001801-0000-1000-8000-00805f9b34fb
        Generic Attribute Profile
[NEW] Characteristic
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0008/char0009
        00002a05-0000-1000-8000-00805f9b34fb
        Service Changed
[NEW] Descriptor
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0008/char0009/desc000b

		
		[NEW] Characteristic
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065
        00000102-0065-6c62-2e74-6f696d2e696d
        Vendor specific
[NEW] Descriptor
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065/desc0067
        00002901-0000-1000-8000-00805f9b34fb
        Characteristic User Description
[NEW] Descriptor
        /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065/desc0068
        00002902-0000-1000-8000-00805f9b34fb
        Client Characteristic Configuration

[LYWSD03MMC]# menu gatt					 	# 进入gatt子菜单

[LYWSD03MMC]# list-attributes				# 列出所有的属性

[LYWSD03MMC]# select-attribute /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065/desc0068	# 选择其中一个属性

[LYWSD03MMC:/service0060/char0065/desc0068]# attribute-info				# 属性信息
Descriptor - Client Characteristic Configuration
        UUID: 00002902-0000-1000-8000-00805f9b34fb
        Characteristic: /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065
[LYWSD03MMC:/service0060/char0065/desc0068]# read						# 读取属性的内容
Attempting to read /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065/desc0068
[CHG] Attribute /org/bluez/hci0/dev_A4_C1_38_AA_9A_1C/service0060/char0065/desc0068 Value:
  00 00                                            ..
  00 00                                            ..
```