

---

Flameshot (программа для создания скриншотов)
sudo apt install flameshot



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

## Goshs — удобный HTTP-сервер на Kali Linux
<p align="center">
  <img width="500" height="200" src="https://raw.githubusercontent.com/patrickhener/image-cdn/refs/heads/main/goshs-banner-light.png">
</p>
---> https://www.kali.org/tools/goshs/
---> https://spy-soft.net/goshs-http-server-kali-linux/
---> https://github.com/patrickhener/goshs



<p align="center">
  <img width="600" height="300" src="https://upload.wikimedia.org/wikipedia/commons/9/9a/Visual_Studio_Code_1.35_icon.svg">
</p>
VScode themes:
2. https://github.com/silofy/hackthebox.git



<p align="center">
  <img width="128" height="128" src="https://flathub.org/_next/image?url=https%3A%2F%2Fdl.flathub.org%2Fmedia%2Fcom%2Fdec05eba%2Fgpu_screen_recorder%2F004169cf6c1e389d03b1a614af74dc9f%2Ficons%2F128x128%2Fcom.dec05eba.gpu_screen_recorder.png&w=128&q=100">
</p>
**GPU Screen Recorder**
Программа для записи экрана, подобная Shadowplay, для Linux. Самая быстрая программа для записи экрана в Linux.

Эта программа для записи экрана оказывает минимальное влияние на производительность системы, записывая изображение с монитора, используя только графический процессор, аналогично Shadowplay в Windows. Это самая быстрая программа для записи экрана в Linux. Работает на X11 и Wayland на платформах AMD, Intel и NVIDIA.

Эту программу можно использовать для записи рабочего стола в автономном режиме, для потоковой трансляции и для мгновенного воспроизведения, как в случае с NVIDIA, где сохраняются только последние несколько минут.
---> https://flathub.org/apps/com.dec05eba.gpu_screen_recorder

---


