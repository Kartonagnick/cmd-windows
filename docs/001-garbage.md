
![logo](cmd25.png)

garbage.exe
-----------

Сканирует каталоги, и удаляет разный мусор.  
Синтаксис:  

```
garbage.exe --help  вывод в консоль текст с описанием дизайна
```

```
garbage.exe
    "--start: dirs-where-search"    [required]   в каких каталогах нужно удалить мусор
    "--mask: masks-dir-or-files"    [optional]   файловая маска: что хотим удалить
    "--S: dirs-masks-include"       [optional]   файловая маска: в какие подкаталоги заходим
    "--ES: dirs-masks-exclude"      [optional]   файловая маска: в какие подкаталоги не заходим
    "--D: dirs-masks-include"       [optional]   файловая маска: какие каталоги хотим удалить
    "--ED: dirs-masks-exclude"      [optional]   файловая маска: какие каталоги не удал¤ть
    "--F: files-masks-include"      [optional]   файловая маска: какие файлы хотим удалить
    "--EF: files-masks-exclude"     [optional]   файловая маска: какие файлы не удалить
    "--debug"                       [optional]   режим отладки: выводим в консоль детальный лог всех действий
    "--test"                        [optional]   режим тестирования: реального удалени¤ не происходит
```

Пример:
-------

Удаляет временные файлы IDE, 
игнорируя при этом некоторые важные каталоги:  

```
    set "PATH=%~dp0scripts\cmd; %PATH%"

    set m1=build; build-*; product; _products
    set m2=Release; release; release32; release64
    set m3=Debug; debug; debug32; debug64
    set m4=RelWithDebInfo; MinSizeRel
    set m5=.vs; *.suo; *.ncb; *.sdf; ipch; *.VC.db; *.aps;
    set m6=log.txt; cmdlog.txt; debug.txt
    set m7=_cache*.bat; _cache
    set mask=%m1%; %m1%; %m2%; %m3%; %m4%; %m5%; %m6%; %m7%;

    set s1=_*
    set s2=google*; boost*; mingw* 
    set s3=external*; product*; build*; programs; cmake*;
    set scan_exclude=%s1%; %s2%; %s3%

    garbage.exe                ^
        "-start: %~dp0."       ^
        "--mask: %mask%"       ^
        "--es: %scan_exclude%" ^
        "--debug" "--test"
```
