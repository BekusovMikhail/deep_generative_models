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
#### Значений метрик нет в данном задании
### Эксперименты
#### Baseline
Стандартная имплементация CSPUp блока, обычная реализация без фишек.  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b02953e0-c4fe-4f9e-8a43-b2ccacf67373)  
Результат: разошлось, дискриминатор ушел в 0  
#### Add weight decay and increase batch size
1. Добавление L2 регуляризации в дискриминатор и генератор для уменьшения вероятности расхождения из-за огромных весов  
2. Увеличение BatchSize для большей выборки обучения генератора (больше, чем 256 на моей GPU не влезло :( )  
Результат: по loss'ам все шло стабильно до 11 эпохи  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/53ca8a79-075e-4cb7-bd94-050417ee3965)  
По изображениям можно сказать, что все пришло к плохому концу плохо
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/cce3e898-c7f5-4604-96a1-582530e15d34)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/734a588a-e902-4dd8-8522-23cadfa0548f)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/779f51b8-0404-48ae-b1f1-4658f59a351c)  
По сравнению с BaseLine видно, что не разошлась сразу и хоть как-то, но обучалась
#### LeakyRelu and BatchNorm
1. Добавление LeakyRelu, так как во многих гайдах обучения GAN советуют заменять ReLU на LeakyReL в дискриминаторе и генераторе для уменьшения вероятности расхождения  
2. Добавление BatchNorm для нормализации батча между свертками  
Результат: разошлось сразу  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/efb49700-1410-46f3-a075-c430ef82f9ad)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f9b9e9a2-8763-4662-9aa8-44666db061d8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8d4ef5df-615a-4cc6-ad8d-09691193a7fa)  
#### Max Poool and Avg Pool
1. Добавление MaxPool или AvgPool в дискриминатор для более медленного обучения дискриминатора, уменьшение количества сверток.  
2. Результат: самые адекватные предсказания из всех, что предсталвены выше  
Результат: По Loss можно сказать, что модель не рухнула, а целенаправленно сходилась, правда, с провалом посередине обучения  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/28d56d72-7b69-4ea8-8aa6-7824726cca65)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/74474ac2-228f-4a94-864c-60e7a405da50)  
#### LR для Discriminator и Generator, кол-во сверток в дискриминаторе и обучение каждые n эпох
1. Провел много экспериментов для подбора LR в Discriminator и Generator, были выбраны эти значения  
2. Увеличение кол-ва сверток в дискриминаторе для уменьшения вероятности Mode Collapse  
3. Обучение Discriminator каждые n эпох
Резльутат: эксперимент, к сожалению, провалился  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/10d9398e-9f0e-4e6b-b39b-2f4e53a6cda2)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a70e1076-2787-44a8-89a3-5a61e2cb75f0)  
## Logging
Прововодил около 100, каждый эксперимент из-за сохранения изображений весит больше 1 ГБ, поэтому прилагаю скрины из TensorBoard и подтверждение  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/c6891f35-24a0-4702-8688-0dd8b2f6a795)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fe8b6d0d-90a8-4c54-a924-18bfa06059d0)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/383004d4-4e13-487e-b55d-36f2b56beb4f)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a88bf59c-0701-488c-bea2-45464ae86d01)  
## Дополнительно
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/e43061fb-32b7-4aa6-b919-c702e92f209b)  
## Выводы
Проведя сверх сотни экспериментов, я могу сказать, что обучение GAN сильно зависит от инициализации весов и рандома в целом.  
Если не учитывать Mode Collapse, то считаю, что получение сходимости - есть, изображения генерируются :)  
