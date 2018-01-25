#### Сборка

1. Вначале скопировать rpg-svo, vo-guard и rpg-vikit из [https://github.com/CopterExpress](https://github.com/CopterExpress)
2. Затем установить и скомпилировать Sophus и fast \(в корневую директорию, , действовать по инструкции [https://github.com/uzh-rpg/rpg\_svo/wiki](https://github.com/uzh-rpg/rpg_svo/wiki)

3. Для сборки Sophus требуется gcc-5 и g++-5, т.к. svo собирается только с определённым коммитом, и он требует именно эти версии компилятора, а на образе установлен gcc-6 и g++-6. Для downgrade нужно выполнить  
   `sudo apt-get remove gcc g++      
    sudo apt-get install gcc-5 g++-5      
    sudo ln -s /usr/bin/gcc-5 /usr/bin/gcc      
    sudo ln -s /usr/bin/g++-5 /usr/bin/g++`

4. После сборки нужно выполнить catkin\_make из директории catkin\_ws_. _Если возникает ошибка с компиляторами C и СXX, нужно указать в файле CMakeCache.txt пути до компилятора

#### Запуск рабочей версии от Ильи

1. Перед запуском нужно добавить два файла: svo\_ros.launch в директорию ~/catkin\_ws/src/rpg\_svo/svo\_ros/launch\_ и px4\_blacklist.yaml в /opt/ros/kinetic/share/mavros/launch \(файлы желательно запушить на наш гитхаб\)
2. roslaunch svo\_ros svo\_ros.launch



