# Обучение поющей speech-to-speech модели so-VITS-svc
[Ссылка](https://drive.google.com/drive/folders/12grjr42p1gxH0KtHCSxyph-YWNSm1inV?usp=sharing) на все песенки на гугл диске  
Ноутбук с обучением, делением и установками: HW5/sovits_notebook.ipynb  
## Задачи
Выбрать исполнителей референса и исходника
Скачать песни
Разделить вокал и инструментал
Нарезать на семплы для подачи в сеть
Обучить сеть на семплах
Инференс сети на вокале целевой песни
# Задачи по пунктам
## Выбрать исполнителей референса и исходника
### Кто будет петь?
Папка HW5/speaker1 - Монеточка  
### Что будет петь?
Песня Michael Jackson They Don't Care About Us  
HW5/speaker0/full/Michael-Jackson-They-Don__039_t-Care-About-Us.wav  
## Скачать песни
Скачано
## Разделить вокал и инструментал
Разделено  
Папки speaker*/instrumental и speaker*/only_voice  
## Нарезать на семплы для подачи в сеть
Нарезано  
Папка - HW5/speaker1/sliced/sliced
## Обучить сеть на семплах
Обучено  
### Loss и tensorboard
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8f58ca08-5d70-46d2-8e29-3c7d4de9c15e)  
tensorboard --logdir=HW5/logs/sovits5.0  
## Инференс сети на вокале целевой песни
Сделано  
Голос - HW5/result_voice.wav  
[Ссылка на песню](https://drive.google.com/file/d/1iSjvp4V6Zp90uCUu94V_V94p0fVLtCT6/view?usp=drive_link)  
Песня - HW5/result.wav  
[Ссылка на песню](https://drive.google.com/file/d/1AZxsHI2T8y-sBkox1Lg_1pZJZhAEMiUP/view?usp=drive_link)  
