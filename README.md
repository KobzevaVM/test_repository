# Анализ временных рядов

Сначала происходит считывание из файла **"training.csv"**, считываем тренировочную выборку. Считывание из файла типа csv
происходит с помощью команды *read_csv* (библиотека **Pandas**). Также построен график начальное выборки с помощью библиотеки
**matplotlib**. Далее описана функция *stationary_series(time_series)*, в качестве аргумента подается исследуемый временной ряд.
Данная функция исследует ряд на стационарность, сначала происходит визульная реулизация рада и его статистик(среднее и стандартное отклонение).
Для этого используются функции *mean()* и *std()* библиотеки **NumPy**. Также в этой функции найден коэффициент вариации, как отношение 
стандартного отклонения к среднему.
Ряд на стационарность исследуется с помощью теста Дики_фуллера. Для реализации теста Дики-Фуллера используется функция *adfuller()*
из библиотеки **statsmodels**. 

Далее разложим наш ряд на 4 составляющие: трендовую, циклическую, сезонную и нерегулярную. 
Простые моделями являются аддитивная модель и мультипликативная. Аддитивная - мы прсдеставляем ряд в вид суммы данных компонент,
мультипликативная - произведение компонент. Используем функцию *seasonal_decompose()* (также из библиотеки **statsmodels**).
Также есть построение графиков данных состовляющих. Затем проверяем наши ряды на стационарность с помощью выше 
описанной функции *stationary_series(time_series)*.

## Интегрируемость ряда порядка k
Функция diff() вычисляет разность исходного ряда с рядом с заданным смещением периода. Период смещения передается как параметр *period*.
Порядок интегрирования необходимо помнить для построения модели временного ряда. Для этого будет использовать модель ARIMA, 
построенную для ряда первых разностей.

def integration_k(time_series, k) функция, которая определяет порядок интегрируемости ряда, если порядок не больше аргумента k.

## Построение модели ряда
Чтобы построить модель нам нужно знать ее порядок, состоящий из 2-х параметров:
* p — порядок компоненты AR
* d — порядок интегрированного ряда
* q — порядок компонетны MA
Параметр d есть и он равет 1 (порядок интегрирования), осталось определить p и q. Для их определения нам надо изучить авторкорреляционную(ACF) и частично автокорреляционную(PACF) функции для ряда первых разностей.
ACF поможет нам определить q,PACF поможет нам определить p.
Для этого в пакете **statsmodels** имеются следующие функции: *plot_acf()* и *plot_pacf()*.

Затем с помощью функции *arima_model()* (**statsmodels**) определяем компоненты AR, MA.
C помощью информационного критерия Акаике находим наилучшую модель. Строим результат модели ARIMA для тренировочного ряда.

Затем происходит считывания тестовой выборки и построение графика прогноза.

## Запуск программы
Для заупска из терминала необходимо перейти в директорию с файлом **task2_time_series.ipynb** и 
осуществить запуска с помощью команты  **jupyter notebook task2_time_series.ipynb**
