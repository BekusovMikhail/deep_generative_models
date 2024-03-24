# Имплементация GAN
## Задачи  
Скачать датасет CelebA (можно через pytorch)
Имплементировать CSPup блок  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f4028f6d-c56b-452a-84f0-457ecf74a2d5)  
Имплементировать генератор GAN по заданной архитектурной схеме  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/06792b20-90c3-4d45-ad5a-fa373c4270ee)  
Обучить имплементированный GAN  
Добиться схдимости (регуляризации, изменение архитектуры, фишки с train loop)  
Выложить сгенерирвоанные данные  
## Результаты
Предоставлены в HW2.ipynb и в папках samples*
Очень хотел бы предоставить папку runs со всеми экспериментами, но вес экспериментов зашкаливает  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/c6891f35-24a0-4702-8688-0dd8b2f6a795) 
## Датасет
[Celeba](https://mmlab.ie.cuhk.edu.hk/projects/CelebA.html)  
202599 сэмплов
## Результаты
Предоставлены в HW2.ipynb  
### Результаты обучения
#### Графики loss
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fe8b6d0d-90a8-4c54-a924-18bfa06059d0)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/383004d4-4e13-487e-b55d-36f2b56beb4f)
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1bd35f3c-d9d1-4592-ae4a-7d590e821ce0)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/cfff091d-892e-42ad-a53e-a1a29ea0a710)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/46e63cfc-1704-492a-9322-39da027bfb12)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/23b4dbdb-83d4-45e6-9f76-54eb82a04b74)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a8a1d4be-be7f-4721-b8fc-abfde288fa42)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1eac852b-aad0-4a62-be2b-f86396fb7ce6)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/9a6e067a-0cc3-44fe-938f-6d19e8bb2e94)  

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
