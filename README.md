# Задание 2

## Краткое описание задания

 1. Считать данные из `training.csv`. Проверить является ли ряд стационарным в широком смысле. Это можно сделать двумя способами: 
    1. Провести визуальную оценку, отрисовав ряд и скользящую статистику(среднее, стандартное отклонение). Построить график на котором будет отображен сам ряд и различные скользящие статистики.
    2. Провести тест Дики - Фуллера.
    Сделать выводы из полученных результатов. Оценить достоверность статистики. (*25 баллов*)
  3. Разложить временной ряд на тренд, сезональность, остаток в соответствии с аддитивной, мультипликативной моделями. Визуализировать их, оценить стационарность получившихся рядов, сделать выводы. (*15 баллов*)
  4. Проверить является ли временной ряд интегрированным порядка `k`. Если является, применить к нему модель ARIMA, подобрав необходимые параметры с помощью функции автокорреляции и функции частичной автокорреляции. Выбор параметров обосновать. Отобрать несколько моделей. Предсказать значения для тестовой выборки. Визуализировать их, посчитать `r2 score` для каждой из моделей. Произвести отбор наилучшей модели с помощью информационного критерия Акаике. Провести анализ получившихся результатов. (*50 баллов*)


## Подход к решению

1. Чтение данных из `training.csv`
* Чтение производится `командой pd.read_csv('training.csv')`

2. Проверка на стационарность
    1. Визуальная оценка
        * Отрисовка ряда
            > ts = pd.Series(np.asarray(data['Value'], dtype=np.float), index=data['Date'])
            
            > ts.cumsum()
            
            > ts.plot(figsize=(20, 10))
            
            > plt.show()
        * Скользящее среднее (визуализация)
            > ts.rolling().mean().plot()
        * Стандартное отклонение (визуализация)
            > ts.rolling().std().plot()
        * Строим вывод о стационарности ряда по визуальной оценке
    2. Тест Дики-Фуллера
        * `sm.tsa.adfuller(ts)` - проводит тест Дики-Фуллера
        * Анализируем полученные из функции параметры
        * Строим вывод о стационарности данного ряда

3. Разложение временного ряда на тренд, сезональность остаток в соответствии с аддитивной и мультипликативной моделями
    * `models(data, model_s, title)` реализует разложение на соответствующие модели
				
    * 

## Инструкции по запуску

Cell -> Run All

## Необходимое ПО

### Библиотеки:
1) **Pandas**
* Для работы с временными рядами
2) **Numpy** 
* Для работы с массивами
* Функция `log()` - натуральный логарифм
* Функция `exp()` - экспонента
3) **Matplotlib.pylab**
* Для построения графиков функций
4) **Statsmodels**
* Используются статистические функции: `acf()`, `pacf()`,
`seasonal_decompose()`
* Для постороения модели ARIMA

### Программы:
1) Jupyter Notebook

## Участники

1) Горбунов Александр - 312 гр.

2) Гулиев Юрий - 312 гр.
