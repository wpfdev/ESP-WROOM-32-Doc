# ESP-WROOM-32-Doc
This repository will explian how to run your first IoT code using ESP-WROOM-32 microprocessor

# Internet of Things

This is documentation will guide you on how to setup environment for playing around with arduino IDE and using ESP-WROOM-32 microprocessor.

## Prerequisites

- ESP-WROOM-32 8266 microprocessor
- LEDs
- Resisters ( > 3 ohm)
- 3.3V battery (Not Mandatory)
- Normal USB cable
- Little knowledge of making electrical circuts

## Softwares required

- python2.7
- Important python packages: pyserial, esptool
- Arduino IDE: [Download link](https://www.arduino.cc/en/Main/Software) - Depending upon your OS's configure choose 32 or 64 bits version

## Procedure to install Arduino

### For Linux/Ubuntu

- Download the Arduino IDE from [here](https://www.arduino.cc/en/Main/Software) 
- After downloading the tar.xz file from the above link, place it in a director
- Untar the package with `tar -xf arduino-<version-number>.tar.xz` 
- Run `suod ./arduino-<version-number>/install.sh`

### For Windows

- Download the [installer.exe](https://www.arduino.cc/download_handler.php?f=/arduino-1.8.10-windows.exe) or you can go with the [whole_package.zip](https://www.arduino.cc/download_handler.php?f=/arduino-1.8.10-windows.zip) if you don't have admin access
	- For the installer part, just run the installer after download
	- For the zip part, just unzip the file using any tool like winZip or winRAR.

## Procedure to setup Arduino

Now that we have Arduino IDE installed, we need to configure it for ESP-Wroom-32 board.

- Open the arduino IDE
	- For Linux/Ubunutu, I would recommend to open it from termial as root user, `sudo arduino`
	- For Windows
		- For those who installed using installer, just open it from `start`
		- For those who downloaded zip, open the application by clicking the `arduino.exe` from the extracted folder

- Go to `File` Menu > Choose `Preferences`
- Enter `https://dl.espressif.com/dl/package_esp32_index.json` into the “Additional Board Manager URLs” field
- Click on `OK` button
- Then, go to `Tools` > `Board` > `Boards Manager...`
- On the pop-up window, search for **esp32** and then select "**ESP32 by Espressif Systems**"
- Then press `Install`

## First Code 

Now, we have the board and ide is configured. We will now try to connect the board and will try to push our first code.

Connect the board now, using one USB cable.

- Go to `Tools` > `Board` > From the drop-down, choose **ESP32 Dev Module**

- Go to `Tools` menu again and verify if the board looks configured (automatically)
	- Select the `Port` submenu and make sure its not disabled in the drop-down

- Go to `File` > `Examples` > `01.Basics` > Choose `Blink`

This will open a new window with a sample code, which looks like this: 


```code
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000);
  digitalWrite(LED_BUILTIN, LOW); 
  delay(1000);
}
```

Modify this code a little, by adding `int LED_BUILTIN = 2;` right before the `setup()` function.

- Once, you are done, Save this new sketch (sktech is the workbook where you write the code in Arduino IDE)
- Compile the code using `Sketch` menu > `Verify/Compile` Option (or Press `Ctrl + R)`
- Once compiled successfully, upload the code to the board using `Sketch` menu > `Upload` Option (or Press `Ctrl + U`)

Once your code is uploaded successfully, you will be able to see the blue led of the ESP-WROOM-32 starts blinking (that's what the `int LED_BUILTIN = 2` points to)


## Possilbe issues:

### Port is not showing (Ubuntu/Linux)

Reason: `ls -l /dev/tty<port-name>` will show you that other user doesn't have access to write access

Solution:
- Either make the port accessible by other user by adding other users to that port
or 
- Make sure you have ran the ide using root user
- Try reconnecting the board
- Try restarting the ide

### Compiling failed with serial/esptool module import error:

Reason: 
- You might not have installed the python packages 
- You might have installed it using non-default python version
- You might have multiple versions of python, make sure the one with `python -version` have the packages installed

Solution:
- `pip install pySerial esptool`
