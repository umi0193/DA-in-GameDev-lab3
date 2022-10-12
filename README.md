# Лабораторная работа № 3 Реализация рейтинговой системы пользователей и ее интеграция в пользовательский интерфейс
Отчет по лабораторной работе #3 выполнила:
- Стрельчук Анастасия Александровна
- 1948616

Отметка о выполнении заданий:

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |


Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
Используя видео-материалы практических работ 1-5 повторить реализацию игровых механик.
- Задание 2.
Добавить в приложение интерфейс для вывода статуса наличия игрока в сети(онлайн или офлайн).
- Задание 3.
Реализовать вывод в консоль количества времени отсутствия игрока в сети
если пользователь офлайн.
- Выводы.

## Цель работы
создание интерактивного приложения с рейтинговой системой
пользователя и интеграция игровых сервисов в готовое приложение.

## Задание 1
### 
Ход работы:
1) Для начала нужно сделать так, чтобы энергетический щит следовал за мышкой, таким образом он смоет ловить яйца в последствии
2) Для этого я создала скрипт EnergyShield 
3) Далее в этом скрипте создаем переменную, которая бдует считывать позицию курсора мыши, где щит должен будет двигаться только по оси Z. Следующая переменная будет передавать значение в камеру, переводя его в 3D вариант.
4) Сохраняем, подключаем скрипт к щиту, как мы делали ранее с другими скриптами. Запускаем сцену и [наблюдаем, как щит передвигается за мышью по одной оси](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%9F%D0%B5%D1%80%D0%B5%D0%BC%D0%B5%D1%89%D0%B5%D0%BD%D0%B8%D0%B5%20%D0%B7%D0%B0%20%D0%BC%D1%8B%D1%88%D1%8C%D1%8E%20%D1%89%D0%B8%D1%82%D0%B0.jpg)
5) Следующим пунктом, я написала кметод OnCollisionEnter к тому же скрипту, а далее добавила Destroy, если предмет столкновения с щитом - яйцо. 
6) Теперь добавим элемент графического интерфейса, (GameObject--->UI--->Text-TextMeshPro) - создаем канвас. Импортируем нужные для его работы папки, далее нужно настроить Canvas.
7) Для этого меняем в окне инспектора его Render Mode - на Screen Space Camera. A в Render Camera подключим Main Camera, с которой я работала 
8) Plane Distance поменяю на 10, и нажав на Canvas получаю [такой результат](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%9F%D0%BE%D1%81%D0%BB%D0%B5%20%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B5%D0%BA%20Canvas.jpg)
9) Далее нужно настроить саму надпись - для этого меняем ее расположение, шрифт, размеры. Располагаем ее справа вверху с [такими настройками](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B8%20Score.jpg) И получаем при сохранении сцены и запуске такой [результат](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%9D%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0%20Score%20-%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82.jpg)
10) Теперь начну создавать элементы GUI - графического интерфейса для пользователя.  Для начала нужно в скрипте Energy Shield создать функционал для отображения счётчика очков.
11) Начну с создания метода внутри Start(чтобы это реализовывалось при запуске) - обнуление счетчика, а точнее - присвоение Score значения ноль. Для дальнейшего подсчета очков. [Вот результат](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%A3%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%B8%D0%BB%D0%B8%20%D0%BF%D1%80%D0%B8%20%D1%81%D1%82%D0%B0%D1%80%D1%82%D0%B5%20%D0%B7%D0%BD%D0%B0%D1%87%D0%B5%D0%BD%D0%B8%D0%B5%20%D1%81%D0%BA%D0%BE%D1%80%D0%B5%20%3D%200.jpg)
12) Далее запишем в скрипт подсчет пойманных яиц. Для этого в метод OnCollisionEnter пропишем считывание значение из переменной в формат инт увеличивая на единицу значение. Далее присваивая это значение в Score. [Результат](https://github.com/umi0193/DA-in-GameDev-lab3/blob/main/%D0%9F%D0%BE%D0%B4%D1%81%D1%87%D1%91%D1%82.jpg)
13) Далле нужно поработать с тем, что будет при промахе - если пользователь не поймает яйцо. В скрипт DragonEgg нужно записать код, который реализует перезапуск сцены при промахе. Для этого создадим метод DragonEggDestroyed в скрипте DragonPicker, и вызовем его в скрипте DragonEgg. Следующее за пропущенным яйцо также должно удаляться со сцены. 
14) Теперь поработаем с энергетическими щитами - при помощи счетчика делаем так, чтобы при промахе также удалялся один из 3 щитов. Далее добавляем перезапуск сцены после удаления последнего щита - то есть фактически перезапуск игры. [Получаем такой результат]()
15) Теперь поработаем над фоном - добавим из Assets Store ассет гор, и настроем фон. 
16) Теперь сделаем настройки света, переместив на сцену установленные фоны. Выбираем настройки через: Windows--->Rendering--->Lightning, для удобства закрепляем рядом с окном инспектор и производим настройку.
17) [Вот такой результат получаем]()

## Задание 2
### 
 
## Задание 3
###  



 
## Выводы




## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
