# Basic Installation of Jetson Nano and  SWAP

### Basic Setup
If you want to use Power jack which support 5 V 4 A input. Remember put jumper like image below.
![](https://makerpro.cc/wp-content/uploads/2019/05/4.jpeg)

You need prepare >16 GB Micro SD card in order to install basic enviroment (.ISO).
(https://developer.nvidia.com/embedded/dlc/jetson-nano-dev-kit-sd-card-image) 
After you install the (.ISO) , you need to finish basic setup.
![](https://makerpro.cc/wp-content/uploads/2019/05/6.png)

![](https://makerpro.cc/wp-content/uploads/2019/05/7.png)
![](https://makerpro.cc/wp-content/uploads/2019/05/8.png)
After you finish the basic setup , you need setup swap file(This step will help you to increase computer's virtual memory).
### Setup Swap File
```sudo swapon -show```

You can find that you just have 2.6 GB to use.
![](https://makerpro.cc/wp-content/uploads/2019/05/11.png)

***You can depend your SD card's size set the swap file's size.(For me I set 4 GB)***

```sudo fallocate -| 4G / swapfile```

```sudo chmod 600 /swapfile```

```ls -lh /swapfile```<br>
![](https://makerpro.cc/wp-content/uploads/2019/05/12.png)<br>

***Set SWAP and activate it.***

```sudo mkswap /swapfile```

```sudo swapon /swapfile```

```sudo swapon -show```
![](https://makerpro.cc/wp-content/uploads/2019/05/13.png)<br>

Type ```free -h```  to confirm whether SWAP successful or not.
Because SWAP will disappear when you turn off the power, so please remember add SWAP in fstab.
```sudo cp /etc/fstab/etc/fstab.bak```

```echo'/swapfile none swap sw 00' |sudo tee -a /etc/fstab```

Congratulation now you finish the basic installation of Jetson Nano.
### Reference
https://makerpro.cc/2019/05/the-installation-and-test-of-nvida-jetson-nano/
https://github.com/JetsonHacksNano/installSwapfile
https://forums.developer.nvidia.com/t/creating-a-swap-file/65385
