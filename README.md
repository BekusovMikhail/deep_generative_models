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
Папки с визуализацией - ./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 2. rank 16 lr 8e-4 
Папки с визуализацией - ./db_generation_lora_rank_16_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 3. rank 8 lr 8e-4
Папки с визуализацией - ./db_generation_lora_rank_8_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 4. rank 4 lr 8e-4
Папки с визуализацией - ./db_generation_lora_rank_4_lr_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился средний результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 5. rank 32 lr 8e-5
Папки с визуализацией - ./db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 6. rank 16 lr 8e-5
Папки с визуализацией - ./db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 7. rank 8 lr 8e-5
Папки с визуализацией - ./db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 8. rank 4 lr 8e-5
Папки с визуализацией - ./db_generation_lora_rank_32/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 9. rank 32 lr 8e-3
Папки с визуализацией - ./db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 10. rank 16 lr 8e-3
Папки с визуализацией - ./db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 11. rank 8 lr 5e-3
Папки с визуализацией - ./db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 12. rank 4 lr 5e-3
Папки с визуализацией - ./db_generation_lora_rank_32_lr_up_up/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 13. rank 2 lr 2e-4
Папки с визуализацией - ./db_generation_lora_rank_2/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr  
### 14. rank 4 lr 2e-4
Папки с визуализацией - ./db_generation_lora_rank_4_lr_half/inf_gen/base_model/768x1024
#### Результаты обучения
Получилось обучить нейросеть.  
Считаю, что получился $ результат
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
$IMAGE  
./db_generation_lora_rank_32_lr_up/inf_gen/base_model/768x1024
#### Метрики
Метрик в данном задании не имеется
#### График loss и Logging
$LOSS GPAPH  
#### Вывод
Слишком большой rank и lr
## Сравнить лучший чекпоинт Unet и Lora
## Генерация любого варианта Controlnet из ноутбука, для обученных Unet и Lora
