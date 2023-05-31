# Cloud_USB
RPI0 2 based Smart Cloud USB Flash Drive with configruable storage 
Required Hardware

    MicroSD Card >= 8GB
    MicroSD Card Adapter/Reader
    Raspberry Pi Zero W 2 (Preferred) 
    Raspberry Pi Camera (Optional)
Required Software :
Raspberry Pi Imager
## Steps
1.Download the image.zip folder & extract it 
2.Use RPI imager to burn the image to SD card with your required username , password & wifi configruations 
3.connect the sd card to the rpi & connect the rpi to any usb port for configuration or just power it
4.using any terminal with SSH , connect & redirect rpi output like this 
: ssh -L localhost:53682:localhost:53682 pi(username)@cloudusb(hostname)
5.setup & configure rclone like this :
curl https://rclone.org/install.sh | sudo bash
rclone config 

6. make a new gdrive with rclone
7. using a crontab programme rclone to sync with the configured drive every 2 mintues 
crontab -e
*/2 * * * * rclone sync ./usb_share/upload gdrive:/usb_share
