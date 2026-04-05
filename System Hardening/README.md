<p align="center">
  <img width="300" height="300" src="https://www.kali.org/tools/kali-tweaks/images/kali-tweaks-logo.svg">
</p>

**Kali Tweaks**  
Инструмент для настройки расширенных параметров конфигурации Kali Linux.
Этот пакет предоставляет возможности для оптимизации работы Kali Linux.

Это включает в себя следующие аспекты:
- Настройка оболочки
- Настройка зеркал APT
- Установка и удаление метапакетов Kali Linux
- Усиление безопасности системы
- Дополнительная настройка для виртуализированных сред
- Настройки ядра

---> https://www.kali.org/tools/kali-tweaks/  
---> https://www.kali.org/docs/general-use/metapackages/

```bash
sudo apt install kali-tweaks
```

---

Пароли по умолчанию в Kali Linux, прочитать: 
> https://www.kali.org/docs/introduction/default-credentials/

---

<p align="center">
  <img width="600" height="600" src="https://codeby.net/attachments/lgotype-jpg.67861/">
</p>

Безопасный пингвин. Усиливаем защиту Kali Linux  
https://codeby.net/threads/bezopasnyi-pingvin-usilivayem-zashchitu-kali-linux.81668/

---

Список всех TCP и UDP сокетов, которые находятся в состоянии ожидания входящих соединений:
```bash
sudo ss -tulwn | grep LISTEN
```
- `-t`: Показать только TCP-сокеты.
- `-u`: Показать только UDP-сокеты.
- `-l`: Показать только прослушивающие сокеты.
- `-n`: Не разрешать имена сервисов и отображать адреса и порты в числовом формате.

Команда покажет все процессы, которые используют порт:
```bash
sudo lsof -i :тут_порт
```

Список всех активных и неактивных служб в системе:
```bash
systemctl list-units --type service
```
