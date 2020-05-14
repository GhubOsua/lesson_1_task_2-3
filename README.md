Домашнее задание 1. Обновить ядро в базовой системе, * и **
## Что сделал
1. Работа выполнялась на основе образа ,который называется  kernel-update;
2. Добавил в Vagrantfile параметр config.vm.synced_folder ".", "/vagrant", type: "virtualbox", чтобы перекидывать файлы с хоста в гостевую ОС. Этот пункт выполняет задание **;
3. Выполнил обновление ОС, чтобы сборка ядра прошло успешно. Выполнил команду sudo yum update, плюс sudo rebbot now;
4. Скачал исходники с сайт  https://www.kernel.org/5.6.12; Перенес исходники ядра на hdd вирт. машины;
5. След. этап это сборка ядра: 
- Выполнил автоматическую сборку ядра командой yes "" | sudo  make oldconfig;
- После приступил к  сборке ядра, командой sudo make install && sudo make modules_install;
6. След. этап обновление конфигурации загрузчика - grub-mkconfig -o /boot/grub/grub.cfg;
7. У меньшил размер образа sudo dd if=/dev/zero of=/EMPTY bs=1M и sudo rm -f /EMPTY;
8. Создал box с помощью vagarnat. vagrant package --base sborkakernel;
9. Создал Vagrantfile. Когда выполнил команду vagrant up, выводилась ошибка ,что нет доступа до ключа privat. Решил созданием файла privatekey на хосте в каталоге vagrant/machines/имявиртулки;

Итого получился образ с ядром 5.6 , с синхронизацией папок с хост машиной 
