# BluetoothPrinting
Learn how to build Android Apps that connect to printer via bluetooth and can print text and receipt (Android)

## Getting Started

These app connect to printer via blutooth, so you need to enable bluetooth permission  

These app send bulk SMS using GSM Modem (tested using Wavecom and Syscom MP8P) 
in this project there is 3 main Component:
- MainActivity (The Main Interface)
- P25Connector (The main connector that connect the app with device via bluetooth)
- Pockdata (The package that contains functional class, data, helper, and constants to translate data from byte, hexa, UTF8 to readable string)

### Code

this app built using P25Connector lib to connect app with Printer using bluetooth and 
BroadcastReceiver to distribute the command, the connection step include:
- enable bluetooth
- connect to P25Connector
- send a command
- disconnect from connector

bluetooth permission in manifest

```
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
```

The Connection need to send the printer serial number and pair it with phone using bluetooth sensor. every printer has different serial number, 
so don't use the example serial number

when executing the command, the code send intent with filter

```
IntentFilter filter = new IntentFilter();
     filter.addAction(BluetoothAdapter.ACTION_STATE_CHANGED);
     filter.addAction(BluetoothDevice.ACTION_FOUND);
     filter.addAction(BluetoothAdapter.ACTION_DISCOVERY_STARTED);
     filter.addAction(BluetoothAdapter.ACTION_DISCOVERY_FINISHED);
     filter.addAction(BluetoothDevice.ACTION_BOND_STATE_CHANGED);
registerReceiver(mReceiver, filter);
```

## The Printer

you can use any bluetooth printer that support P25 to connect the device via bluetooth socket
in this repository, the code example can print:
- ASCII Character, Alphabet, and Numeric
- Barcode

## Built With

* Android Studio v 2.9
* Operating System - Ubuntu
* Bluetooth Printer

## Authors

* **Marchellin Antonia**

## Screenshoot
no screenshoot yet

