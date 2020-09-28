# VNC tutorial

Generally speaking, we will connect the NVIDIA Jetson Nano to the screen, keyboard, and mouse for operation. Of course, there is no problem. But if we don’t have a screen, keyboard, etc., or we want to go out. It is not convenient to connect the screen, keyboard, and mouse to operate. At this time, remote login is required.

* We use Jetson Nano as the server, and our Windows laptop as the client (Linux is also available).

* The server and client must be connected to the same network!!!


# Installation process

First, install VINO VNC
```
$ sudo apt-get install vino
```
Second, Enable desktop sharing permissions for "dconf-editor"
```
$ sudo apt-get install dconf-editor
```
Open dconf-editor
```
$ dconf-editor
```

Go into /org/gnome/desktop/remote-access", and turn off "require-encryption"

Fourth, edit "org.gnome.Vino.gschema.xml" to fill in the missing enable option. Please drag to the bottom and fill in the following code before the last </schema>

```
    <key name='enabled' type='b'>
      <summary>Enable remote access to the desktop</summary>
      <description>
        If true, allows remote access to the desktop via the RFB
        protocol. Users on remote machines may then connect to the
        desktop using a VNC viewer.
      </description>
      <default>false</default>
    </key>
```
After filling the missing parts, please remember to save it.

# Run

Open VNC server in Jetson Nano
```
/usr/lib/vino/vino-server
```

Also, we have to download VNC viewer in our laptop. Here is the download link:
 https://www.realvnc.com/en/connect/download/viewer/
 
 After downloading it, please fill in the network IP and press enter.
 
# Just connect Jetson nano to the power supply, and wait for a minute, and then turn on the VNC viewer from our client laptop and enter the IP to remotely control it!