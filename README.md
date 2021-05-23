# Алгоритм Дейкстры

[![CMake](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-dijkstra-algorithm-dan/actions/workflows/cmake.yml/badge.svg?branch=main)](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-dijkstra-algorithm-dan/actions/workflows/cmake.yml)

### Краткое описание семестрового проекта
В данной семестровой работе обозревается **алгоритм Дейкстры**.
- Данный алгоритм используется для нахождения кратчайших путей в графе из заданной вершины
- Общая формула для оценки сложности по времени T = O(n \* T1 + m \* T2), где n - количество вершин в графе, m - количество ребер, T1 - время нахождения минимальной метки среди невыбранных вершин, T2 - время смены метки
- В данной работе для хранения невыбранных вершин была использована бинарная куча, поэтому сложность по времени - T = O(n \* log(n) + m \* log (n))
- Для хранения графа был использован список смежности, поэтому M = O(m + n)


## Команда "Odin's bless"


| Фамилия Имя   | Вклад (%) | Прозвище              |
| :---          |   ---:    |  ---:                 |
| Галеев Даниль   | 100        |  Мигелиус               |


**Девиз команды**
> _О́ди́н в поле воин!_

## Структура проекта


Проект состоит из следующих частей:

- [`src`](src)/[`include`](include) - реализация структуры данных (исходный код и заголовочные файлы);
- [`benchmark`](benchmark) - контрольные тесты производительности структуры данных (операции добавления, удаления,
  поиска и пр.);
- [`examples`](examples) - примеры работы со структурой данных;
- [`dataset`](dataset) - наборы данных для запуска контрольных тестов и их генерация;
- [`graphics`](graphics) - скрипт для визуализации результатов контрольного тестирования

## Требования (Prerequisites)

 Рекомендуемые требования:

1. С++ компилятор c поддержкой стандарта C++17 (например, _GNU GCC 8.1.x_ и выше).
2. Система автоматизации сборки _CMake_ (версия _3.12.x_ и выше).
3. Интерпретатор _Python_ (версия _3.7.x_ и выше).
4. Рекомендуемый объем оперативной памяти - не менее 4 ГБ.
5. Свободное дисковое пространство объемом ~ 400 МБ (набор данных для контрольных тестов).

## Сборка и запуск

#### Сборка проекта

Зайдите на [главную страницу](https://github.com/Algorithms-and-Data-Structures-2021/semester-work-suffix-tree-dan) проекта и нажмите кнопку code, показанную  на рисунке снизу


![clone](https://user-images.githubusercontent.com/70788419/116008429-26ca8100-a61d-11eb-8d58-9a2f5ff2394b.png)
 
 Либо вы можете склонировать себе проект в локальный репозиторий с помощью консольной команды:
```shell
git clone https://github.com/Algorithms-and-Data-Structures-2021/semester-work-dijkstra-algorithm-dan.git
```


Для автоматичекой сборки зайдите в IDE (у меня это CLion) и нажмите на кнопку сборки проекта (в моем случае зеленый молоток)


![build](https://user-images.githubusercontent.com/70788419/116302645-1dbaea80-a7aa-11eb-91aa-088a8bd0fd16.png)


#### Генерация тестовых данных

Для того, чтобы сгенерировать тестовые данные, вам нужно в консоли перейти в папку dataset, поскольку именно там хранятся скрипты, которые позволят вам сгенерировать данные

Генерация тестового набора данных в
формате [comma-seperated values (CSV)](https://en.wikipedia.org/wiki/Comma-separated_values):

```shell
# переход в папку генерации набора данных
cd dataset

# запуск Python-скрипта
python generate_csv_dataset.py
```

Для работы скрипта вам необходимо установить библиотеку numpy. Это можно сделать следующим образом:
```shell
pip install numpy
```

Для удобства запуска контрольных тестов данные организованы в директориях:

```shell
dataset/data/
  dijkstra-algorithm/
    01/
      100.csv
      ...
      1000000.csv
    02/ ...
    03/ ...
    ...
    10/ ...
  ...
```

По названию директории `/dataset/data/dijkstra-algorithm` можно понять, что здесь хранятся наборы данных для контрольных тестов по
**выполнению работы алгоритма**. Названия файлов `100.csv`. `200.csv` и т.д. хранят информацию о размере набора данных (т.е. количество вершин в графе). 

#### Контрольные тесты (benchmarks)

Для запуска контрольных тестов для начала перейдите в папку benchmarks. Там вы увидите текстовый файл с настройками для теста.
Там всё предельно просто, но во избежании ошибочных действий давайте разберём, что же там находится
```
absolute path to the dataset directory=/home/miguelius/CLionProjects/semester-work-dijkstra-algorithm/dataset/data/dijkstra-algorithm
absolute path to the directory, where you want to store results of benchmarks=/home/miguelius/CLionProjects/semester-work-dijkstra-algorithm/benchmark/results/test
file names=100.csv,500.csv,1000.csv,5000.csv,10000.csv,25000.csv,50000.csv,100000.csv,250000.csv,500000.csv,750000.csv,1000000.csv
count of one dataset tests=10
```

Как вы можете видеть, здесь сначала идёт описание, потом идёт значение, которое нужно установить.
1. Абсолютный путь до папки с тестовыми данными
2. Абсолютный путь к папке, в которую вы хотите записать файлы с результатами тестирования
3. Имя файлов, с которых вы будете читать данные. Таким образом, вы можете выбирать, какие данные вы будете тестировать
4. Количество повторных запусков для каждого набора данных

Мои тестовые наборы данных на [Google Drive](https://drive.google.com/drive/folders/1zDf4mEJBtYvaZStx76TWguSTEduWeO7h?usp=sharing).

##### Список контрольных тестов

| Название                  | Описание                                | Метрики         |
| :---                      | ---                                     | :---            |
| `algorithm_benchmark` | выполнение алгоритма   | _время_         |

##### Примеры запуска

Не забудьте перед запуском **поменять файл настроек**, иначе тест **не будет работать**!

```shell
# в параметрах запуска нужно указать абсолютный путь до настроек для запускаемого теста
./algorithm /home/miguelius/CLionProjects/semester-work-suffix-tree-dan/benchmark/dijkstra-algorithm.txt
```

##### Визуализация для особо интересующихся

Вы уже видели в структуре проекта, что скрипты находятся в папке graphics. Вам нужно перейти туда. 

Для начала разберемся с тем, по каким данным строятся графики. Вы можете увидеть файл data.csv. Давайте откроем его!

![csv-example](https://i.imgur.com/Ire6jXf.png)

В принципе все и так понятно, но все равно распишем.
- В первом столбце хранятся длины строк, на которых проводилось тестирование
- Другой столбец хранит значения результатов теста в наносекундах(советую использовать средние значения, подсчитанные из результатов теста по всем наборам данных)
- Если хотите построить графики для своих значений, поменяйте их в этом файле

Теперь, когда в файле лежат нужные данные, построим графики
```shell
cd /your/path/to/the/directory/graphics
python graphics.py
```

Для работы скрипта вам необходимо установить библиотеку matplotlib. Это можно сделать следующим образом:
```shell
pip install matplotlib
```

Теперь в папке со скриптами у вас появятся картинка с графиком. Вот и всё!

## Источники


1.  [Алгоритм Дейкстры(en wiki)](https://en.wikipedia.org/wiki/Dijkstra's_algorithm)
2.  [Алгоритм Дейкстры(ru wiki)](https://ru.wikipedia.org/wiki/%D0%90%D0%BB%D0%B3%D0%BE%D1%80%D0%B8%D1%82%D0%BC_%D0%94%D0%B5%D0%B9%D0%BA%D1%81%D1%82%D1%80%D1%8B)
3.  [Двоичная куча](https://ru.wikipedia.org/wiki/%D0%94%D0%B2%D0%BE%D0%B8%D1%87%D0%BD%D0%B0%D1%8F_%D0%BA%D1%83%D1%87%D0%B0)
4.  [Краткая лекция о теории графов](https://ita.sibsutis.ru/sites/csc.sibsutis.ru/files/courses/saod/saod_lecture_10.pdf#:~:text=%D0%A0%D0%B0%D0%B7%D1%80%D0%B5%D0%B6%D0%B5%D0%BD%D0%BD%D1%8B%D0%B9%20%D0%B3%D1%80%D0%B0%D1%84%20(sparse%20graph)%20%E2%80%93,%D0%B2%20%D0%B3%D1%80%D0%B0%D1%84%D0%B5.%20%F0%9D%90%B8%20=%20%F0%9D%91%82(%7C%F0%9D%91%89%7C))
