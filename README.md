# Running Raspberry Pi in Kiosk Mode

This tutorial will guide you on how to configure a Raspberry Pi to boot directly into a web page or application without a desktop environment.

## Requirements
- Raspberry Pi 4 with the latest OS installed

## Steps

1. **Create an Autostart Directory:** If it doesn't already exist, create the autostart directory:

    ```bash
    mkdir -p ~/.config/lxsession/LXDE-pi
    ```

2. **Create an Autostart File:** Create an autostart file (e.g., autostart) in the `~/.config/lxsession/LXDE-pi/` directory:

    ```bash
    nano ~/.config/lxsession/LXDE-pi/autostart
    ```

3. **Add Startup Programs:** Add the programs you want to start automatically to this file. For example, to start a Node.js server, you can add a line like this:

    ```bash
    @/usr/bin/firefox <your-application-url>
    ```

    Replace `<your-application-url>` with the URL of your web application.

    **Save and Exit:** Save the file by pressing `Ctrl + X`, then `Y`, and finally `Enter`.

4. **Configuring Crontab:** Starting your server on boot

   - Create a bash script named `start-app.sh` and include the following code:

         
         #!/bin/bash
      
         export DISPLAY=:1
         cd /root/Desktop/nodeserver && node index.js
         

   - Open crontab:

         
         sudo nano /etc/crontab

     Include your start script here
     ![image](https://github.com/vinayakaraju46/lxsession/assets/30818966/84076550-c71a-45db-826e-464e3cc93b19)

         

5. **Reboot:** Reboot your Raspberry Pi to apply the changes:

    ```bash
    sudo reboot
    ```

Your Raspberry Pi should now start with your application open in the Firefox browser.

![image](https://github.com/vinayakaraju46/lxsession/assets/30818966/e769daaa-93d0-42a4-8fa1-3f11f93c20ef)

