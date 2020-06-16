# Merge multiple audio files and video files into single MP4 file 

Make sure all audio and video files are in same folder, Open Command Prompt in that folder and follow below steps.

1. Create text file with all audio files names into 'myAudioList.txt', make sure to open the text file and check if all files are in currect order
```sh
(for %i in (*.aac) do @echo file '%i') > myAudioList.txt
```
2. Create text file with all video files names into 'myVideoList.txt', make sure to open the text file and check if all files are in currect order
```sh
(for %i in (*.ts) do @echo file '%i') > myVideoList.txt
```
3. If all files are having same codec you would see no problem in merging or else you may face issues and these step will not work for you.

4. Download ffmpeg open source executable from official website
```sh
https://ffmpeg.org/download.html
```
5. Extract zip file and copy executable 'ffmpeg.exe' to the same folder having all your audio, video files.

6. Merge all audio files into single audio file
```sh
ffmpeg -f concat -safe 0 -i myAudioList.txt -c copy output.aac
```
7. Merge all video files into single video file
```sh
ffmpeg -f concat -safe 0 -i myVideoList.txt -c copy output.ts
```
8. Merge video file and audio file into single mp4 file
```sh
ffmpeg -i output.ts -i output.aac -map 0:V:0 -map 1:a:0 -c copy -f mp4 -movflags +faststart output.mp4
```

Helpful Web Links:

https://trac.ffmpeg.org/wiki/Concatenate

https://trac.ffmpeg.org/wiki
