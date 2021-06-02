# Примеры неправильного применения критерия Манна-Уитни (aka U-test)

В разное время разные люди предлагали использовать критерий Манна-Уитни в расчете АБ-тестов. Поэтому решил написать об этом.

Если распределение метрики сильно отличается от нормального, то критерий Манна-Уитни обладает большей мощностью (быстрее «прокрашивается»), чем t-тест. Поэтому может возникнуть соблазн применить этот критерий для проверки метрик с асимметричным распределением (например, выручка на пользователя).

Но на самом деле он не проверяет нуль гипотезу равенства средних двух генеральных совокупностей. Кто-то говорит, что этим критерием можно проверить нуль гипотезу равенства медиан. Но это тоже ошибка.

Для демонстрации сделал несколько примеров в юпитере. Тест, который подходит для проверки нуль гипотезы равенства средних генеральных совокупностей, не должен прокрашиваться, если средние выборочные равны. Аналогично для медианы.

Критерий Манна-Уитни сложно интерпретировать. Он проверяет гипотезу, что для любых `x` и `y`, выбранных случайно из двух генеральных совокупностей, вероятность того, что `x > y`, равна вероятности того, что `y > x`. Если вы вдруг решили применить этот тест к метрике, подумайте, как вы будете объяснять результаты продакту :)

Соответственно, если в тесте мы хотим вырастить выручку на пользователя, то этот критерий применять нельзя. Метрики, для которых этот критерий может подойти, — метрики времени (между какими-то двумя событиями). Но сложность интерпретации при этом никуда не девается. Это точно не критерий для проверки равенства среднего или медианного времени.