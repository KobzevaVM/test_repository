# Задание 3

## Описание программы
Программа принимает на вход названия файлов, которые необходимо обработать: **sell.csv, supply.csv, inventory.csv**.
Эти три файла описывают один из магазинов торговой сети, каждый магазин находится в каком-то конкретном штате.
В программе учитывается, что первые две буквы названия файла являются почтовым кодом штата США.
Программа перестает считывать названия файла, если пользователь введет *"end"*.

Для каждого магазина мы получаем три файла: **daily.csv, steal.csv, sold_stolen.csv**.

* *daily.csv* содержит информацию о состоянии склада на каждый день,

* *steal.csv* содержит информацию о украденом товаре за каждый месяц,

* *sold_stolen.csv* содержит информацию о украденном и проданном товаре за каждый год.

После того, как были обработаны данные о всех магазинах, обрабатываются файлы **sold_stolen.csv**. 
Эти файлы объединяются, сортируются по годам и штатам, если несколько магазинов находятся в одном штате, 
то данные о продаже и сворованном товаре суммируются.
В результате получаем файл **all_sold_stolen.csv**, в котором данные объеденены по годам и штатам

## Используемы библиотеки
**pandas, csv**

## Запуск программы
Зайты в директорию с проектом 

Ввести в терминале **"jupyter notebook"**
