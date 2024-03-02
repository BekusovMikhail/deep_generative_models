# Байесовский генератор стилей
## Задачи  
На основе формулы MLE и формулы Байеса о полной вероятности генерировать случайный стиль  
Вернуть вероятность генерации данного стиля  
Написать генератор изображений, который генерирует новый аватар  
Выложить в репозиторий 5 сгенерированных аватаров  
## Резкультаты
Предоставлены в HW1.ipynb и в папке avatars  
# Автоэнкодер по лункам
## Задачи
Имплементировать автоэкодер  
Обучить автоэнкодер  
Найти threshold для определения классификации normal/proliv  
Посчитать качество  
## Датасет
Предоставлен разработчиками курса  
## Результаты
Предоставлены в HW1.ipynb  
### Результаты обучения
#### График loss
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8f97f312-4617-4f4e-be83-b2909fdb707c)
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/969c83c7-6f97-4b86-a611-f5d7d60301db)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/75a16848-1c74-44bc-969c-82e2a3e8ee4f)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d9f8ca95-9c45-445e-84fd-4d53214750a7)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/34d07c14-1fbc-4e74-8cb8-88382c51039f)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/aff15718-fe6d-4d9e-b9d3-2304cae4ac99)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/16029077-9e4e-4e01-91b7-b0354fb0880f)
#### Метрики
Precision 0.15441176470588236  
F1_score 0.2595797280593325  
Recall 0.813953488372093  
TPR 0.813953488372093  
TNR 0.8431105047748977  
### Эксперименты
Цель: достичь обучения автоэнкодера на нормальных изображениях, чтобы в дальнейшем с помощью mse ошибки отсеивать изображения с проливом  
Идея: реализовать автоэнкодер  
Результаты: выше в результатах обучения  
Mean MSE value for normal: 0.23744981735944748  
Mean MSE value for proliv: 1.6871622800827026  
Выводы: автоэнкодер реализован, по средним значениям mse видно, что ошибка у proliv гораздо больше  
## Logging
tensorboard --logdir=HW1/runs/  
Прововодил множество экспериментов, около 70, но для того, чтобы было видно результат закоммитил только один
