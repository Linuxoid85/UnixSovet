# Пару слов про SerenityOS

SerenityOS — любительская опреационная система семейства UNIX, разрабатываемая с 2018 года. Она предназначена для архитектуры x86, имеет своё собственное ядро и графический интерфейс «а-ля Windows 9x». Она написана с нуля на языке С++. Согласно [GitHub](https://github.com/SerenityOS/serenity/graphs/contributors), с 2018 по 2024 год в разработке SerenityOS так или иначе участвуют(участвовали) больше тысячи человек.

Этой статьёй я хотел бы начать обзор всевозможных «экзотических» ОС, разрабатываемых энтузиастами. Интересно не только рассказать про саму ОС, но и про какие-то её особенности, а также примерно понять, для какой аудитории подойдёт эта система, а также примерно угадать, что ждёт её в будущем.

![](pic/preview.png)

<small>Скриншот взят с <a href="https://serenityos.org/">сайта</a> проекта.</small>

Как запустить эту ОС, готова ли она для повседневного использования и в чём её смысл? — добро пожаловать под кат.

<!--

ЧТО ОЖИДАЕТСЯ В СТАТЬЕ:

- Сборка ОС
- запуск в QEMU
- беглый обзор графического интерфейса
- изучаем файловую систему
- пытаемся запустить хоть что-то
- мысли по поводу предназначения этой ОС, её аудитории и проч. проч. проч.

-->

## Полезные ссылки

Перед прочтением статьи можете посетить ряд сайтов для более точного понимания, что же такое эта ваша SerenityOS:

- [Сайт проекта](https://serenityos.org/);
- [GitHub репозиторий](https://github.com/SerenityOS/serenity);
- [FaQ](https://serenityos.org/faq/);

## Получение ОС

Для начинающего пользователя получить эту ОС станет не так уж просто, ведь её загрузочных образов просто нет. Придётся собирать её из исходников самостоятельно, благо процесс сборки достаточно прост. <small>Далее я буду приводить инструкции по сборке, взятые из <a href="https://github.com/SerenityOS/serenity/blob/master/Documentation/BuildInstructions.md">документации этой ОС</a>. Я пользуюсь дистрибутивом Archlinux, поэтому инструкции будут даны относительно него. В принципе, если вы используете другой дистрибутив Linux, то все различия будут заключаться только лишь в установке необходимых зависимостей для сборки ОС.</small>

Для начала склонируйте репозиторий с ОС и перейдите в директорию с исходниками:

```bash
git clone https://github.com/SerenityOS/serenity
cd serenity
```

Теперь же требуется установить необходимое ПО для компиляции системы:

```bash
sudo pacman -S --needed      \
  base-devel cmake curl      \
  mpfr libmpc gmp e2fsprogs  \
  ninja qemu-desktop         \
  qemu-system-aarch64 ccache \
  rsync unzip
```

<small>Даже не знаю, зачем тут <tt>qemu-system-aarch64</tt>, ведь SerenityOS предназначена для x86_64. Может быть, в документации этой ОС ошибка? Хотя ARM-архитектуры дас ищ гут, но мы пока остановились на x86.</small>

## Сборка ОС

Для сборки введите команду:

```bash
Meta/serenity.sh run
```

Этой командой вы начнёте сборку ОС, по завершении которой будет создан ряд файлов в директории `Build/x86_64/Root` и запущена виртуальная машина QEMU с собранной SerenityOS.

![](pic/build_serenity.png) | ![](pic/build_serenity2.png)

## Особенности ОС

Среди интересных особенностей этой ОС можно отметить то, что как таковой фиксации версий не существует. Нет такого понятия как «SerenityOS 1.0» или «SerenityOS 1.1 Alpha». Мы просто клонируем `master`-ветку из git-репозитория и собираем ОС из исходников. Кроме того, как я написал уже ранее, уже собранных образов или дистрибутивов этой ОС также не предоставляется — ожидается, что пользователь соберёт систему самостоятельно.

Несмотря на то, что ОС написана на С++, это не совсем тот С++, который мы все знаем: авторы называют этот язык «Serenity C++». В нём остутствуют исключения и имеется своя стандартная библиотека.

Для SerenityOS был разработан собственный фреймворк для создания графических интерфейсов ПО LibGUI с собственным набором виджетов. Да и вообще вся SerenityOS больше является «вещью в себе»: своё ядро, своя стандартная библиотека С++, свой GUI... Даже свой браузер есть со своим движком LibWeb, который, кстати, не так давно отпочковался от SerenityOS и стал самостоятельным проектом, способным работать в том числе в Linux.

---

## Поддержать меня

Если вам понравилась эта статья, то вы можете отправить мне донат:

> **2202 2062 5233 5406** (Сбербанк; Михаил Сергеевич К.)

На данный момент мне требуется новый ноутбук, на котором я смогу продолжить писать статьи, поэтому каждый донат приблизит дату его приобретения на какой-то небольшой срок. Заранее спасибо!