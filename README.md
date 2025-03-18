> echo $GITHUB_USERNAME
matveech99
> cd ${GITHUB_USERNAME}/workspace
> pushd .
~/matveech99/workspace ~
> source scripts/activate
~/matveech99/workspace > 
$ pushd .
pushd — команда, которая добавляет текущую директорию в стек директорий (список, куда можно "запоминать" пути). Это полезно, если вы хотите временно перейти в другую директорию, а потом вернуться обратно.
. — обозначает текущую директорию.
Итог: Команда сохраняет текущую директорию (workspace) в стеке, чтобы позже можно было легко вернуться в неё с помощью команды popd.



















> git clone https://github.com/${GITHUB_USERNAME}/lab02 projects/lab03
Клонирование в «projects/lab03»...
remote: Enumerating objects: 19, done.
remote: Counting objects: 100% (19/19), done.
remote: Compressing objects: 100% (12/12), done.
remote: Total 19 (delta 3), reused 12 (delta 2), pack-reused 0 (from 0)
Получение объектов: 100% (19/19), 5.95 КиБ | 5.95 МиБ/с, готово.
Определение изменений: 100% (3/3), готово.
> cd projects/lab03
> git remote remove origin
> git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
> 
~/m/w/projects/lab03 master >   
Общий смысл этих команд:
    1. Вы клонируете репозиторий lab02 в папку projects/lab03.
    2. Переходите в папку projects/lab03.
    3. Удаляете связь с исходным удаленным репозиторием (lab02).
    4. Добавляете новый удаленный репозиторий (lab03) с именем origin.
Таким образом, вы перенастраиваете локальный репозиторий для работы с новым удаленным репозиторием lab03. Это может быть полезно, если вы хотите использовать код из lab02 как основу для нового проекта lab03.




















> g++ -std=c++11 -I./include -c sources/print.cpp

> ls print.o
print.o
> git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	print.o

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
> nm print.o | grep print
0000000000000000 T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSo
000000000000002a T _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
> ar rvs print.a print.o
ar: создаётся print.a
a - print.o
> git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	print.a
	print.o

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
> file print.a
print.a: current ar archive
> g++ -std=c++11 -I./include -c examples/example1.cpp
cc1plus: fatal error: examples/example1.cpp: Нет такого файла или каталога
compilation terminated.
> g++ -std=c++11 -I./include -c examples/example1.cpp
> git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	example1.o
	examples/example1.cpp
	print.a
	print.o

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
> ls example1.o
example1.o
> g++ example1.o print.a -o example1
> git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	example1
	example1.o
	examples/example1.cpp
	print.a
	print.o

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
> ./example1 && echo

> git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	example1
	example1.o
	examples/example1.cpp
	log.txt
	print.a
	print.o

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
~/m/w/projects/lab03 master ?6 >
Компилируется файл print.cpp в объектный файл print.o.
    1. Проверяется наличие файла print.o.
    2. Ищутся символы, связанные с print, в объектном файле.
    3. Создается статическая библиотека print.a из объектного файла print.o.
    4. Проверяется тип файла print.a.
    5. Компилируется файл example1.cpp в объектный файл example1.o.
    6. Проверяется наличие файла example1.o.
    7. Линкуются объектный файл example1.o и статическая библиотека print.a в исполняемый файл example1.
    8. Запускается программа example1, и если она завершается успешно, выводится пустая строка.















> g++ -std=c++11 -I./include -c examples/example2.cpp
Kоманда компилирует файл examples/example2.cpp в объектный файл example2.o, используя стандарт C++11 и включая заголовочные файлы из директории ./include.
> nm example2.o
Команда выводит список символов (например, функций и переменных), которые содержатся в объектном файле example2.o:
0000000000000000 V DW.ref.__gxx_personality_v0
                 U __gxx_personality_v0
0000000000000000 T main
                 U __stack_chk_fail
                 U _Unwind_Resume
                 U _Z5printRKNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEERSt14basic_ofstreamIcS2_E
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEEC1EPKcSt13_Ios_Openmode
                 U _ZNSt14basic_ofstreamIcSt11char_traitsIcEED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED1Ev
0000000000000000 W _ZNSt15__new_allocatorIcED2Ev
0000000000000000 n _ZNSt15__new_allocatorIcED5Ev
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEEC1EPKcRKS3_
                 U _ZNSt7__cxx1112basic_stringIcSt11char_traitsIcESaIcEED1Ev
                 U _ZSt21ios_base_library_initv
0000000000000000 r _ZStL19piecewise_construct
> g++ example2.o print.a -o example2
Команда линкует объектный файл example2.o и статическую библиотеку print.a в исполняемый файл example2.
> ./example2
Команда запускает программу example2. Предполагается, что программа выполняет какие-то действия, например, записывает данные в файл log.txt.
> cat log.txt && echo
Команда выводит содержимое файла log.txt
hello
~/m/w/projects/lab03 master ?8 > 




















> rm -rf example1.o example2.o print.o
> rm -rf print.a
> rm -rf example1 example2
> rm -rf log.txt
~/m/w/p/lab03 master ?1 >  

Удаляются объектные файлы (example1.o, example2.o, print.o).
Удаляется статическая библиотека (print.a).
Удаляются исполняемые файлы (example1, example2).
Удаляется файл с логами (log.txt).








> cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(print)
EOF
> cat >> CMakeLists.txt <<EOF
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
> cat >> CMakeLists.txt <<EOF
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
> cat >> CMakeLists.txt <<EOF
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
> 
~/m/w/p/lab03 master ?2 >     
















> cmake -H. -B_build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- The C compiler identification is GNU 13.3.0
-- The CXX compiler identification is GNU 13.3.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done (0.3s)
-- Generating done (0.0s)
-- Build files have been written to: /home/matvey/matveech99/workspace/projects/lab03/_build
> cmake --build _build
[ 50%] Building CXX object CMakeFiles/print.dir/sources/print.cpp.o
[100%] Linking CXX static library libprint.a
[100%] Built target print
~/m/w/projects/lab03 master ?2 >                                                  13:06:37

Настройка проекта: cmake -H. -B_build генерирует файлы для сборки в директории _build.
Сборка проекта: cmake --build _build выполняет сборку проекта в директории _build.

> cat >> CMakeLists.txt <<EOF

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF
> cat >> CMakeLists.txt <<EOF

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
~/m/w/projects/lab03 master ?2 >                                                  13:08:25







> cmake --build _build
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/matvey/matveech99/workspace/projects/lab03/_build
[ 33%] Built target print
[ 50%] Building CXX object CMakeFiles/example1.dir/examples/example1.cpp.o
[ 66%] Linking CXX executable example1
[ 66%] Built target example1
[ 83%] Building CXX object CMakeFiles/example2.dir/examples/example2.cpp.o
[100%] Linking CXX executable example2
[100%] Built target example2
> cmake --build _build --target print
[100%] Built target print
> cmake --build _build --target example1
[ 50%] Built target print
[100%] Built target example1
> cmake --build _build --target example2
[ 50%] Built target print
[100%] Built target example2
~/m/w/projects/lab03 master ?2 >   



Сборка всего проекта: cmake --build _build собирает все цели, указанные в CmakeLists.txt.

Сборка конкретных целей:
cmake --build _build --target print собирает цель print.
cmake --build _build --target example1 собирает цель example1.
cmake --build _build --target example2 собирает цель example2.








> ls -la _build/libprint.a
Команда проверяет, существует ли файл libprint.a в директории _build, и выводит его атрибуты (размер, права доступа и т.д.).
-rw-rw-r-- 1 matvey matvey 2246 мар 18 13:06 _build/libprint.a
> _build/example1 && echo
hello
Команда запускает программу example1, и если она завершится успешно, выводит строку hello.
> _build/example2
> cat log.txt && echo
hello
> rm -rf log.txt
Команда удаляет файл log.txt.
~/m/w/projects/lab03 master ?2 >   










> git clone https://github.com/tp-labs/lab03 tmp
Клонирование в «tmp»...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (30/30), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 91 (delta 23), reused 21 (delta 21), pack-reused 61 (from 1)
Получение объектов: 100% (91/91), 1.02 МиБ | 2.29 МиБ/с, готово.
Определение изменений: 100% (41/41), готово.
> mv -f tmp/CMakeLists.txt .
> rm -rf tmp
~/m/w/projects/lab03 master ?2 >                                                  13:26:51

Клонируется репозиторий lab03 в директорию tmp.
Файл CMakeLists.txt из директории tmp перемещается в текущую директорию.
Директория tmp удаляется, так как она больше не нужна.











> cat CmakeLists.txt
Команда выводит содержимое файла CMakeLists.txt на экран.
cmake_minimum_required(VERSION 3.4)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

option(BUILD_EXAMPLES "Build examples" OFF)

project(print)

add_library(print STATIC ${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)

target_include_directories(print PUBLIC
  $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
  $<INSTALL_INTERFACE:include>
)

if(BUILD_EXAMPLES)
  file(GLOB EXAMPLE_SOURCES "${CMAKE_CURRENT_SOURCE_DIR}/examples/*.cpp")
  foreach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
    get_filename_component(EXAMPLE_NAME ${EXAMPLE_SOURCE} NAME_WE)
    add_executable(${EXAMPLE_NAME} ${EXAMPLE_SOURCE})
    target_link_libraries(${EXAMPLE_NAME} print)
    install(TARGETS ${EXAMPLE_NAME}
      RUNTIME DESTINATION bin
    )
  endforeach(EXAMPLE_SOURCE ${EXAMPLE_SOURCES})
endif()

install(TARGETS print
    EXPORT print-config
    ARCHIVE DESTINATION lib
    LIBRARY DESTINATION lib
)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/include/ DESTINATION include)
install(EXPORT print-config DESTINATION cmake)

> cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
Команда настраивает проект для сборки, создает директорию _build и указывает, что установка проекта должна происходить в директорию _install.
CMake Deprecation Warning at CMakeLists.txt:1 (cmake_minimum_required):
  Compatibility with CMake < 3.5 will be removed from a future version of
  CMake.

  Update the VERSION argument <min> value or use a ...<max> suffix to tell
  CMake that the project does not need compatibility with older versions.


-- Configuring done (0.0s)
-- Generating done (0.0s)
-- Build files have been written to: /home/matvey/matveech99/workspace/projects/lab03/_build
> cmake --build _build --target install
Команда устанавливает проект в директорию _install, копируя туда необходимые файлы (например, исполняемые файлы, библиотеки, заголовочные файлы).
[100%] Built target print
Install the project...
-- Install configuration: ""
-- Installing: /home/matvey/matveech99/workspace/projects/lab03/_install/lib/libprint.a
-- Installing: /home/matvey/matveech99/workspace/projects/lab03/_install/include
-- Installing: /home/matvey/matveech99/workspace/projects/lab03/_install/include/print.hpp
-- Installing: /home/matvey/matveech99/workspace/projects/lab03/_install/cmake/print-config.cmake
-- Installing: /home/matvey/matveech99/workspace/projects/lab03/_install/cmake/print-config-noconfig.cmake
> tree _install
Команда выводит структуру директории _install, показывая, какие файлы и директории были установлены.
_install
├── cmake
│   ├── print-config.cmake
│   └── print-config-noconfig.cmake
├── include
│   └── print.hpp
└── lib
    └── libprint.a

4 directories, 4 files
~/m/w/projects/lab03 master ?2 > 

























> git add CmakeLists.txt
Команда добавляет файл CMakeLists.txt в индекс Git. Теперь он готов к коммиту.
> git status
Текущая ветка: master
Изменения, которые будут включены в коммит:
  (используйте «git restore --staged <файл>...», чтобы убрать из индекса)
	новый файл:    CMakeLists.txt

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	examples/example1.cpp

> git commit -m"added CMakeLists.txt"
[master 25b4479] added CMakeLists.txt
 1 file changed, 36 insertions(+)
 create mode 100644 CMakeLists.txt
> git push origin master
Перечисление объектов: 22, готово.
Подсчет объектов: 100% (22/22), готово.
При сжатии изменений используется до 16 потоков
Сжатие объектов: 100% (14/14), готово.
Запись объектов: 100% (22/22), 6.65 КиБ | 6.65 МиБ/с, готово.
Всего 22 (изменений 4), повторно использовано 18 (изменений 3), повторно использовано пакетов 0
remote: Resolving deltas: 100% (4/4), done.
To https://github.com/matveech99/lab03.git
 * [new branch]      master -> master
~/m/w/projects/lab03 master ?1 >
