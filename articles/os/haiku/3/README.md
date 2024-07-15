# Пару слов про Haiku. Часть 3 — Первый запуск ОС

![](pic/desktop.png)

Что-ж, во [второй](../2/) части мы установили Haiku на нетбук Samsung NF210, сейчас же пришло время рассмотреть эту ОС подробнее.

## Первый запуск

![](pic/desktop1.png)

Система, установленная на старый HDD, работает вполне отзывчиво (достаточно шустро она работала и с загрузочного USB). К слову, если вы запишите iso-образ Haiku на флешку, то получите не ограниченную Live-систему (как в случае с Linux), а вполне пригодную к работе ОС. Это реальная система, в которой сохраняются все ваши изменения и настройки, чего нельзя сказать про «живые» образы Linux, где вся система содержится в squashfs-образе, недоступном для записи.

Система загружается достаточно быстро — на моём компьютере меньше минуты. Во время загрузки не отображаются текстовые сообщения ядра и системы инициализации, нет рваных переходов между загрузочной анимацией и графическим интерфейсом (когда во время этого перехода показывается текстовая консоль TTY). Сразу видно, что в отличие от Linux и BSD, в Haiku графический интерфейс и остальные системные компоненты не примотаны друг к другу на скотч, а идеально подогданы друг под друга, всё тесно взаимосвязано и интегрировано. Поскольку система создана для одного пользователя, то не отображается меню входа в систему, которое в Linux я всегда отключаю, устанавливая автоматический вход от имени одного единственного пользователя, которого я создал во время установки ОС.

Лично я считаю, что в современной десктопной ОС функционал для создания новых пользователей вообще должен быть крайне урезан. У нас есть пользователь `root` (на всякий случай, а вдруг у нас система сломается и придётся её восстанавливать — Linux не отличается особой стабильностью), есть несколько системных пользователей, и есть один единственный **обычный** пользователь, от имени которого и будут работать люди за компьютером. `root` и системные пользователи скрыты от глаз обычного юзера, потому что ему их видеть не следует. За всю свою жизнь я не видел ни одного человека, у которого на компьютере заведено несколько обычных пользователей, от имени которых люди работают за компьютером.

## Комбинации клавиш

Самым важным отличием Haiku от других систем является замна клавиш Alt и Ctrl местами. Например, если в современных ОС для переключения окон существует комбинация <kbd>Alt</kbd>+<kbd>Tab</kbd>, то здесь <kbd>Ctrl</kbd>+<kbd>Tab</kbd>.

![](pic/key-layout.png)

К слову, клавиша <kbd>Super</kbd> (с логотипом Windows) здесь имеет название <kbd>Option</kbd>, а клавиша <kbd>Alt</kbd> в программе «Раскладка» (её скриншот выше) имеет название <kbd>Cmd</kbd>, хотя в остальных программах упоминается её привычное назание <kbd>Alt</kbd>.

Комбинация <kbd>Alt</kbd>+<kbd>F4</kbd> не закрывает окно, а переключает нас на четвёртый рабочий стол. Кстати, каждый рабочий стол может иметь свои обои.

Комбинация <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Z</kbd> разворачивает окно до максимального размера, а <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Z</kbd> разворачивает окно на весь экран, закрывая собой Deskbar:

![](pic/zoom.png) | ![](pic/zoom1.png)