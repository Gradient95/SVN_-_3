# Инструкция по работе с Git и удалёнными репозиториями

## Что такое Git?

одна из реализаций распределённых систем контроля версий, имеющая как локальную версионность, так и версионность на сервере. Git является самой популярной системой контроля версий на сегодняшний день

## Подготовка репозитория
Для того, чтобы создать репозиторий в указанной папке, используется команда "git init". Для этого достаточно написать команду в папке с будущим репозиторием

## Создание фиксаций

### Создание коммитов

Для создания новой фиксации необходимо использовать команду "git commit". Используется она следующим образом: в папке с репозиторием пишется команда "git commit -m *<сообщение к коммиту>*. Все файлы коммита должны быть предварительно добавлены с помощью команды  *git add*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

### Добавление файла к коммиту
для того чтобы добавить файл к новому коммиту ("сохранению") необходимо использовать команду "git add". Используется она следующим образом: в папке с репозиторием пишем команду *git add <имя файла>*

### Просмотр информации о изменениях

для того, чтобы посмотреть информацию об изменениях в текущей ветке, необходимо использовать команду *git status*. Для этого достаточно использовать *git status* в папке с репозиторием

## Перемещение между сохранениями

Для перемещения между "сохранениями" _(Коммитами)_ нужно вызвать журнал изменений с помощью команды *git log*. Откроется список со всеми коммитами в ветке, в которой мы находимся *(о ветках ниже)*. Чтобы перейти в нужный нам коммит, нужно ввести команду *git checkout <hash>*. __*Hash (Хэш)*__ - это индивидуальный номер коммита. Команде достаточно 4-5 первых символов хэша, но в случае когда коммитов очень много, чтобы избежать вероятность перехода не на тот коммит, следует копировать весь хэш.

## Журнал изменений

О *журнале изменений* уже было сказано ранее. Журнал вызывается командой *git log*. При вводе команды в терминале выявляются последние 3 коммита в данной ветке. Для просмотра предыдущих коммитов, нужно нажать *Space (Пробел)*. Из журнала можно перемещаться между коммитами. Для более наглядного просмотра изменений веток *(Если было создание новых/слияние/удаление веток)*, нужно воспользоваться командой *git log --graph*.

## Ветки в Git

Для удобства и систематизации и чтобы не "засорять" главную *(чистовую)* ветку, используются побочные ветки. Чтобы создать новую ветку, нужно использовать команду *git branch <branch_name>*, либо *git checkout -b <branch_name>*. В первом случае, чтобы перейти на созданную ветку, используем *git checkout <branch_name>*, во втором мы автоматически переходим на созданную ветку. Проверить, на какой ветке мы находимся, можно с помощью *git branch*.

## Слияние веток

Для объединения веток используется команда *git merge <branch_name>*. При этом содержимое из ветки <branch_name> *"Смёрджится" (сольётся)* в содержимое ветки, в которой мы сейчас находимся. При этом <branch_name>, из которой мы мёрджили данные, остаётся.

## Слияние веток и разрешение конфликтов

При автоматическом слиянии веток могут происходить конфликты, если, например, данные в одной ветке удалялись. В таком случае стоит уже вручную приминать или отклонять изменения при слиянии.

## Удаление веток

Для того, чтобы удалить ненужную нам ветку, нужно воспользоваться командой *git branch -d <branch_name>*. В случае, если в ветке присутствуют не *"закоммиченные"* изменения, команда выдаст ошибку. Чтобы произвести удаление несмотря на изменения без коммита, элемент команды *-d* заменяется на *-D*: *git branch -D <branch_name>*.

## GitHub и удалённые репозитории

### что такое GitHub

GitHub - это сервис для хранения *удаленных репозиториев* (находящихся на сервере и доступные для редактирования и скачивания), а так же для облегчения командной работы над одним проектом. Сервис позволяет не только создавать, скачивать и добавлять репозитории, но и вносить изменения прямо на сервисе.

### Регистрация и создание репозитория

Для работы с сервисом необходимо зарегистрироваться. Для этого нужно перейти по ссылке на сервис __*https://github.com*__ и воспользоваться кнопкой *Sign up*, и выполнить регистрацию одним из предложенных способов. После регистрации, для создания удаленного репозитория, необходимо перейти на вкладку *Your profile*, далее на вкладку *Repositories*, и нажать кнопку *New*. Далее вводим название нового репозитория, описание, выбираем *публичным или приватным* будет наш репозиторий, и жмём *Create repository*. 

Для того, чтобы отправить локальный репозиторий в удаленный, необходимо ввести команду *git push origin master*. После ввода начнётся отправка репозитория.

## Скачивание удалённого репозитория

Для скачивания удаленного репозитория есть несколько способов. Можно воспользоваться командой *git clone <ссылка>*, при этом создается копия удаленного репозитория на устройстве. Если же нужно загрузить изменения из удаленного репозитория в связанный локальный репозиторий, необходимо ввести команду *git pull origin*, при этом в локальный репозиторий "сливаются" все изменения, коммиты из удаленного репозитория, а так же создается новый коммит.

## Отправка запроса по удаленному репозиторию 

Для того, чтобы рассказать другим о тех изменениях, которые были размещены в репозитории, необходимо сделать запрос. Для этого нужно сделать *Fork* уже существующего репозитория, далее внести свои изменения, сделать коммит, и далее нажать на *Pull Request*. Эта команда отправит автору оригинального репозитория запрос на внесение изменений в файл.