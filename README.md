# **Проект по прогнозированию оттока клиентов**
Этот проект посвящен прогнозированию оттока клиентов в телекоммуникационной компании с использованием алгоритмов машинного обучения. Цель заключается в разработке моделей, которые могут точно определить клиентов, склонных к оттоку, что позволит компании предпринять меры для их удержания.

##  Набор данных
В данном проекте используется набор данных, содержащий различные характеристики клиентов, такие как период нахождения клиента, ежемесячные затраты, общая сумма затрат, пол, статус пожилого гражданина, наличие партнера и детей, информация о телефонных и интернет-услугах, наличие онлайн-защиты и резервного копирования, доступ к технической поддержке, наличие онлайн-телевидения и подписки на фильмы, тип контракта, предпочтение биллинга, метод оплаты и целевая переменная - отток.

##  Предобработка данных и исследование
Перед построением моделей данные прошли предобработку и исследовательский анализ для подготовки их к использованию в алгоритмах машинного обучения. Были выполнены следующие шаги:

1) Обработка отсутствующих значений: Пропущенные значения в столбце "TotalSpent" были заменены нулями, чтобы можно было выполнить преобразование в числовой тип данных.

2) Масштабирование числовых признаков: Числовые признаки, включая "ClientPeriod", "MonthlySpending" и "TotalSpent", были стандартизированы с использованием StandardScaler, чтобы обеспечить одинаковый масштаб и предотвратить доминирование отдельного признака.

3) Кодирование категориальных признаков: Категориальные признаки были закодированы с помощью метода one-hot encoding с использованием OneHotEncoder и параметром "ignore" для обработки неизвестных категорий.

4) Исследовательский анализ данных: Гистограммы и круговые диаграммы были построены для визуализации распределений числовых и категориальных признаков соответственно. Также было проанализировано распределение целевой переменной - оттока клиентов.

##**Моделирование**
Для прогнозирования оттока клиентов были построены две модели: логистическая регрессия и CatBoostClassifier.

*Логистическая регрессия*: Была создана модель, включающая стандартизацию числовых признаков и кодирование категориальных признаков. С помощью метода GridSearchCV был выполнен поиск лучших гиперпараметров модели, оптимизирующих метрику ROC-AUC. Лучшая модель была обучена на полном наборе данных и использована для прогнозирования оттока.

*CatBoostClassifier*: Была создана модель, использующая алгоритм CatBoostClassifier, который хорошо работает с категориальными признаками. Модель была обучена с использованием обучающей выборки, а затем ее качество было оценено на валидационной выборке с помощью метрики ROC-AUC. Далее был выполнен поиск лучших гиперпараметров модели с использованием GridSearchCV, и лучшая модель была обучена на полном наборе данных.

##**Оценка качества моделей**
Оценка качества моделей была выполнена на валидационной выборке с помощью метрики ROC-AUC. Полученные результаты:

*Логистическая регрессия*: ROC-AUC на валидационной выборке составил 0.8323.

*CatBoostClassifier*: После выполнения поиска лучших гиперпараметров с использованием GridSearchCV лучшая модель CatBoostClassifier показала ROC-AUC на кросс-валидации равный 0.8451.

##**Прогнозирование на тестовом наборе данных**
Лучшая модель CatBoostClassifier была использована для прогнозирования оттока на тестовом наборе данных. Предсказанные значения были сохранены в файле "my_submission.csv". 
