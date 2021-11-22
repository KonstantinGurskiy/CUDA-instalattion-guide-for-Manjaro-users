# CUDA Install Guide

Installing the required packages for GPU-calculations.

## Скрипт для Manjaro Linux

удалить имеющиеся драйверы nvidia с помощью pacman, используя графический интерфейс

установить новый в shell

```shell
sudo mhwd -i pci video-nvidia-470
```
установить cudnn и CUDA

```shell
sudo pacman -S cudnn cuda
```
в случае поломки с помощью ctrl+alt+F2 зайти в shell и ввести это:


```shell
sudo pacman mirrors -f3
sudo pacman -Syyu
sudo mhwd -r pci video-nvidia
sudo nano /etc/mkinitcpio.conf
```
удалить слово nouveau и, если не помогло, то:


```shell
sudo mkinitcpio -p linux[version]
sudo mhwd -a pci nnfree 0300
sudo mhwd -r pci video-vesa
sudo pacman -R xserver-xorg-video-vesa
sudo pacman -S xserver-xorg-video-vesa
```
проблема заключается в библиотеке video-vesa, однако удалить ее просто так может не получиться
если графическкий интерфейс так и не запуститья - попробуйте снести CUDA



```shell
sudo pacman -R cudnn cuda
sudo reboot
```
