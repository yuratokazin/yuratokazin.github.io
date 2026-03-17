# OCR из PDF в Debian

  

Для распознавания текста (OCR) из PDF в Debian лучше всего использовать **Tesseract OCR**. Установите его командой `sudo apt install tesseract-ocr tesseract-ocr-rus` (для русского языка), затем преобразуйте PDF в картинки и распознайте текст через терминал.

Вот пошаговая инструкция для вашего файла:

**Установите необходимые инструменты:**

```
sudo apt update
sudo apt install tesseract-ocr tesseract-ocr-rus imagemagick pdftk
```

**Преобразуйте PDF в изображения (Tiff или PNG):**

```
convert -density 300 "/home/oem/Загрузки/Telegram Desktop/instr.pdf" -depth 8 /tmp/page.tiff
```

**Распознайте текст:**

```
tesseract /tmp/page.tiff /home/oem/Загрузки/instr_result -l rus
```

*Результат будет сохранен в файле `instr_result.txt` в папке Загрузки.*

**Альтернативный вариант (GUI):**
Установите **gscan2pdf** или **ocrmypdf** для графического интерфейса:
`sudo apt install ocrmypdf`
Затем запустите: `ocrmypdf -l rus "/home/oem/Загрузки/Telegram Desktop/instr.pdf" /home/oem/Загрузки/instr_final.pdf`. 



Для распознавания текста (OCR) в Debian есть несколько проверенных  инструментов. Выбор зависит от того, предпочитаете ли вы графический  интерфейс или командную строку.



\1. OCRmyPDF (самый мощный инструмент)

Это лучшая утилита для работы с PDF. Она берет PDF-скан и добавляет в него  невидимый текстовый слой, который можно копировать и искать.

**Установка:**

```
sudo apt update
sudo apt install ocrmypdf tesseract-ocr-rus
```

**Использование:**
Перейдите в папку с файлом и запустите обработку (результат сохранится в новый файл):

```
cd "/home/oem/Загрузки/Telegram Desktop"
ocrmypdf -l rus+eng instr.pdf output.pdf
```

*Здесь `-l rus+eng` указывает языки распознавания (русский и английский).*

\2. Tesseract (командная строка)

Если вам нужно просто вытащить текст в текстовый файл (`.txt`), используйте напрямую Tesseract.

**Установка:**

```
sudo apt install tesseract-ocr tesseract-ocr-rus
```

**Использование:**
Tesseract лучше работает с изображениями, поэтому для PDF часто удобнее сначала сконвертировать его или использовать связку с `pdftoppm`:

```
pdftoppm -png instr.pdf page
tesseract page-1.png output -l rus
```

\3. gImageReader (графический интерфейс)

Если вы хотите видеть документ и выделять конкретные области для распознавания мышкой.

**Установка:**

```
sudo apt install gimagereader tesseract-ocr-rus
```

**Использование:**
Найдите программу в меню приложений, откройте ваш файл по пути `/home/oem/Загрузки/Telegram Desktop/instr.pdf` и нажмите кнопку «Распознать всё» или выделите нужную область.

\4. Браузер (быстрый способ без установки)

Если файл открывается в браузере (например, Chrome/Chromium), вы можете использовать встроенные функции:

1. Откройте файл в браузере.
2. Кликните правой кнопкой мыши по странице и выберите **«Поиск через Google Объектив»** (Google Lens).
3. Выберите вкладку «Текст», чтобы скопировать его. 

**Примечание по пути к файлу:** Обратите внимание, что в пути `/home/oem/Загрузки/Telegram Desktop/` есть пробел. При вводе команд в терминале обязательно заключайте такой путь в **кавычки**, иначе система его не распознает.

Какой из вариантов вам удобнее: **графический интерфейс** или **автоматизация** через терминал?



```
convert -density 300 "/home/oem/Загрузки/Telegram Desktop/instr.pdf" -depth 8 /tmp/page.tiff convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/426. convert-im6.q16: no images defined `/tmp/page.tiff' @ error/convert.c/ConvertImageCommand/3229.
```



Эта ошибка возникает из-за политики безопасности 

**ImageMagick**, которая по умолчанию блокирует обработку PDF из-за уязвимостей в Ghostscript.

Чтобы это исправить, нужно разрешить ImageMagick работать с PDF:

Откройте файл конфигурации под **sudo**:

```
sudo nano /etc/ImageMagick-6/policy.xml
```

*(Если у вас версия 7, путь будет `/etc/ImageMagick-7/...`)*.

Найдите в нижней части файла строку:

```
<policy domain="coder" rights="none" pattern="PDF" />
```

Используйте код с осторожностью.

Замените `none` на `read|write`:

```
<policy domain="coder" rights="read|write" pattern="PDF" />
```

Нажмите `Ctrl+O`, затем `Enter` (сохранить) и `Ctrl+X` (выйти).

---

Более современный способ (без правок конфигов)

Если вам нужно просто подготовить файл для OCR, лучше использовать пакет **poppler-utils**, который работает быстрее и не требует правок безопасности:

```
sudo apt install poppler-utils
pdftoppm -tiff -r 300 "/home/oem/Загрузки/Telegram Desktop/instr.pdf" /tmp/page
```

Это создаст файлы `page-1.tif`, `page-2.tif` и т.д. в папке `/tmp`.

Хотите продолжить работу именно через **ImageMagick** или попробуем распознать текст напрямую через **OCRmyPDF**, который сам делает всю конвертацию внутри?



```
oem@lenovo:~$ pdftoppm -tiff -r 300 "/home/oem/Загрузки/Telegram Desktop/instr.pdf" /tmp/page 
oem@lenovo:~$
```



Отлично, `pdftoppm` отработал без ошибок! Теперь в папке `/tmp` лежат готовые изображения вашего документа (они будут называться `/tmp/page-1.tif`, `/tmp/page-2.tif` и так далее).

Теперь осталось запустить само распознавание текста через **Tesseract**.

\1. Установите Tesseract и русский словарь (если еще не сделали)

```
sudo apt update
sudo apt install tesseract-ocr tesseract-ocr-rus
```

\2. Распознайте первую страницу

Попробуйте на одной странице, чтобы проверить результат:

```
tesseract /tmp/page-1.tif /tmp/result -l rus+eng
```

Где

- `/tmp/page-1.tif` — исходная картинка.
- `/tmp/result` — имя выходного файла (Tesseract сам добавит расширение `.txt`).
- `-l rus+eng` — использовать русский и английский языки.

\3. Как посмотреть результат?

Просто выведите текст в терминал:

```
cat /tmp/result.txt
```

------

**Что делать, если в PDF много страниц?**
Если страниц много, можно обработать их все одной командой:

```
for f in /tmp/page-*.tif; do tesseract "$f" "${f%.*}" -l rus+eng; done
cat /tmp/page-*.txt > /tmp/full_text.txt
```

После этого весь текст из документа будет собран в файле `/tmp/full_text.txt`.

**Текст распознался корректно** или в консоли «каша» из символов?



```
oem@lenovo:~$ tesseract /tmp/page-1.tif /tmp/result -l rus+eng Error, cannot read input file /tmp/page-1.tif: No such file or directory Error during processing. oem@lenovo:~$
```



Скорее всего, `pdftoppm` сохранил файлы с расширением **.tif** (одна «f»), а не **.tiff**, либо добавил в название номер страницы с ведущими нулями (например, `page-01.tif`).

Давайте проверим, как именно называются файлы в `/tmp`:

```
ls /tmp/page*
```

Как исправить команду:

**Если файл называется `page-1.tif`:**
Просто уберите одну букву `f` в расширении:

```
tesseract /tmp/page-1.tif /tmp/result -l rus+eng
```

**Если файл называется `page-01.tif`:**

```
tesseract /tmp/page-01.tif /tmp/result -l rus+eng
```

**Универсальный способ (для всех страниц разом):**
Если страниц несколько, выполните эту команду — она сама подхватит все файлы, начинающиеся на `page-` и заканчивающиеся на `.tif`:

```
for f in /tmp/page-*.tif; do tesseract "$f" "${f%.*}" -l rus+eng; done
```

**Что выдала команда `ls /tmp/page\*`?** (Так мы точно поймем правильное имя файла).



```
oem@lenovo:~$ ls /tmp/page* /tmp/page-01.tif  /tmp/page-04.tif  /tmp/page-07.tif  /tmp/page-10.tif /tmp/page-02.tif  /tmp/page-05.tif  /tmp/page-08.tif  /tmp/page-11.tif /tmp/page-03.tif  /tmp/page-06.tif  /tmp/page-09.tif  /tmp/page.tiff oem@lenovo:~$
```



Теперь всё понятно: файлы называются с двузначным номером (например, 

`page-01.tif`). Чтобы распознать **все страницы разом** и собрать их в один текстовый файл, выполните эту цепочку команд:

**Запустите распознавание для всех 11 страниц:**

```
for f in /tmp/page-[0-9][0-9].tif; do tesseract "$f" "${f%.*}" -l rus+eng; done
```

**Склейте все полученные текстовые файлы в один финальный документ:**

```
cat /tmp/page-*.txt > ~/Desktop/instr_full.txt
```

Что в итоге получится?

- В папке `/tmp` появятся файлы `page-01.txt`, `page-02.txt` и т.д.
- На вашем **Рабочем столе** появится файл `instr_full.txt` со всем текстом из документа.

**Попробуйте выполнить первую команду. Появились ли в терминале сообщения о прогрессе распознавания?**



```
oem@lenovo:~$ ls /tmp/page* /tmp/page-01.tif  /tmp/page-04.tif  /tmp/page-07.tif  /tmp/page-10.tif /tmp/page-02.tif  /tmp/page-05.tif  /tmp/page-08.tif  /tmp/page-11.tif /tmp/page-03.tif  /tmp/page-06.tif  /tmp/page-09.tif  /tmp/page.tiff 

oem@lenovo:~$ for f in /tmp/page-[0-9][0-9].tif; do tesseract "$f" "${f%.*}" -l rus+eng; done oem@lenovo:~$ cat /tmp/page-*.txt > ~/Desktop/instr_full.txt bash: /home/oem/Desktop/instr_full.txt: Нет такого файла или каталога oem@lenovo:~$
```



Похоже, в вашей системе папка «Рабочий стол» называется по-русски или просто не создана в домашней директории. В Debian стандартный путь обычно 

**`~/Рабочий стол`**.

Давайте просто сохраним файл в вашу домашнюю папку, так он точно никуда не пропадет:

```
cat /tmp/page-*.txt > ~/instr_full.txt
```

После этого вы сможете найти текстовый результат в своей домашней папке (`/home/oem/instr_full.txt`).

**Как проверить, что всё получилось?**
Просто выведите первые 20 строк файла в терминал:

```
head -n 20 ~/instr_full.txt
```

**Текст в файле читаемый или есть ошибки в распознавании?**


У вас довольно объемный документ (почти 500 страниц!). Чтобы распознать  такой массив данных эффективно, используйте модифицированную команду,  которая учтет трехзначную нумерацию файлов (

`001`, `002` и т.д.).

Выполните эти три шага по очереди:

\1. Запуск распознавания (это займет время)

Команда обработает все файлы `.tif`, созданные `pdftoppm`:

```
for f in /tmp/page-*.tif; do tesseract "$f" "${f%.*}" -l rus+eng; done
```

*Поскольку страниц много, процесс может занять от 5 до 15 минут в зависимости от мощности процессора.*

\2. Сборка всех страниц в один файл

Когда Tesseract закончит работу, объедините все текстовые фрагменты в один документ в вашей домашней папке:

```
cat /tmp/page-*.txt > ~/zaklyuchenie_text.txt
```

\3. Проверка результата

Проверьте, что файл создался и содержит текст:

```
ls -lh ~/zaklyuchenie_text.txt
head -n 50 ~/zaklyuchenie_text.txt
```

**Совет:** Если такие задачи возникают часто, для файлов на сотни страниц в Debian лучше всего использовать **OCRmyPDF**. Он делает всё одной командой и сохраняет PDF с возможностью поиска (текст можно выделять прямо в документе):
`sudo apt install ocrmypdf`
`ocrmypdf -l rus+eng "/home/oem/Загрузки/Заключение эксперта.pdf" ~/itog.pdf`

Вам нужно просто **извлечь текст** или желательно получить **готовый PDF** с текстовым слоем?
