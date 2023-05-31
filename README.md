# Cloud_USB
RPI0 2 based Smart Cloud USB Flash Drive with configruable storage 
Required Hardware

    MicroSD Card >= 8GB
    MicroSD Card Adapter/Reader
    Raspberry Pi Zero W 2 (Preferred) 

Required Software :

    Raspberry Pi Imager
    rclone for raspberry pi

## Steps
###1.Download the image.zip folder & extract it .
###2.Use RPI imager to burn the image to SD card with your required username , password & wifi configruations.

###3.connect the sd card to the rpi & connect the rpi to any usb port for configuration or just power it.

###4.using any terminal with SSH , connect & redirect rpi output like this.

: ssh -L localhost:53682:localhost:53682 pi(username)@cloudusb(hostname)
###5.setup & configure rclone like this :
curl https://rclone.org/install.sh | sudo bash
rclone config 

###6. make a new gdrive with rclone.
create new remote with n
look for google drive
skip entering credentials 
choose scope 1
skip(press enter) until reaching if you're working on remote or headless remote & choose no
You will now see, “Please go to the following link” followed by a long URL open this like from the same computer where you're sshing with pi, 
save the new remote & exit
follow the steps from here if you get lost ! : https://www.thedigitalpictureframe.com/how-to-synchronize-your-raspberry-pi-digital-picture-frame-with-google-drive-using-rclone/
###7. using a crontab programe rclone to sync with the configured drive every 2 mintues, make sure you have a folder named " usb_share" in your google drive main folder 
crontab -e
*/2 * * * * rclone sync ./usb_share/upload gdrive:/usb_share
