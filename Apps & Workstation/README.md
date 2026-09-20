# 🎬 Apps & Workstation

Полезный софт для повседневной работы, записи контента и создания рабочего окружения в Kali Linux.

### 📸 Мультимедиа и Скриншоты
* **Flameshot** — мощная и удобная утилита для создания скриншотов с возможностью быстрого редактирования и добавления стрелок/текста на лету.
  ```bash
  sudo apt install flameshot
  ```
  ---> https://flameshot.org/  
  ---> https://pkg.kali.org/pkg/flameshot

* **GPU Screen Recorder** — сверхбыстрая программа для записи экрана с минимальной нагрузкой на систему. Работает через графический процессор (аналог NVIDIA Shadowplay в Windows). Поддерживает X11/Wayland и видеокарты AMD, Intel, NVIDIA.  
---> https://flathub.org/en/apps/com.dec05eba.gpu_screen_recorder  
---> https://git.dec05eba.com/gpu-screen-recorder/about/

### 🗄 Базы данных (Development)
* **PostgreSQL & pgAdmin 4** — связка СУБД для локальной разработки.
  ```bash
  $ python3 -m venv pgadmin4
  $ source pgadmin4/bin/activate
  (pgadmin4) $ pip install pgadmin4
  ...
  (pgadmin4) $ pgadmin4
  ```
  ---> https://www.postgresql.org/download/linux/debian/  
  ---> https://www.pgadmin.org/download/pgadmin-4-python/  
  ---> https://zalinux.ru/?p=6695  
  ---> https://devmems.ru/library/postgresql-parol-po-umolchaniyu-polzovatelya-postgres  

### 🌐 Сетевые инструменты
* **Goshs** — продвинутый и удобный HTTP/HTTPS сервер на Go, заменяющий стандартный `python3 -m http.server`.  
---> https://www.kali.org/tools/goshs/  
---> https://github.com/goshs-labs/goshs
