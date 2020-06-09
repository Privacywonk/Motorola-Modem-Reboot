# Motorola-Modem-Reboot
This script provides metadata about a Motorola MB8600 modem which can be useful for integration other systems, such as home automation and monitoring.  It returns a JSON object in stdout.  Additionally, it can reboot the modem with the appropriate argument passed.

### Credit
Based on https://github.com/aclytle/Motorola-Modem-Reboot.  Many thanks for the powerful tool you created.

The original script automatically rebooted the modem, which may be dangerous in some scenarios.  A parameter was added to specifically request the reboot.  This implementation can also provide basic information about the modem if the reboot command is not provided.  Furthermore, the host, username, and password for the modem can all be specified from the command line if not using the default values.

### Prerequisite Requirements
* Python3
* Requests

To install `Requests` in Ubuntu Linux:
```
sudo apt-get install python-requests
```

To install `Requests` in MacOS:
```
python3 -m pip install requests
```

### Usage
```
usage: modem_reboot.py [-h] [--host HOST] [--username USERNAME]
                       [--password PASSWORD] [--reboot]

optional arguments:
  -h, --help           show this help message and exit
  --host HOST          Hostname or IP of your modem (Default: 192.168.100.1)
  --username USERNAME  Admin username (Default: admin)
  --password PASSWORD  Admin password (Default: motorola)
  --reboot             Reboots the modem
  ```

### Example Request to Retrieve Data
`~$ python3 modem_reboot.py --username myAdminUsername --password myPassword`

### Example Pretty Print Response (Success)
```
{
    "requestStatus": "SUCCESS",
    "data": {
        "softwareVersion": "8600-18.2.12",
        "macAddress": "00:40:36:4E:B6:1F",
        "serialNumber": "0408-MB8600-3252",
        "operatorSoftwareVersion": "Prod_18.2_a4",
        "wanStatus": "Connected",
        "systemUptime": "0 days 06h:47m:26s",
        "networkAccess": "Allowed"
    }
}
```

### Example Pretty Print Response (Failure)
```
{
    "requestStatus": "ERROR",
    "message": "Login failed."
}
```