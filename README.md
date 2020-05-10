# zad_kernel
Домашнее задание 1. Обновить ядро в базовой системе, * и **
## Что сделал
1. Взял виртулку из kernel-update за основу. Чтоб не качать образ, подумал так проще будет
2. CentsOs стояла старенькая, пришлось обновить sudo yum update
3. Скачал https://www.kernel.org/	5.6.12
4.  make oldconfig make && make modules и sudo make install && sudo make modules_install
5. grub-mkconfig -o /boot/grub/grub.cfg
6. У меньшил размер образа sudo dd if=/dev/zero of=/EMPTY bs=1M и sudo rm -f /EMPTY
7. Создал box vagrant package --base sborkakernel
8. Создал Vagrantfile . Пришлось тут создать файл privatekey на хосте в каталоге vagrant/machines/имявиртулки
9. Для общих папок добавил в vagrantfile строку config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
