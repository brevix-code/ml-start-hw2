# Домашняя работа №2

## 1) Датасет

Использую [Spaceship Titanic](https://www.kaggle.com/competitions/spaceship-titanic).
<br>Выбрал этот датасет, потому что по сравнению с другими вариантами он имеет небольшой размер и понятные признаки. При этом датасет достаточно сложный для проверки feature engineering, нескольких моделей и ансамблей.
<br>В обучающей выборке 8 693 пассажира и 14 столбцов, а в тестовой - 4 277 пассажиров и 13 столбцов. В данных нет полных дубликатов, но есть 2 324 пропущенных значения

## 2) Подход

1. Проверка типов данных, пропусков, дубликатов и распределения целевой переменной
2. Анализ числовых и категориальных признаков, выбросов и корреляций
3. Создание новых признаков из `PassengerId`, `Cabin`, возраста и расходов
4. Logistic Regression как baseline
5. Сравнение Logistic Regression, Decision Tree, Random Forest и Gradient Boosting по 5-fold CV accuracy
6. Подбор параметров Random Forest с помощью `GridSearchCV`
7. Weighted Voting из Logistic Regression, Random Forest и Gradient Boosting
8. Проверка выбранной по CV модели на local test и создание `submission.csv`

## 3) Результат

1. **Logistic Regression** как baseline получила CV accuracy `0.7913`
2. **Decision Tree** показал `0.7660`, то есть оказался хуже baseline
3. **Random Forest** получил `0.8026` и стал лучшей моделью без подбора параметров
4. **Gradient Boosting** показал CV accuracy `0.7961`
5. После `GridSearchCV` результат Random Forest вырос с `0.8026` до `0.8051`. Лучшие параметры: `max_depth=12`, `min_samples_leaf=2`,`n_estimators=200`
6. **Weighted Voting** получил `0.8034` и не смог обойти настроенный Random Forest

Лучшей моделью стал **Random Forest после GridSearchCV**. На test он показал accuracy `0.8039`. Результат близок к CV accuracy `0.8051`, поэтому сильного переобучения не видно