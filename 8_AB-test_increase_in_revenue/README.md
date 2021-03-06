# Принятие решений на основании А/В-теста / Decision making based on A/B test

`В этой директории два ноутбука: один посвящён приоритизации гипотез, а другой - принятию решения на основе результатов А/В-теста`.   
[приоритизация гипотез](https://github.com/IrinaTetereva/Yandex.Practikum_DA/blob/main/8_AB-test_increase_in_revenue/hypothesis.ipynb),  
[принятие решения на основе результатов А/В-теста](https://github.com/IrinaTetereva/Yandex.Practikum_DA/blob/main/8_AB-test_increase_in_revenue/AB-test_increase_in_revenue.ipynb)   
**Цели исследования** - выявить наиболее приритетную для исследования гипотезу и проанализировать результаты А/В-теста: выявить значимые различия в показателях выручки между двумя группами: А и В. Показателями выручки в тесте выступают: средний чек группы и конверсия группы.   

**Результаты проекта**:   
1. **Результаты приоритезации** по двум фреймворкам различны. Гипотеза-лидер в ICE (`Запустить акцию, дающую скидку на товар в день рождения`) заняла только пятое место во втором, т.к. у неё низкий охват пользователей, что достаточно логично, т.к. день рождения раз в году.  
Рассмотрим гипотезу-лидера по фреймворку RICE (`Добавить форму подписки на все основные страницы, чтобы собрать базу клиентов для email-рассылок`): за счёт высоко оцененного охвата среди пользователей эта гипотеза выиграла в приоритете, также оценка параметров Impact (влиение на пользователей) и Confidence (уверенность в успехе) у неё высокая и средняя оценка для Efforts (сложность тестирования).  
Отмечу, что фреймворк RICE оценивает приоритетность гипотез точнее, если нам важно включить охват пользователей.  

2. **Во второй части проекта нами получены следующие результаты А/В-теста** (при альфа=0,05):  
  1) для "сырых" данных:  
   - конверсия статистически значимо различается - средняя конверсия группы В больше относительно группы А на 13,8%  
   - средний чек не показал статистически значимого различия - средний чек группы В относительно группы А больше на 25,9 %.    
  2) для "очищенных" данных:  
   - конверсия статистически значимо различается - средняя конверсия группы В больше относительно группы А на 17,3%  
   - средний чек не показал статистически значимого различия - средний чек группы В относительно группы А даже меньше на 2 %.  
     
Как "очищенные", так и "сырые" данные получили похожие результаты: есть значимые различия в конверсии и нет значимых различий в среднем чеке. Результаты получились неоднозначные: мы видим, что конверсия значительно больше в группе В по сравнению с контрольной группой, а средний чек даже снизился при очистке от выбросов. Рост конверсии говорит о том, что к нам приходит больше покупателей, но в то же время их "качество" в лучшую сторону не изменилось (т.к. средний чек покупки меньше в В, чем в А). Т.к. тест проводится с целью выявить значимые различия в выручке, то показатель среднего чека в этом случае более подходящий для оценки результатов теста.   
Следовательно, предлагаю остановить тест и зафиксировать отсутствие различий между группами.   
В ходе работы с данными было выявлено, что процедура тестирования некорректна (не соблюдается количественная пропорция в группах и пользователи пересекаются между группами) и требует доработки.  

**Анализ строился в 2 этапа**: 1) приоритизация гипотез по методикам ICE и RICE, 2) анализ А/В-теста. Второй этап состоит из следующих шагов: обзор данных, небольшая предобработка и оценка корректности системы сбора данных для АВ-тестирования, анализ и выводы. Первоначальные данные находились в двух файлах. Пришлось их перегруппировать в удобные для анализа таблицы с агрегированными по дням кумулятивными данными о заказах и посетителях, используя `lambda` функцию.    
 
**Методы и навыки**: язык `python` (создание функций, циклы, списки, словари, строковые данные, логическая индексация), библиотека `pandas` (чтение файла, группировка и сортировка, нахождение среднего, медианы, обработка пропусков, замена типов данных, работа с датой и временем, обработка строковых значений, объединение таблиц, настройка отображения данных), библиотека `matplotlib` и модуль `pyplot` для визуализации данных (line, axhline, scatter), библиотека `scipy` модуль `stats` (проверка статистических гипотез критерием Манна-Уитни), библиотека `numpy` (logical_and, logical_not, logical_or, mean, percentile, arange), `А/В-тестирование` (`A/B-test`), методики приоритизации гипотез  `ICE` и `RICE`.

В первом ноутбуке: всего 6 ячеек, а во втором - 38 ячеек. Есть графики.  
`Проект завершён.`
