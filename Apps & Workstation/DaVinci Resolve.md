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
