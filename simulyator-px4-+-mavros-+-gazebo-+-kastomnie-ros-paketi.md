## Симулятор px4 + mavros + gazebo + кастомные ROS пакеты

1. Настройка и установка тулчейна ROS Melodic + необходимые библиотеки для компиляции прошивки: https://dev.px4.io/v1.8.2/en/setup/dev\_env\_linux.html\#gazebo-with-ros
2. Установка библиотек для gstreamer v1.0:
   https://github.com/PX4/Firmware/issues/13117\#issuecomment-539400429

3. Для того, чтобы файлы симулятора стали видны для ROS, нужно добавить в .bashrc:  
   source ~/cloned/coex\_firmware/Tools/setup\_gazebo.bash /home/goldarte/cloned/coex\_firmware /home/goldarte/cloned/coex\_firmware/build/posix\_sitl\_default  
   export ROS\_PACKAGE\_PATH=$ROS\_PACKAGE\_PATH:/home/goldarte/cloned/coex\_firmware  
   export ROS\_PACKAGE\_PATH=$ROS\_PACKAGE\_PATH:/home/goldarte/cloned/coex\_firmware/Tools/sitl\_gazebo



