<p align="center">
  <img width="1000" height="250" src="https://www.danieltufvesson.com/images/header_makeresolvedeb.png">
</p>

**DaVinci Resolve:**  

1. DaVinci Resolve in a Box  
https://www.youtube.com/watch?v=Oo0QyPBAlAQ  
канал: [Akzel](https://www.youtube.com/@PMK94)  
---> https://github.com/zelikos/davincibox

2. MakeResolveDeb  
---> https://www.danieltufvesson.com/makeresolvedeb

---

**🛠️ Памятка: Решение вылетов Fusion в DaVinci Resolve на Linux**  
⚠️ СИМПТОМЫ:   
Краш (Signal 6 / SIGABRT) при нажатии на ПРОБЕЛ (поиск нод), клавишу DELETE или при вводе текста в поиск EFFECTS.  

🛑 ПРИЧИНА:  
Встроенная во Fusion библиотека Qt5 ломается, если в системе Linux физически не сгенерирована американская локаль (en_US.UTF-8), даже если сам интерфейс программы включен на английском.  

🛠️ БЫСТРОЕ РЕШЕНИЕ:  
1. Сгенерировать локаль в терминале:  
    ```bash
    sudo dpkg-reconfigure locales 
    ``` 
   • В ПЕРВОМ окне: найдите в списке "en_US.UTF-8 UTF-8", отметьте ПРОБЕЛОМ, чтобы появилась звездочка [*], и нажмите ОК.   
   • ВО ВТОРОМ окне: выберите свой основной язык системы "ru_RU.UTF-8" и нажмите ОК.  
3. Если не помогло, запускать DaVinci принудительно с флагом локали через терминал:  
   `LC_ALL=en_US.UTF-8 /opt/resolve/bin/resolve`  
4. Для встроенной графики (если начнет тормозить):  
   Ограничить память в Preferences -> System -> Memory (Выделить под Resolve не более 7-8 ГБ, под Fusion Cache не более 2.5 ГБ, так как VRAM берется из общей оперативной памяти).  

---

Этот скрипт использует ffmpeg для преобразования файлов форматов MKV и MP4 в MOV для программы видеомонтажа DaVinci Resolve  
```bash
sudo apt-get update
sudo apt-get install ffmpeg
```
From MKV to MOV:
```bash
ffmpeg -i input.mkv -map 0:0 -map 0:1 -map 0:2? -vcodec dnxhd -acodec:0 pcm_s16le -acodec:1 pcm_s16le -s 1920x1080 -r 30000/1001 -b:v 36M -pix_fmt yuv422p -f mov output.mov
```
From MP4 to MOV:
```bash
ffmpeg -i input-video.mp4 -c:v dnxhd -profile:v dnxhr_hq -pix_fmt yuv422p -c:a pcm_s16le output-video.mov
```

From MOV to MP4:
```bash
ffmpeg -i input.mov -qscale 0 output.mp4
```
---> https://gist.github.com/gsilano/939c696e4fd72b177d8b21ef183c1c83  
---> https://stackoverflow.com/questions/12026381/ffmpeg-converting-mov-files-to-mp4

---


### 📹 OBS Studio
<p align="center">
  <img width="500" height="300" src="https://obsproject.com/assets/images/features-new/hero_32_1_1.png">
</p>

Бесплатное программное обеспечение с открытым исходным кодом для записи видео и прямых трансляций.  
Скачайте программу и начните вести трансляции быстро и легко — на Windows, Mac или Linux.  
---> https://obsproject.com/  
---> https://pkg.kali.org/pkg/obs-studio  

**Сжатие картинки до 16:9 без обрезки**  
Этот способ сделает ролик ровно 16:9 для YouTube, и на нем поместится весь ваш экран 16:10 целиком, но изображение будет едва заметно сжато по вертикали.
1. Перейдите в Настройки -> Видео.
2. В строке Разрешение предпросмотра (холст) вручную сотрите текст и впишите 1920x1080 (или 2560x1440, если монитор 2К).
3. В строке Разрешение выхода выберите то же самое (1920x1080). Нажмите «Применить» и «ОК».
4. Теперь на главном экране OBS кликните правой кнопкой мыши по вашему источнику.
5. Выберите Трансформировать -> Растянуть до границ (или нажмите комбинацию клавиш Ctrl + S).

---

### 🎙️ Audacity
<p align="center">
  <img width="500" height="300" src="https://www.audacityteam.org/_astro/hero-surface-studio-darkened.Bg6vZ4zE_Z1E7Af.webp">
</p>

Самое популярное в мире приложение для записи и редактирования аудио.  
---> https://www.audacityteam.org/  
---> https://pkg.kali.org/pkg/audacity  

---

### #1
Создай скрипт и назови его как тебе удобно, например, `w1.sh`
```bash
INPUT=$1
OUTPUT=${INPUT%%.*}.dnxhd.mov

CODEC='dnxhd'
SIZE='1920:1080'
FPS='60000/1001' # 59.94
FORMAT='yuv422p' # 4:2:2
BITRATE='220M'
AUDIO_CODEC='pcm_s16le' # 16-bit audio

ffmpeg -i "${INPUT}" -c:v $CODEC -vf "scale=${SCALE},fps=${FPS},format=${FORMAT}" -b:v $BITRATE -c:a $AUDIO_CODEC "${OUTPUT}"
```
Запуск `./w1.sh файл.mkv`

### #2
Создай скрипт и назови его как тебе удобно, например, `w2.sh`
```bash
CODEC='dnxhd'
SIZE='1920:1080'
FPS='60000/1001' # 59.94
FORMAT='yuv422p' # 4:2:2
BITRATE='220M'
AUDIO_CODEC='pcm_s16le' # 16-bit audio

FFMPEG_OVERWRITE="" # '-y' or empty

EXTENSION_FILTER='mkv mk3d mp4 m4v mov qt asf wmv mxf m2p ps ts tsy m2ts mts vob evo 3gp 3g2 f4v flv ogv ogx webm rmvb divx'
FILES_LIST=''
SPACE_CHAR='%20'

echo "Autoencoder in DNxHD codec."
echo -e "\nEncode parameters:"
echo " - codec = $CODEC"
echo " - size = $SIZE"
echo " - fps = $FPS"
echo " - format = $FORMAT"
echo " - bitrate = $BITRATE"
echo " - audio codec = $AUDIO_CODEC"

echo -e "\nExclude files:"
for var in "$@"
do
  flag1=0
  flag2=0
  if [ "$var" == "${var%%.*}.dnxhd.mov" ]; then
    flag1=1
    echo " X $var # .dnxhd.mov in blacklist"
  else
    for item in $EXTENSION_FILTER
    do
      if [ "${var##*.}" == "$item" ]; then
        flag2=1
      fi
    done
  fi
  if ! [ $flag2 == 1 ] && [ $flag1 == 0 ]; then
    echo " X $var # unknown .${var##*.}"
  else
    if [ $flag1 == 0 ]; then
      FILES_LIST+=" ${var// /$SPACE_CHAR}"
    fi
  fi
done

echo -e "\nInclude files:"
for var in $FILES_LIST
do
  echo " - ${var//$SPACE_CHAR/ }"
done

echo -e "\nStart encoding..."
for var in $FILES_LIST
do
  INPUT=${var//$SPACE_CHAR/ }
  OUTPUT=${INPUT%%.*}.dnxhd.mov
  ffmpeg $FFMPEG_OVERWRITE -i "${INPUT}" -c:v $CODEC -vf "scale=${SCALE},fps=${FPS},format=${FORMAT}" -b:v $BITRATE -c:a $AUDIO_CODEC "${OUTPUT}"
done
```
Запуск `./w1.sh файл*`
