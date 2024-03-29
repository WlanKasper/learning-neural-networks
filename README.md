# Нейронный сети

## Основыные фреймворки на 2018

- TensorFlow
- Keras
- PyTorch

### Основные рекомендации обучения сети

- Запускать алгоритм для разных начальных значений весовых коэффициентов. Затем отобрать лучший вариант. Начальное значение генерируем случайным образом, в окрестности нуля (чтобы не попасть в область где значение производной близко к нулю, что приведет к малому изменению весовых коэффициентов в процессе обучения), кроме тех что относятся к bias (bias - смещение проскости/гиперплоскости);
- Запускать алгоритм обучения с оптимизацией по Adam или Нестерову для ускорения обучения;
- Выполнять нормировку входных значений и запоминать нормировочные параметры: min, max из обучающей выборки, для применения на практических выходных значениях;
- Помещать в обучающую выборку разнообразные данные примерно равного количества;
- Наблюдения на вход сети подавать случайным образом, корректировать веса осле серии наблюдений, разбитых на mini-batch (mini-batch - выборка около 1000 экземпляров);
- Использовать минимальное необходимое количество нейронов в сети, для избежания эффекта переобучения (когда сеть слишком сильно подстраивается под обучающую выборку);
- Разбивать все множество наблюдений на три выборки: обучающую, валидирующую, тестовую. Это необходимо для предотвращения эффекта переобучения;
- При малом количестве скрытых слоев можно использовать гиперболическую или логистическую (сигмоидальную) функцию активации или ReLu (или ее вариации) при большом количестве слоев;
- Для задач регрессии у выходных нейронов использовать линейную (linear) функцию активации, для задач классификации не пересекающийся классов - SoftMax;

### Критерии остановки процесса обучения сети

- При расхождении параметров качества обучающей и валидирующей выборки;
- От итерации к итерации (по всей эпохе) показатель качества выходит на плато. В таком случае можно: переопределить параметры для градиентного алгоритма, переиннициализировать сеть с другими весовыми коэффициентами;
- Малое изменение весовых коэффициентов;
- Достигли максимального числа итераций.

### Функции активации для нейронов (скрытых слоев)

- Пороговая функция (редко);
- Гиперболический тангенс (если меньше 5 скрытых слоев);
- Логистическая функция (если меньше 5 скрытых слоев);
- ReLu (f(x) = max(x,0)) если больше 5 (deep learning);

### Функции активации для нейронов (выходных слоев)

- Линейная (linear) к примеру в задачах регрессии (если с выходным сисловым значением ничего делать не нужно);
- SoftMax к примеру в задачах классификации (если нужно получить интерпритацию в виде вероятности принадлежности к каждому из классов по значению входного вектора). Для Softmax важен правильный критерий качества которым принято считать перекрестную энтропию;

### Критерии качества

- Для распознования:
  - hinge / hinge^2
  - бинарная кросс-энтропия: при классификации двух классов
  - катигориальная кросс-энтропия: при классификации более двух классов
- Для обработки текста:
  - логарифмический гиперболический косинус (logcosh)

- Для регрессии:
  - средний квадрат ошибок (mean squared error)
  - средний модуль ошибок (mean absolute error)
  - средний абсолютный процент ошибок (mean absolute percentage error) - отлично для прогнозирования
  - средний квадрат логарифмических ошибок (mean squared logarithmic error)
