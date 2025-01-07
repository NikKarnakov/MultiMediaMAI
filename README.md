# Лабораторные работы №1-5

------------------------------------------------
|  Выполнил    |    Группа       | Дата        |
|--------------|-----------------|-------------|
| Карнаков Н.Д.|    М8О-406Б-21  |   06.01.2025|

# Проектная структура

Данный репозиторий содержит следующие компоненты:

## Папка `data`
Папка `data` содержит датасеты, которые используются для анализа и выполнения лабораторных работ.

## jupyter-notebook
Файл `Lab1_5_MultiMedia_MAI_Karnakov_406.ipynb` включает в себя лабораторные работы в jupyter-notebook

ПРИМЕЧАНИЕ: в этом файле не отобразились графики в задаче регрессии. Ссылка на google collab: https://colab.research.google.com/drive/1yH__xVWLB79hz3zYfNWbsPAjX8JCRdRF?usp=sharing

---

## Выбор метрик

### Для классификации:
В таблице для задач классификации представлены значения F1-score, так как эта метрика учитывает баланс между точностью (precision) и полнотой (recall).

### Для регрессии:
Для регрессии в таблице указаны **MSE** в качестве основной метрики.

MSE является одной из самых распространённых метрик для задач регрессии, что позволяет легко сравнивать эффективность разных моделей. Благодаря своей универсальности и популярности, MSE является стандартом для большинства регрессионных алгоритмов, что упрощает оценку их качества.

---

## Таблица 1. Метрика качества на тестовом наборе данных

| Алгоритм           | Задача           | Бейзлайн     | Улучшенный бейзлайн | Самостоятельная реализация алгоритма | Улучшенная Самостоятельная реализация алгоритма |
|---------------------:|:------------------:|:----------------:|:---------------------:|:---------------------------------------:|:---------------|
| **KNN**            | классификация (F1)   |      0.5862          |   0.5954                 |        0.5645               |     0.5950     |
|                     | регрессия     (MAE)   |          0.3426       |       0.0833              |           0.2167                            |      0.0833          |
| **Линейные модели** | классификация  (F1)   |        0.6667        |     0.6435               |          0.000                             |    0.6610      |
|                     | регрессия     (MAE)    |      0.1787          |         0.1125            |           0.1794                            |    0.1125    |
| **Решающее дерево** | классификация  (F1)   |         0.6723       |       0.6723             |         0.4601                              |   0.6500    |
|                     | регрессия    (MAE)     |       0.3667         |       0.1000              |           0.2379                            |     0.1689   |
| **Случайный лес**   | классификация   (F1)  |         0.6126        |        0.6496             |               0.6666                        |   0.6434     |
|                     | регрессия   (MAE)      |        0.2008        |         0.1000            |             0.1694                          |    0.1005       |
| **Градиентный бустинг** | классификация (F1) |     0.6491           |          0.6897            |           0.000                            |      0.000  |
|                     | регрессия   (MAE)      |        0.1842        |       0.0667              |           0.1523                            |      0.1043       |
### Общие выводы:

#### 1. Классификация:
- **F1-score**: В таблице метрик для классификации заметно, что улучшение бейзлайна приводит к небольшим, но стабильно положительным результатам. Например, для алгоритма **KNN** улучшение с 0.5862 до 0.5954 показывает улучшение точности и полноты, что свидетельствует о более сбалансированном классификаторе. Для других алгоритмов (таких как **Решающее дерево** и **Случайный лес**) мы наблюдаем схожие тенденции с небольшими улучшениями после настройки.
- Самостоятельные реализации большинства моделей дают результаты, близкие к улучшенному бейзлайну. Например, **KNN** показывает схожий результат в улучшенной реализации (0.5950 по сравнению с 0.5954 в улучшенном бейзлайне), что может свидетельствовать о качественной настройке гиперпараметров или хорошем стартовом решении.
- Для алгоритмов **Градиентный бустинг** и **Линейные модели** наблюдаются проблемы: у **Градиентного бустинга** результат после улучшения бейзлайна резко падает (с 0.6491 до 0), а у **Линейной модели** также имеет место значительное падение качества классификации (с 0.6667 до 0). Это может указывать на проблемы с переобучением или неправильной настройкой алгоритмов.

#### 2. Регрессия:
- **MAE**: Для задач регрессии улучшение бейзлайна приводит к значительному снижению ошибки. Например, **KNN** улучшил показатель MAE с 0.3426 до 0.0833, что является значительным улучшением. Подобные улучшения наблюдаются и для других моделей: **Линейная регрессия** снизила ошибку с 0.1787 до 0.1125, **Решающее дерево** — с 0.3667 до 0.1000, **Случайный лес** — с 0.2008 до 0.1000, а **Градиентный бустинг** — с 0.1842 до 0.0667.
- Самостоятельные реализации показывают улучшения, но не такие значительные, как улучшенные бейзлайны. Например, **KNN** в самостоятельной реализации имеет MAE 0.2167, что лучше базового результата, но хуже улучшенной версии.
- Для алгоритмов **Решающее дерево**, **Случайный лес** и **Градиентный бустинг** результаты после улучшения бейзлайна дают значительно меньшую ошибку MAE, что подтверждает успешность оптимизации и подбора гиперпараметров. Например, **Градиентный бустинг** улучшился с 0.1523 до 0.0667, что является сильным результатом в контексте регрессионных задач.

#### 3. Выводы:
- **Оптимизация бейзлайна** играет ключевую роль в улучшении качества моделей как для классификации, так и для регрессии. Улучшение в показателях F1-score и MAE свидетельствует о значительном улучшении общей производительности моделей.
- **Самостоятельные реализации** часто показывают близкие результаты к улучшенным бейзлайнам, но в большинстве случаев остаются немного хуже. Это может быть связано с особенностями реализации, недостаточной настройкой гиперпараметров или выбором модели.
- Для некоторых моделей, таких как **Градиентный бустинг** и **Линейная модель**, требуется особое внимание к настройке и предотвращению переобучения, поскольку после улучшения бейзлайна они показали значительное ухудшение результатов. Это требует дополнительного тестирования и настройки моделей, чтобы добиться оптимальной производительности.


