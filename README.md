# Обучение Stable diffusion 1.5 методом Dreambooth
## Задачи  
Собрать датасет от 15 изображений одного персонажа  
Кропнуть и заресайзить лица, тут можно обрабатывать сразу все  
Скачать предобученный чекпоинт SD1.5  
Обучить Stable diffusion 1.5
Обучить LoRA модель  
Сравнить лучший чекпоинт Unet и Lora  
Генерация любого варианта Controlnet из ноутбука, для обученных Unet и Lora  
## Результаты
Предоставлены в DreamBooth_Stable_Diffusion.ipynb и в папках с генерациями  

# Задачи по пунктам  
## Используемые промпты
### Для визуализации в readme
```
seed = 345252
prompt = "portrait of sks man face, in the apartment, lamp light, day, sitting on a chair, 4K, raw, hrd, hd, high quality, realism, sharp focus, beautiful eyes, detailed eyes"  
negative_prompt = "naked, nsfw, deformed, distorted, disfigured, poorly drawn, extra limb, missing limb, floating limbs, mutated arms, severed limbs, mutation, ugly, blurry, amputation"
```
### Для визуализации в папках
```
seed = 147525234 + 345324 * iter_step # Нужно, чтобы генерировались разные изображения для одного и того же запроса
token = "sks"
promt_list = [
    {
        "name": "kitchen",
        "prompt": f"close up portrait of {token} man face, in the kitchen, standing, 4K, raw, hrd, hd, high quality, realism, sharp focus",
        "n_prompt": "naked, nsfw, deformed, distorted, disfigured, poorly drawn, bad anatomy, extra limb, missing limb, floating limbs, mutated hands disconnected limbs, mutation, ugly, blurry, amputation",
    },
    {
        "name": "forest",
        "prompt": f"portrait of {token} man face, in the forest, standing, 4K, raw, hrd, hd, high quality, realism, sharp focus",
        "n_prompt": "naked, nsfw, deformed, distorted, disfigured, poorly drawn, bad anatomy, extra limb, missing limb, floating limbs, mutated hands disconnected limbs, mutation, ugly, blurry, amputation",
    },
    {
        "name": "street",
        "prompt": f"portrait of {token} man face, on the street, lights, midnight, NY, standing, 4K, raw, hrd, hd, high quality, realism, sharp focus, beautiful eyes, detailed eyes",
        "n_prompt": "naked, nsfw, deformed, distorted, disfigured, poorly drawn, bad anatomy, extra limb, missing limb, floating limbs, mutated hands, mutation, ugly, blurry",
    },
    {
        "name": "apartment",
        "prompt": f"portrait of {token} man face, in the apartment, lamp light, day, sitting on a chair, 4K, raw, hrd, hd, high quality, realism, sharp focus, beautiful eyes, detailed eyes",
        "n_prompt": "naked, nsfw, deformed, distorted, disfigured, poorly drawn, bad anatomy, extra limb, missing limb, floating limbs, mutated hands, mutation, ugly, blurry",
    },
    {
        "name": "office",
        "prompt": f"portrait of {token} man face, in the office, light, standing, 4K, raw, hrd, hd, high quality, realism, sharp focus, beautiful eyes, detailed eyes",
        "n_prompt": "naked, nsfw, deformed, distorted, disfigured, poorly drawn, bad anatomy, extra limb, missing limb, floating limbs, mutated hands, mutation, ugly, blurry",
    },
]
```
## Собрать датасет от 15 изображений одного персонажа
Был собран датасет с, лежит в папке arthas. Собирал изображения одного небезызвестного стримера :)  
## Кропнуть и заресайзить лица, тут можно обрабатывать сразу все  
Кропнуто, лежит в папке birme-512x512  
## Скачать предобученный чекпоинт SD1.5
Скачан, не стал выкладывать по причине огромного веса
## Обучить Stable diffusion 1.5
Обучено
### Результаты обучения
Получилось обучить нейросеть, автоматически сгенерировав регуляризационный датасет.  
Считаю, что получился отличный результат :)
#### График loss и Logging
$LOSS GPAPH  
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
Также Лежат в папке arthas_gen_unet  
#### Метрики
Метрик в данном задании не имеется  

## Обучить LoRA модель 
## Эксперименты
Цель: достичь самой лучшей и реалистичной генерации изображений с конкретным персонажем  
Идея: подбор гиперпараметров lr и rank
Результаты: в ноутбуке и ниже по каждому из экспериментов    
  
1. rank 32 lr 8e-4  
2. rank 16 lr 8e-4  
3. rank 8 lr 8e-4  
4. rank 4 lr 8e-4  
5. rank 32 lr 8e-5  
6. rank 16 lr 8e-5  
7. rank 8 lr 8e-5  
8. rank 4 lr 8e-5  
9. rank 32 lr 8e-3  
10. rank 16 lr 8e-3  
11. rank 8 lr 5e-3  
12. rank 4 lr 5e-3  
13. rank 2 lr 2e-4  
14. rank 4 lr 2e-4 - **Топ-1 вариант**
### 1. rank 32 lr 8e-4
Папка с визуализацией - ./HW4/db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/566a9da8-9363-4fed-8e60-04bcf9ac6daa)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/feda963b-fafd-49c4-a621-734f4db7e99c)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d1773fa7-fb31-4258-8cf9-6852d316f99b)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/9e918ca0-48b5-4c5f-b7f0-a5205bb07071)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/3e34eccc-b617-482c-ad28-86399a4f6082)  
./HW4/db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/cf55b263-b046-40e1-900f-6bf18ae34958)  
tensorboard --logdir=HW4/db_generation_lora_rank_32_lr_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 2. rank 16 lr 8e-4 
Папка с визуализацией - ./HW4/db_generation_lora_rank_16_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d7ff1b18-f12e-4cc8-9964-b9a14c86353a)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a34ae1c5-cd79-4034-9cde-7fdb2287794a)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/6836cfd0-996e-403f-9d64-9d96040516ed)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f56afca2-5801-4555-9fdc-b0f1312171b1)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/2d83b7cd-e361-4af3-8d81-74ceddce6654)  
./HW4/db_generation_lora_rank_16_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a6c1ce0e-3359-4ac9-9683-3dbd42603f55)  
tensorboard --logdir=HW4/db_generation_lora_rank_16_lr_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 3. rank 8 lr 8e-4
Папка с визуализацией - ./HW4/db_generation_lora_rank_8_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/75cd28d2-d0bf-450b-a49e-4e85fed195e5)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d718e941-c8ee-4fa7-b2ad-b6363fc84711)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/233d385f-f232-4046-a63d-0cb5f2b103a2)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/c08fb160-c226-4bcd-8135-f954037081ba)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4d90a582-631e-4ae3-87ef-8a343bac236e)  
./HW4/db_generation_lora_rank_8_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/26187974-961a-4181-90c3-0d1e2918c056)  
tensorboard --logdir=HW4/db_generation_lora_rank_8_lr_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 4. rank 4 lr 8e-4
Папка с визуализацией - ./HW4/db_generation_lora_rank_4_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/951296fb-953c-48b2-8082-940e4f586f20)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/269b6d17-cdf8-41d7-b3de-552d1d05a9b3)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/71e8a0f5-dde1-4092-9dc8-1ee1a3a5f146)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fa0e3017-b0f2-4c72-8bad-a10c81d233f8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/95f1fdc0-2212-451c-a7e0-8aa8440428ea)  
./HW4/db_generation_lora_rank_4_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8ba932c6-4ae3-4ffc-8fbc-262248f260a3)  
tensorboard --logdir=HW4/db_generation_lora_rank_4_lr_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 5. rank 32 lr 8e-5
Папка с визуализацией - ./HW4/db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b7bb46ed-a162-42d1-8419-176e8069d273)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b089b13f-17c7-415f-be8b-26537d25031c)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1c720361-d221-46a9-8958-0fd4a898bac9)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/66593ec1-21aa-44f0-94e4-e14003bbe5fa)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/c0681ead-778a-4dbe-b075-61deefc23a5c)  
./HW4/db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a2f90154-bcd7-4275-97ae-d7c206e28ae5)  
tensorboard --logdir=HW4/db_generation_lora_rank_32/log_dir/
#### Вывод
Слишком большой rank и lr  
### 6. rank 16 lr 8e-5
Папка с визуализацией - ./HW4/db_generation_lora_rank_16/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/cd0a957c-a4e8-4e19-ae93-89290c7839e8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/cc583b7c-1ae1-4d05-b2d6-95c7ccae04fe)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f82c6d8a-565c-43f5-a3ea-f2bcb4a9d088)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b456de80-5c6f-4fb2-a2af-352b76376a5d)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d6a1c5c4-f1c8-4ea0-af75-92cdd311b011)  
./HW4/db_generation_lora_rank_16/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/ff89bb7a-4bd6-44e0-bfd4-04e2417748dc)  
tensorboard --logdir=HW4/db_generation_lora_rank_16/log_dir/
#### Вывод
Слишком большой rank и lr  
### 7. rank 8 lr 8e-5
Папка с визуализацией - ./HW4/db_generation_lora_rank_8/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/ed7573b6-abb7-444b-ad00-2b6dec5d47d6)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/6d45dfe1-d711-4b7d-8e3b-160a4de6fccb)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/da96887b-e450-4ae1-9551-2b15e898501c)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/748b897b-85e0-43d4-a9cc-8a53fd76f934)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/88549866-d9c7-427d-804f-53a32adb0481)  
./HW4/db_generation_lora_rank_8/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/56241114-0c61-49f4-bf8b-0b5e03d2f628)  
tensorboard --logdir=HW4/db_generation_lora_rank_8/log_dir/
#### Вывод
Слишком большой rank и lr  
### 8. rank 4 lr 8e-5
Папка с визуализацией - ./HW4/db_generation_lora_rank_4/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fea562a9-da13-455e-b4d5-8b5a7e67d238)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1c6cbe90-bbb0-4157-bd5b-ea1d53f8309e)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4ce9aeef-4abd-4a4a-9659-4984c3fd377d)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1ec1194f-8473-4b76-996a-cc3e221fa9a2)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8f181ff5-0b7c-4331-b720-26c70e13d61e)  
./HW4/db_generation_lora_rank_4/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/6c7afb1d-bb06-40fd-ad6b-c6a48f4c5182)  
tensorboard --logdir=HW4/db_generation_lora_rank_4/log_dir/
#### Вывод
Слишком большой rank и lr  
### 9. rank 32 lr 8e-3
Папка с визуализацией - ./HW4/db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a901b936-74f5-400b-8a41-64271c9618c8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/5b7fe53e-bc0b-40b4-8a56-64e3ead25bdb)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/5c7921d0-db50-43b1-8a27-6977318b5753)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/50326479-623a-4444-a4e9-a29be05f2f22)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b48a08af-e920-4408-9443-32b13aac3709)  
  
./HW4/db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/7bbf967d-5a0f-46b1-8b06-fb0dc93f09f2)  
tensorboard --logdir=HW4/db_generation_lora_rank_32_lr_up_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 10. rank 16 lr 8e-3
Папка с визуализацией - ./HW4/db_generation_lora_rank_16_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1658e2ed-e2db-4540-b5db-886d3ec393f0)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/e5efdb20-c976-4890-8cdf-95e975063e29)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/0348feb7-fed9-4fae-b34e-ea5e214f61e5)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/21cf5c04-9e1b-465c-b341-3123eec01876)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d1fa4fe6-6923-4f57-bdf6-14a3c2db4ce8)  
./HW4/db_generation_lora_rank_16_lr_up_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a39d123f-10d5-4303-9225-9db48335bcb4)  
tensorboard --logdir=HW4/db_generation_lora_rank_16_lr_up_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 11. rank 8 lr 5e-3
Папка с визуализацией - ./HW4/db_generation_lora_rank_8_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/27cd4129-3f5b-4799-9abb-8daec56fdec8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/43926d21-c707-4951-be5d-d32234f301de)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/ca8adc7b-0622-4359-928b-625e2c64459c)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/029c4fa8-823d-4ae6-9b40-10e9de7c4be2)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/1249807f-914b-4ce3-9f34-5412ac778b39)  
./HW4/db_generation_lora_rank_8_lr_up_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/790e2b15-3221-40d0-b977-855b6e296299)  
tensorboard --logdir=HW4/db_generation_lora_rank_8_lr_up_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 12. rank 4 lr 5e-3
Папка с визуализацией - ./HW4/db_generation_lora_rank_4_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4a995197-fc94-455d-bce4-98c9d1976a22)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/60f36962-1803-40a8-967e-094fb9c010db)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/56729823-681f-49da-a6f2-00ec4c2e8d0c)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4534d98c-2287-46f8-b9f8-0d3b618852e6)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/09358021-8918-465a-b101-35945efccf51)  
./HW4/db_generation_lora_rank_4_lr_up_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/50a5d002-71a3-48fc-8537-8d6bd1a731e2)  
tensorboard --logdir=HW4/db_generation_lora_rank_4_lr_up_up/log_dir/
#### Вывод
Слишком большой rank и lr  
### 13. rank 2 lr 2e-4
Папка с визуализацией - ./HW4/db_generation_lora_rank_2/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f3d3da83-b387-4c06-9f9e-12cc2ba10014)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/898b7227-253a-4da3-947d-44f3d4feb9f0)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/765d1913-4c77-4bea-895d-261f6ee3503f)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/be14ffd7-9a3a-464b-be8b-84f065c657c1)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4b22fd36-f2c3-4b77-a213-220fb6c226bb)  
./HW4/db_generation_lora_rank_2/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4e3fb408-b046-43c8-9a2c-e10969ae1145)  
tensorboard --logdir=HW4/db_generation_lora_rank_2/log_dir/
#### Вывод
Слишком большой rank и lr  
### 14. rank 4 lr 2e-4
Папка с визуализацией - ./HW4/db_generation_lora_rank_4_lr_half/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/8fd5d40c-7832-4361-8e7f-5ab5f6e65bb2)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/38864da1-7875-4d3e-afc6-f987eb58265f)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/bf8061e9-26ba-4e59-ad2d-d86bb6fbbb03)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/f40b01c6-682a-4a3d-adcb-0b092251c284)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/56ae7e6d-1800-4bb3-84c8-274fcad09432)  
.HW4/db_generation_lora_rank_4_lr_half/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/205915db-c9b9-4f88-92ff-69116af046a2)  
tensorboard --logdir=HW4/db_generation_lora_rank_4_lr_half/log_dir/
#### Вывод
Слишком большой rank и lr
## Сравнить лучший чекпоинт Unet и Lora
## Генерация любого варианта Controlnet из ноутбука, для обученных Unet и Lora
