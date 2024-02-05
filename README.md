# cloud-init-ros2
Unattended install of the ros2 enviroment

Wanted to automate a rebuild of the ros enviroment...

From the Raspberry Pi imager, selected the device, selected a Ubuntu server 64 bit install, customized the image with my preferences.

once complete, updated the boot drive [[network-config]](https://github.com/MatthewCKelly/cloud-init-ros2/blob/main/network-config) to enable the wired connection.

Then updated [[user-data]](https://github.com/MatthewCKelly/cloud-init-ros2/blob/main/user-data) - see linked files.

to confirm that the config has the correct syntax, check with the following command.
```sudo cloud-init schema --config-file /mnt/path/to/user-data```

For the apt ros source ```PGP PUBLIC KEY BLOCK``` to add to the [[userdata]](https://github.com/MatthewCKelly/cloud-init-ros2/blob/main/user-data) used the following steps...  Note: the gpg key **F42ED6FBAB17C654** is displayed when imported...
```
curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key | gpg --import
gpg: key F42ED6FBAB17C654: "Open Robotics <info@osrfoundation.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

gpg --export  --armor F42ED6FBAB17C654 > cloudinit-ROS-pgp-key.asc
cat cloudinit-ROS-pgp-key.asc
```
