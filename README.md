# zkteco-sdk-php

ZKLibrary is PHP Library for ZK Time & Attendance Devices. This library is design to reading and writing data to attendance device (fingerprint, face recognition or RFID) using UDP protocol. This library is useful to comunicate between web server and attendance device directly without any addition program. This library is implemented in the form of class. So that you can create an object and use it functions.

Web server must be connected to the attendance device via Local Area Network (LAN). The UDP port that is used in this communication is 4370. You can not change this port without changing firmware of the attendance device. So, you just use it.

The format of the data are: binary, string, and number. The length of the parameter and return value must be vary.
# Example
```
<?php

 include("zklib/zklib.php");

$zk = new ZKLibrary('192.168.1.102', 4370);
$zk->connect();
$zk->disableDevice();

// $zk->setTime(date('Y-m-d H:i:s'));
$zk->testVoice();

$zk->enableDevice();
$zk->disconnect();

?>
```
#Data Structrure
```
Class ZKLibrary {
    String ip;
    Unsigned Short port;
    Unsigned Long socket;
    Unigned Long session_id;
    String received_data;
    String user_data[][];
    String attendance_data[][];
    Unsigned Long timeout_sec;
    Unsigned Long timeout_usec;
}
```
# Function
```
__construct($ip, $port)
####Parameters
$ip

IP address of device.

$port

UDP port of device.

disconnect()
Function to disconnect from the device.

getUser()
Get  of users.

getAttendance()
Get  attendance log.

The role of user. The length of $role is 1 byte. Possible value of $role are:

0 = LEVEL_USER
2 = LEVEL_ENROLLER
12 = LEVEL_MANAGER
14 = LEVEL_SUPERMANAGER

```
