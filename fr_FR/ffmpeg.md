## FFMPEG
`ffmpeg -i in.mp4 -vcodec libx264 -f mp4 -preset veryslow -s 480x270 -acodec aac -ab 128k out.mp4`  
libx265 aussi possible  
`ffmpeg -i in.mp4 -ss 30 -c copy -t 10 out.mp4` Créé une copie de 10 secondes à partir de la 30eme seconde

**ff-prompt.bat**  
```sh
@ECHO OFF
REM FF Prompt 1.2
REM Open a command prompt to run ffmpeg/ffplay/ffprobe
REM Copyright (C) 2013-2015  Kyle Schwarz

TITLE FF Prompt

IF NOT EXIST bin\ffmpeg.exe (
  CLS
  ECHO bin\ffmpeg.exe could not be found.
  GOTO:error
)

CD bin || GOTO:error
PROMPT $P$_$G
SET PATH=%CD%;%PATH%
CLS
ffmpeg -version
ECHO.
ECHO For help run: ffmpeg -h
ECHO For formats run: ffmpeg -formats ^| more
ECHO For codecs run: ffmpeg -codecs ^| more
ECHO.
ECHO Current directory is now: "%CD%"
ECHO The bin directory has been added to PATH
ECHO.

CMD /Q /K 
GOTO:EOF

:error
ECHO.
ECHO Press any key to exit.
PAUSE >nul
GOTO:EOF

```
