# Sampling в латентном пространстве StyleGAN
## Датасет  
https://www.kaggle.com/datasets/dansbecker/5-celebrity-faces-dataset/data?select=train  
## Подготовительные работы
Encoder, оптимизация, лоссы и тд брал стандартные из ноубука
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/de1270e5-cf85-420c-973d-5868027b8c35)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/c077cb9c-164d-4e54-9a90-eca9d15eb584)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d444a10a-fb10-4504-beb3-fd47c7fe3d4e)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/b41f5b0f-3d45-403d-876e-8e4701357021)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/57b1e3b4-077f-408b-aef3-78a2c5f1d0a8)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/a3f9e2eb-37bd-473b-9fc9-8d14521cec8e)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/aa402368-a9f9-4ebe-b26a-0156c1d4d550)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fdae3974-ab78-4426-b036-775fbd795f61)  
## Latent space  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/7c5d8e91-2560-4348-892a-cd5200504a35)
## Style trasfer
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/5792850d-6687-4442-89fc-afe0e98f0f73)
Попробовал самый простой метод перемешивания частей латентных векторов
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/4a00e0f1-a824-4c67-9289-2f3d947bfcb6)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/aafbdf79-3a30-4d94-9078-85af60611f7b)  
Брал indeces = [7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17] при psi=0.0  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/eb1ab136-9641-4106-8a79-fc0252c46ca7)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/7d2173d9-607c-4b2d-9c6f-96125b4ebb89)
Брал indeces = [7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17] при psi=0.0  
Брал indeces = [ 9, 10, 11, 12, 13, ]] при psi=-0.5  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/d3a30ffd-7b6a-4d38-9d79-207092cf229d)  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/5918ae5b-0f84-4c39-8f4e-93079c3ba7ff)  
## Expression Transfer
Smyle:  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/249046d6-d587-4575-b5c1-d07ebc2dc124)  
Surprise:  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/65d594ad-eb96-40f1-81ee-1faedb538be1)
Age:  
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/85f6c429-31af-48ea-a687-aa69f1e2989d)

## Face swap
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/ae053c34-5f7a-4d90-9bdc-31038eba4e85)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/5d7f668c-cd8e-4170-bb63-ecd2f001192b)
![image](https://github.com/BekusovMikhail/deep_generative_models/assets/63633043/fe847fb2-821b-434e-b1ef-ad8ccd75f731)
