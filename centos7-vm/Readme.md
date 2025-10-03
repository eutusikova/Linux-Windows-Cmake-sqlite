# Автоматизированное развертывание CentOS 7 с Docker и сборкой SQLite

Этот проект автоматически разворачивает виртуальную машину CentOS 7, устанавливает Docker и собирает SQLite библиотеку в Docker-контейнере.

## Предварительные требования

1. Версия ОС Ubuntu 20.04.6 LTS. Образ для VirtualBox можно установить по ссылке: 
```
https://releases.ubuntu.com/focal/ubuntu-20.04.6-desktop-amd64.iso
```
2. Установленный Vagrant (2.2.6)
3. Установленный VirtualBox (версия 6.1.50_Ubuntur161033)
4. Установленный Ansible (ansible 2.9.6, python version = 3.8.10)

ВАЖНО: Необходимые компоненты можно установить следующей командой: 
```
   sudo apt install virtualbox vagrant ansible -y
```
ИЛИ
```
sudo apt install -y virtualbox=6.1.50-dfsg-1~ubuntu1.20.04.1 vagrant=2.2.6+dfsg-2ubuntu3 ansible=2.9.6+dfsg-1 git=1:2.25.1-1ubuntu3.14
```
## Использование

1. Клонируйте репозиторий и перейдите в директорию проекта:
```
   git clone https://github.com/eutusikova/Linux-Windows-Cmake-sqlite.git cmake-sqlite-project
   cd cmake-sqlite-project/centos7-vm
```
2. Запустите виртуальную машину с автоматической установкой Docker и сборкой SQLite:
```
   vagrant up
```
3. После завершения процесса проверьте результат:
3.1 Зайдите в виртуальную машину:
```
   vagrant ssh
```
3.2. Проверьте, что Docker установлен и работает:
```
   docker --version
   systemctl status docker
```
3.3 Проверьте рабочую директорию на наличие sqlite3.so
```
   ls -l /home/vagrant/sqlite-build
```
