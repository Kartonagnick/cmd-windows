
![logo](cmd25.png)

find_in.exe
-----------

Поиск файлов или каталогов.  
Синтаксис:  

```
garbage.exe --help  вывод в консоль текст с описанием дизайна
```

```
find_in 
    "--start: dirs-where-search"    [required] список путей, где нужно искать
    "--mask: masks-dir-or-files"    [optional] файловая маска: какие нужно искать файлы или каталоги 
    "--S: dirs-masks-include"       [optional] файловая маска: в какие подкаталоги заходим
    "--ES: dirs-masks-exclude"      [optional] файловая маска: в какие подкаталоги не заходим
    "--D: dirs-masks-include"       [optional] файловая маска: в какие каталоги ищем
    "--ED: dirs-masks-exclude"      [optional] файловая маска: в какие каталоги не ищем
    "--F: files-masks-include"      [optional] файловая маска: в какие файлы ищем
    "--EF: files-masks-exclude"     [optional] файловая маска: в какие файлы не ищем
    "--once"                        [optional] флаг: нужно ли прекратить поиск после обнаружения первой цели
    "--dirnames"                    [optional] флаг: интересует не файл, а каталог, где он был обнаружен.
    "--exe32"                       [optional] флаг: интересуют только 32 битные приложения
    "--exe64"                       [optional] флаг: интересуют только 64 битные приложения
    "--debug"                       [optional] флаг: выводить подробный лог о ходе работы
```

Пример:
-------

Выполняем поиск программы 7z.exe,
которая может быть расположена в различных каталогах:  

```
    set dirs=                          ^
        ePATH_ROOT\programs\x64\7-Zip; ^
        C:\Program Files\7-Zip;        ^
        ePATH_ROOT\programs\x86\7-Zip; ^
        C:\Program Files (x86)\7-Zip;  ^
        D:\long\workspace\programs\x64\7-Zip

    for /f "usebackq tokens=* delims=" %%a in (
        `find_in.exe "--start:%dirs%" "--S:7-Zip*" "--F:7z.exe" "--once" "--dirnames"`
    ) do (
        set "ePATH_7Z=%%a"
    )
```
