# linux_note

### linux nodejs install 
解決 apt nodejs 版本太舊　
`curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -`
`sudo apt-get install -y nodejs`

### save vim with sudo
`:w !sudo tee %`

### list services
`service --status-all`

雙系統時間校正 https://www.ptt.cc/bbs/Linux/M.1504346730.A.784.html

### vscode settings
prettier
Simple React Snippets
user settings
{
    "editor.formatOnSave": true,
    "editor.tabSize": 4,
    "window.zoomLevel": 1,
    "prettier.tabWidth": 4
}

firefox plugin `NoSquint Plus`

桌面更換 https://askubuntu.com/questions/134/how-do-i-create-a-desktop-wallpaper-slideshow

### linux make win10 usb installer
https://itsfoss.com/bootable-windows-usb-linux/
`sudo umount /dev/sdb1`
`sudo woeusb --target-filesystem NTFS --device ~/Downloads/Win10.iso /dev/sdb`
### ubuntu 指定版本pip
`python3.6 -m pip install`

### git push without username password 
`git config --global credential.helper cache`

### pip error
把 /usr/bin/pip的 (如果python3就改 /usr/bin/pip3)
```
from pip import __main__
if __name__ == '__main__':
    sys.exit(__main__._main())
```

### ubuntu fdisk 指令
http://idobest.pixnet.net/blog/post/22040703-%5B%E8%BD%89%E8%B2%BC%5D-linux%E5%B8%B8%E7%94%A8%E7%9A%84%E7%A3%81%E7%A2%9F%E6%8C%87%E4%BB%A4

### ubuntu disk GUI tool
`sudo gparted`

### ubuntu zip 檔名亂碼
`unzip -O big5 xxx.zip`

### ubuntu text change encoding
`iconv -f big-5 -t utf-8 備忘錄.txt > test`

### let's encrypy tutorial
https://medium.com/@dd0425/lets-encrypt%E5%85%8D%E8%B2%BBssl-tls%E6%86%91%E8%AD%89%E5%AE%89%E8%A3%9D-98059946fabd

### fix mounting disk
`sudo ntfsfix /dev/sdb1`

### error: src refspec "你的遠端branch名稱" does not match any.
`git push origin HEAD:"你的遠端branch名稱" `

### BRYAN IS COOL
