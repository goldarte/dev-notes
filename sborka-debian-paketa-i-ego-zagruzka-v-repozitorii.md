## Сборка debian пакета из ROS ноды и его загрузка в репозиторий

Опорная статья: [How to make a debian from a ROS package](https://gist.github.com/awesomebytes/196eab972a94dd8fcdd69adfe3bd1152)  
Статья Лёши Рогачевского: [Сборка ROS-пакетов в deb-пакеты \(на примере OpenCV3\)](https://github.com/sfalexrog/coex_kb/blob/master/kb001_building_ros_packages_as_deb.md)

### Сборка debian пакета из ROS ноды.

Проще всего собирать на той же платформе, для которой предполагается пакет \(для остального - есть docker и chroot, об этом в статье у Лёши\). Например, если пакет будет устанавливаться на raspbian, то в ней его и собирать. Следующие шаги выполняются именно для raspbian.

Что нужно для сборки?

1. Скачать и установить инструментарий:
   ```
   sudo apt-get install python-bloom fakeroot debhelper dpkg-dev
   ```
2. Перейти в папку с исходником ROS ноды \(обычно ~/catkin\_ws/src/&lt;название ноды&gt;\)
3. Подготовить ROS ноду к сборке \(в папке с исходником должна появиться папка debian\)
   ```
   bloom-generate rosdebian --os-name debian --os-version stretch --ros-distro kinetic
   ```
4. Обновить все зависимости
   ```
   source /opt/ros/indigo/setup.bash
   ```
5. Собрать пакет
   ```
   fakeroot debian/rules binary
   ```

В итоге в корне исходника должно появиться два файла .deb

Оба файла следует загрузить в репозиторий.

### Загрузка debian пакетов в репозиторий

Чтобы загрузить пакет в репозиторий в соответствии с соглашениями, которые используются при построении linux репозиториев, следует воспользоваться утилитой [aptly](https://www.aptly.info/). Предполагается, что aptly уже установлена и настроена. Для загрузки пакета следует выполнить следующие шаги:

1. Войти в терминал репозитория
2. Загрузить собранные debian пакеты в папку, которую просматривает aptly
3. Запустить aptly в docker контейнере:
   ```
   sudo docker exec -it aptly /bin/bash
   ```
4. Добавить загруженные пакеты в репозиторий \(для репозитория coex подробности в [гисте](https://gist.github.com/urpylka/f75167cc82dd9d774ba15e2ed4fce069) урпылки\):
   ```
   aptly repo add rpi-ros-kinetic /opt/aptly/ros-kinetic/
   aptly publish update stretch rpi-ros-kinetic
   ```









