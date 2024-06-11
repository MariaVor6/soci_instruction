# soci_instruction
Инструкция по установке и настройке библиотеки SOCI
1. Вызываем командную строку(cmd) в выбранной нами директории, допустим: C:\Users\Сервис\source\repos.Выделяем путь(Ctrl+A) и пишем cmd.
2. Далее прописываем клонированную ссылку 
```shell
git clone https://github.com/SOCI/soci.git
```
3. Далее прописываем dir.
   Например: C:\Users\Сервис\source\repos>dir\
> Команда dir отображает в широком формате алфавитный список соответствующих имен файлов в каждом каталоге и приостанавливается при каждом заполнении экрана, пока не нажимаете клавишу, чтобы продолжить.
4. Переходим в создавшуюся директорию с именем soci (имя нашей установленной библиотеки). Для пехода используем команду cd.
Выглядит это так:
> C:\Users\Сервис\source\repos>cd soci

5. В нашей папке soci создаём директорию(папку) с именем build. Для этого используем команду  mkdir build.
Выглядит это следующим образом:
> C:\Users\Сервис\source\repos\soci>mkdir build
6. Далее уже по изветсной нам команде переходим в папку build.
> C:\Users\Сервис\source\repos\soci>cd build
7. Далее прописывааем команду cmake .. . Это позволит нам собрать исходный код. Если CMake не установлен, его надо установить.
> CMake — кроcсплатформенная утилита для автоматической сборки программы из исходного кода. Установить можно здесь: <https://cmake.org/>

Важно! После слова(команды) идёт пробел и две точки. Выглядит это так: 
> C:\Users\Сервис\source\repos\soci\build>cmake ..
8. После загрузки есть вероятность что у вас возникнет подобная проблема:
> None of the supported Oracle versions (21;20;19;18;12;11;10) could be found, consider updating ORACLE_VERSIONS if the version you use is not among them.
-- WARNING: Oracle libraries not found, some features will be disabled.
-- PostgreSQL:
-- WARNING: PostgreSQL libraries not found, some features will be disabled.
-- SQLite3:
-- SQLite3 not found (SQLITE3_INCLUDE_DIR=SQLITE3_INCLUDE_DIR-NOTFOUND, SQLITE3_LIBRARY=SQLITE3_LIBRARY-NOTFOUND.
-- WARNING: SQLite3 libraries not found, some features will be disabled.
Библиотеки ни одной из БД(Базы данных) не найдены и доступа к их функциям нет. В моём случае меня интересует конкретно БД Postgresql.
Для решения проблемы я прописала следующую команду:
> cmake -G "Visual Studio 17" -DWITH_BOOST=OFF -DCMAKE_BUILD_TYPE=RELEASE -DSOCI_CXX11=ON -DCMAKE_VERBOSE_MAKEFILE=ON -DWITH_DB2=OFF -DWITH_FIREBIRD=OFF -DWITH_MYSQL=OFF -DWITH_ODBC=OFF -DWITH_ORACLE=OFF -DWITH_POSTGRESQL=ON -DPOSTGRESQL_INCLUDE_DIR=C:\Program Files\PostgreSQL\15\include -DPOSTGRESQL_LIBRARY=C:\Program Files\PostgreSQL\15\lib\libpq.lib -DWITH_SQLITE3=OFF C:\Users\Сервис\source\repos\soci
Здесь мы прописываем путь к include и lib, причём при указании lib выписываем путь к конкретной библиотеке libpq.lib. 

