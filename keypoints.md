*Формального определения особой точки из источника, на который можно сослаться, я не нашёл, поэтому ниже привел тот
вариант из научпопа, который мне самому нравится больше.*

**Особая точка** изображения – это точка изображенного объекта, которая с большой долей вероятности будет найдена на
другом изображении этого же объекта.

Требования к особым точкам (Haralick and Shapiro, 1992, "Computer and Robot Vision"):

1. Отличимость: Особая точка должна выделяться на фоне и быть уникальной в своей окрестности.
2. Инвариантность: Выбор особых точек должен быть независимым от афинных преобразований.
3. Стабильность: Выбор особых точек должен быть устойчив к шуму и ошибкам.
4. Уникальность: Помимо локальной отличимости, особая точка должна также обладать свойством глобальной уникальности
   для того, чтобы улучшить различимость повторяющихся паттернов.
5. Интерпретируемость: Особые точки должны определяться таким образом, чтобы их можно было использовать для анализа
   соответствий и лучшей интерпретации изображения.

**Детектор** осуществляет поиск особых точек на изображении.

**Дескриптор** особой точки – вектор, описывающие структуру её окрестности. Он призван обеспечивать инвариантность
нахождения соответствий между точками относительно преобразований изображения.

**Матчер (matcher)** осуществляет построение соответствий между двумя наборами особых точек изображений на основании их
дескрипторов.

К особым точкам могут относиться углы, края, пятна.

Некоторые детекторы призваны распознавать исключительно углы. К таковым относятся Moravec, Harris, Shi-Tomasi, SUSAN,
Trajkovic, FAST. Они приведены в порядке их возникновения и в некотором смысле в порядке усложнения.

Детекторы углов устойчивы к поворотам, однако при изменении масштаба углы могут становится менее четкими и переставать
распознаваться. Для разрешение этой проблемы был разработан алгоритм SIFT (Scale-Invariant Feature Transform). Он также
попутно строит дескрипторы найденных особых точек.

Минус SIFT заключается в невысокой скорости работы. Алгоритм SURF, основан на тех же принципах что и SIFT, однако
имеются различия, благодаря которым SURF работает быстрее. Как и SIFT, он формирует дескрипторы для найденных особых
точек.

Ещё одной оптимизацией SIFT, а именно его метода построения дескрипторов, является алгоритм BRIEF.

Особенность алгоритмов SIFT и SURF в том, что они запатентованы и их коммерческое использование стоит денег. Библиотека
OpenCV предоставляет бесплатную альтернативу этим методам под названием ORB (Oriented FAST and Rotated BRIEF).

В OpenCV представлено большинство из вышеупомянутых
методов: [Feature Detection and Description](https://docs.opencv.org/4.x/db/d27/tutorial_py_table_of_contents_feature2d.html).