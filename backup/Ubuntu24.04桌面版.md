# [開啟文件夾共享]([url](https://post.smzdm.com/p/azor2m55/)）
`sudo apt install samba smbclient`
`sudo ufw allow samba`
`sudo apt install nautilus-share`
`sudo usermod -aG sambashare $(whoami)`
reboot
`sudo smbpasswd -a ubuntula`