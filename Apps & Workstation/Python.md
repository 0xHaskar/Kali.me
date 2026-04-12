<p align="center">
  <img width="600" height="300" src="https://habrastorage.org/getpro/habr/upload_files/6b4/64a/c27/6b464ac275204276853de85acff33009.gif">
</p>
**Быстрый старт в мир Python окружений с uv:**
[uv](https://github.com/astral-sh/uv) — довольно быстрый пакетный менеджер и менеджер виртуальных окружений для Python, написанный на Rust. По заявлению разработчиков, uv способен заменить такие Python инструменты, как pip, pip-tools, pipx, poetry, pyenv, twine, virtualenv и другие.

Установки пакета из pypi.org:
```bash
uv tool install xsstrike     # Установка пакета xsstrike
uv tool list                 # Показать список установленных пакетов
uv tool uninstall xsstrike   # Удаление пакета xsstrike
```

Установка пакета из github:
```bash
uv tool install 'git+https://github.com/xaitax/SploitScan'  # Установка пакета из репозитория
uv tool list                 # Показать список установленных пакетов 
uv tool uninstall sploitscan # Удаление пакета SploitScan
```

Установка пакета с помощью venv:
```bash
git clone https://github.com/xaitax/SploitScan 
cd SploitScan                       # Переход в папку проекта
python3 -m venv SploitScan          # Создание виртуального окружения
source SploitScan/bin/activate      # Активация виртуального окружения
uv pip install -r requirements.txt  # Установка всех зависимостей
deactivate                          # Выход из виртуального окружения
```
---> https://habr.com/ru/articles/875840/
---> https://github.com/astral-sh/uv

**Установка приложений Python с помощью pipx:**
```bash
pipx install xsstrike    # Установка пакета (он должен быть на pypi.org)
pipx list                # Показать список установленных пакетов
pipx uninstall xsstrike  # Удалить пакет
```
---> https://www.kali.org/docs/general-use/python3-external-packages/

**Установка через виртуальное окружение (venv):**
```bash
$ python3 -m venv xsstrike          # Создание виртуального окружения
$ source xsstrike/bin/activate      # Активация виртуального окружения
(xsstrike) $ pip install xsstrike   # Установка пакета xsstrike
(xsstrike) $ xsstrike               # Запуск скрипта
(xsstrike) $ deactivate             # Выход из виртуального окружения
```

В этом окружении вы можете устанавливать библиотеки и запускать проекты на Python, используя установленные библиотеки, что обеспечивает изоляцию и предотвращает конфликты между проектами.
