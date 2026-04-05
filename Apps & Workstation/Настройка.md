



### Изменение ключей SSH по умолчанию
Secure Shell или SSH — это сетевой протокол. Он используется для безопасного взаимодействия с компьютерами. SSH дает возможность аутентифицироваться без ввода паролей.

Есть два типа ключей SSH. Один публичный, а другой частный. Необходимо изменить наши публичные SSH-ключи, потому что у всех дистрибутивов они одинаковые, а генерация частных ключей будет гарантировать, что только аутентифицированные пользователи могут получить доступ.
Ключи SSH по умолчанию расположены в каталоге `/etc/ssh`. Мы не будем удалять старые ключи, а просто перенесем в другое безопасное место. Для этого используем команды:

```bash
cd /etc/ssh
```

```bash
sudo mkdir old_keys
```

```bash
sudo mv ssh_host_* old_keys
```
Теперь все наши старые ключи SSH перемещены в каталог с именем `old_keys`.
![[Pasted image 20240412171726.png]]
Теперь создаем новые ключи:
```bash
sudo dpkg-reconfigure openssh-server
```

Команда создаст новые ключи SSH:
![[Pasted image 20240412171825.png]]
Если мы столкнемся с какой-то проблемой, можно будет использовать резервные копии ключей SSH.

---
### Смена языка Kali Linux.
Открываем терминал и пишем
`dpkg-reconfigure locales`
Выбираем ru_RU.UTF8 и нажимаем ОK.
Теперь пишем в терминале `locale-gen` и перезагружаем систему.
Все, теперь система на Русском языке.

---

Flameshot (программа для создания скриншотов)
sudo apt install flameshot

---

man название_программы - узнать информацию об проге

---

<p align="center">
  <img width="200" height="200" src="https://raw.githubusercontent.com/jeffshee/hidamari/resource/hidamari.svg">
</p>

видео обои --> https://github.com/jeffshee/hidamari

---

> [!Note]
postgresql - настройка kali

устанавливать pgadmin4 как написано в инструкции через python pip
p.s. запускать pgadmin4 через виртуальное окружение python
https://www.pgadmin.org/download/pgadmin-4-python/

pgAdmin - PostgreSQL Tools for Windows, Mac, Linux and the Web
а postgresql есть уже в репах kali
по-этому скачиваем через apt

https://www.postgresql.org/download/linux/debian/
https://zalinux.ru/?p=6695
https://devmems.ru/library/article/16

```bash
$ python3 -m venv pgadmin4
$ source pgadmin4/bin/activate
(pgadmin4) $ pip install pgadmin4
...
(pgadmin4) $ pgadmin4
```

---

**Антивирус для Linux – ClamAV**
<p align="center">
  <img width="300" height="300" src="https://raw.githubusercontent.com/Cisco-Talos/clamav/main/logo.png">
</p>
---> https://habr.com/ru/articles/654541/
---> https://github.com/Cisco-Talos/clamav

---
### OBS-Studio убрали из реп Kali Linux
Установка теперь такая:
sudo apt update
Устанавливаем Flatpak: sudo apt install flatpak
Возможно, нужно будет установить репозиторий flathub (есть на странице сайта)
На flathub странице OBS-Studio, выполняем команды для установки

---
### Если сломалась kali-undercover
Thread: Can't get out of kali undercover
https://forums.kali.org/showthread.php?46010-Can-t-get-out-of-kali-undercover&p=106359
sudo apt reinstall kali-undercover
sudo apt reinstall xfce4
Перезагружаемся и выполняем команду: kali-undercover
Радуемся!

---

## Kali с функцией автоматического создания снимков!
Упоминание:
https://www.kali.org/blog/kali-linux-2022-2-release/

Тут можно найти способы установки: 
https://www.kali.org/docs/installation/
там находится --> https://www.kali.org/docs/installation/btrfs/

---

## Goshs — удобный HTTP-сервер на Kali Linux
<p align="center">
  <img width="500" height="200" src="https://raw.githubusercontent.com/patrickhener/image-cdn/refs/heads/main/goshs-banner-light.png">
</p>
---> https://www.kali.org/tools/goshs/
---> https://spy-soft.net/goshs-http-server-kali-linux/
---> https://github.com/patrickhener/goshs

---




---

> [!warning]
> Если вы столкнулись с блокировкой или проблемами с соединением к HackTheBox, то это может вам помочь.
> Если у вас возникают ошибки с `dig`, типа:  
> `dig AXFR inlanefreight.htb @10.129.210.39`,  
> то добавьте параметр `-b`:  
> `dig AXFR inlanefreight.htb @10.129.210.39 -b ip_htb_vpn`.



---

<p align="center">
  <img width="600" height="300" src="https://raw.githubusercontent.com/searxng/searxng/master/client/simple/src/brand/searxng.svg">
</p>
SearXNG — это бесплатная интернет-метапоисковая система, которая агрегирует результаты из различных поисковых сервисов и баз данных. Пользователи не отслеживаются и не профилируются.
---> https://github.com/searxng/searxng

---

<p align="center">
  <img width="600" height="300" src="https://upload.wikimedia.org/wikipedia/commons/9/9a/Visual_Studio_Code_1.35_icon.svg">
</p>
VScode themes:
1. https://github.com/doki-theme/doki-theme-vscode.git
2. https://github.com/silofy/hackthebox.git




---


<p align="center">
  <img width="128" height="128" src="https://flathub.org/_next/image?url=https%3A%2F%2Fdl.flathub.org%2Fmedia%2Fcom%2Fdec05eba%2Fgpu_screen_recorder%2F004169cf6c1e389d03b1a614af74dc9f%2Ficons%2F128x128%2Fcom.dec05eba.gpu_screen_recorder.png&w=128&q=100">
</p>
**GPU Screen Recorder**
Программа для записи экрана, подобная Shadowplay, для Linux. Самая быстрая программа для записи экрана в Linux.

Эта программа для записи экрана оказывает минимальное влияние на производительность системы, записывая изображение с монитора, используя только графический процессор, аналогично Shadowplay в Windows. Это самая быстрая программа для записи экрана в Linux. Работает на X11 и Wayland на платформах AMD, Intel и NVIDIA.

Эту программу можно использовать для записи рабочего стола в автономном режиме, для потоковой трансляции и для мгновенного воспроизведения, как в случае с NVIDIA, где сохраняются только последние несколько минут.
---> https://flathub.org/apps/com.dec05eba.gpu_screen_recorder

---


