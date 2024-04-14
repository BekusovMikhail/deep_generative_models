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
## Скачать предобученный чекпоинт SD1.5
Обучено
### Результаты обучения

#### График loss
Прошу прощения, забыл выставить, так как создавал новый conda env, не установил tensorboard и послен обучения получил
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/aba8a89b-4aa7-4e6e-a806-72a0271ffc17)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d9b96861-9e4a-4d04-a442-f22afabf9c1b)  
#### Графика метрик в данном задании не имеется
#### 5-10 примеров работы нейросети
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/9cd64db8-b611-4b90-80f3-39b26055a856)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4b57a002-8061-4f08-b30f-3e3bc83a0a5e)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/120d82b4-b48e-47ef-90fd-ff77e012e115)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/353d6fa3-60b4-470d-a390-6c7e16b1f078)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/64d7ecbf-f485-44cc-ab46-e9b40f97d9f7)  
Также Лежат в папке arthas_gen_unet  
#### Метрики
Метрик в данном задании не имеется
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
