
# portable

On **Windows**, Anki can be installed on a USB / flash drive and run as a portable application. The following example assumes your USB drive is drive G.

Copy the `\Program Files\Anki` folder to the flash drive, so you have a folder like `G:\Anki`.

Create a text file called `G:\anki.bat` with the following text:

`g:\anki\anki.exe -b g:\ankidata`

If you would like to prevent the black command prompt window from remaining open, you can instead use:

`start "anki" /b "D:\program-files\Anki\anki.exe" -b "D:\program-files\Anki\data"`

Double-clicking on anki.bat should start Anki with the user data stored in `G:\anki\data`.

The **full path including drive letter** is required - if you try using \anki\anki.exe instead you will find **syncing** stops working.

Media syncing with AnkiWeb may not work if your flash drive is formatted as ~~FAT32~~. Please format the drive as NTFS to ensure media syncs correctly.


# addons

[Minimize to tray - AnkiWeb](https://ankiweb.net/shared/info/85158043)

- [AnkiConnect - AnkiWeb](https://ankiweb.net/shared/info/2055492159)



# ankiweb
[Are there limits on file sizes on AnkiWeb? / Anki Ecosystem / Knowledge Base - Anki (old site) Support](https://anki.tenderapp.com/kb/anki-ecosystem/are-there-limits-on-file-sizes-on-ankiweb)

> 100MB compressed
> 250MB uncompressed

This includes the text on your cards and the scheduling information, but **does not include sounds/images**, as they are stored separately.

> Most users will never reach the limit. 

25,000 average-sized cards and several years of review history will take up about 25MB, so to hit the limit you usually need to either be copying large amounts of text into each card, or filling your collection with hundreds of thousands of new cards that you aren't actually studying.

At the moment there are no limits on the size of your media, although the size of **individual media files is limited to 100MB**.

As the usage of Anki and AnkiWeb increases, at some point a pricing system may be introduced where basic, low-capacity accounts are free and heavier users can pay more for more space.

If you have hit the collection size limit, you will see messages about the collection being in an inconsistent state when you do a one way upload to AnkiWeb. It is not possible to increase the limit, because such large collections slow down AnkiWeb for other users. If you have imported a dictionary's worth of content, you will need to move some unused cards to a separate deck, export the deck, and then delete the deck from your collection. After doing so, **Tools>Check Database** can be used to free up space that was taken by the deleted cards.



# ~~local server setup~~


ref:

[tsudoko/anki-sync-server](https://github.com/tsudoko/anki-sync-server)

## server side

- install anki

```
sudo apt-get update -y
sudo apt-get install -y anki
```

- install python2.7 and pip for 2

`sudo apt install python2.7 python-pip`

python3 version is tsudoko

- install AnkiServer

`sudo pip install AnkiServer`

- downgrade pip to version 8.1.0

otherwise you will get UndefinedEnvironmentName: 'extra' does not exist in evaluation environment. error

```
pip install pip==8.1.0
pip install -U sentry
```

or

`pip setuptools==20.4`

- config ankiserver

```
mkdir Anki
cd Anki
sudo updatedb
locate example.ini
cp /usr/local/examples/example.ini production.ini
nano production.ini
host=10.XX.XX.XX    #自己服务器的地址也可是局域网IP
allowed_hosts=0.0.0.0  #允许同步的客户端ip地址，使用0.0.0.0表示允许任何ip地址连接
```

- add anki user

`ankiserverctl.py adduser username`

input password after prompt.

- debug for testing

`$ ankiserverctl.py debug [configfile]   # 如果配置文件就在当前目录下，则可以不输入配置文件的路径`

- start or stop service

```
cd anki
ankiserverctl.py start
ankiserverctl.py stop
```

#question:

- 每30秒被启动一次，但很快进程就没有了
- 开机启动在debian9中有变化

add port forwarding

- name: anki
- device: server
- internal port: 27701
- external port: 2770- 

## windows side

- anki > tools > addons > open addons folder
- exit anki
- new file: mysyncserver.py

```
import anki.sync
anki.sync.SYNC_BASE = 'http://192.168.0.100:27701/'
anki.sync.SYNC_MEDIA_BASE = 'http://192.168.0.100:27701/msync/'
```

- start anki
- click sync
- input username and password

## android side

- menu > setting > advanced setting > custom sync server

```
'http://192.168.0.100:27701/'
'http://192.168.0.100:27701/msync/'
```

make sure there isn't https.
