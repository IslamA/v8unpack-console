
# v8Unpack, GCC edition
Добавлен проект CodeBlocks 13.12.
Для сборки требуется Boost.

## Fork of v8Unpack project by Denis Demidov (disa_da2@mail.ru)

[Original project HOME](https://www.assembla.com/spaces/V8Unpack/team)

[Original project svn repo](http://svn2.assembla.com/svn/V8Unpack/)

## Note

V8Unpack - a small console program  for rebuild/build configuration files [1C](http://1c.ru) such as *.cf *.epf *.erf

#####Функционал V8Unpack
<ol>
<li>Утилита работает только с файлами CF и EPF</li>
<li>Основное назначение утилиты - распаковать файл в файловую структуру и собрать его обратно из этой файловой структуры</li>
<li>Структура папок - как в исходном файле</li>
<li>Детализация распаковки задается дополнительными ключами</li>
<ol type="1">
<li>Простое отображение без распаковки модулей</li>
<li>Отображение с распаковкой упакованных модулей</li>
<li>Расширенная распаковка с преобразованием распакованных модулей в файловую систему в максимальной детализации (например, будет файл с именем Кнопка, а внутри параметры этой кнопки), как свойства данного элемента.</li>
</ol>
</ol> 
#####Командная строка

-UNP[ACK]     in_filename.cf     out_dirname
-P[ACK]       in_dirname         out_filename.cf
-UND[EFLATE]  in_filename.data   out_filename
-D[EFLATE]    in_filename        filename.data
-EX[AMPLE]
-BAT
-PARSE        in_filename.cf     out_dirname      --PARSELEVEL={0|1|2}
-BUILD        in_dirname         out_filename.cf

## Plaform 

Windows, POSIX

## Environment

Project for [codelite IDE](http://www.codelite.org/)  
Project for [Codeblocks IDE](http://codeblocks.org/)

## Build

Артефакты/релизы можно скачать с [build-server проекта](https://build.batanov.me/job/v8unpack-win/)

[Прямая ссылка на последнюю успешную сборку win32](https://build.batanov.me/view/e8-script/job/v8unpack-win/label=mingw32/lastSuccessfulBuild/artifact/bin/Release/*zip*/v8unpack.zip)

[Прямая ссылка на последнюю успешную сборку win64](https://build.batanov.me/view/e8-script/job/v8unpack-win/label=mingw64/lastSuccessfulBuild/artifact/bin/Release/*zip*/v8unpack.zip)

### Ubuntu/Debian

```
git clone https://github.com/xDrivenDevelopment/v8unpack-console.git
sudo apt-get install gcc make libboost-all-dev
cd v8unpack-console 
make
```
## Version 2.0

- Версия 2.0 переписана "с нуля" и дополнена новой парой ключей PARSE-BUILD

- Внимание, изменились значения ключей, так что сначала нужно запустить программу без ключей.
- В частности, 'P' - теперь parse, а не pack
- Можно разбирать конфигурацию в файловую систему одним ключом PARSE (он представляет собой UNPACK+UNDEFLATE в "одном флаконе")

## Version 3.0

- Оптимизирована сборка .cf файла ключ -B[UILD]. В версии 2.0 сборка корневого контейнера происходила в оперативной памяти.
При сборке больших конфигураций это могло приводить к ошибке "segmentation fault". В версии 3.0 сборка корневого контейнера происходит 
динамически с сохранением элементов контейнера непосредственно в файл по мере их создания.
