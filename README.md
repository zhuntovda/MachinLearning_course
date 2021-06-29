# MachinLearning_course

Итоговый проект курса "Машинное обучение в бизнесе"

Стек:

ML: sklearn, pandas, numpy
API: flask
Данные: с kaggle - https://www.kaggle.com/uciml/human-activity-recognition-with-smartphones

Задача: предсказать по показаниям датчиков мобильного устройства текущее действие человека.

Классификация состоит из 6 видов активности:

  |  ТИП               | Кол-во |
  -------------------------------
  |LAYING              |  1407  |
  |STANDING            |  1374  |
  |SITTING             |  1286  |
  |WALKING             |  1226  |
  |WALKING_UPSTAIRS    |  1073  |
  |WALKING_DOWNSTAIRS  |   986  |

Используемется 561 измерение передаваемый с датчиков мобидьного устройства разных 10 типов

Преобразования признаков: tfidf
Из признаков исключены идентификаторы пользователей

Модель: xgboost

### Клонируем репозиторий и создаем образ
```
$ git clone https://github.com/fimochka-sudo/GB_docker_flask_example.git
$ cd GB_docker_flask_example
$ docker build -t fimochka/gb_docker_flask_example .
```

### Запускаем контейнер

Здесь Вам нужно создать каталог локально и сохранить туда предобученную модель (<your_local_path_to_pretrained_models> нужно заменить на полный путь к этому каталогу)
```
$ docker run -d -p 8180:8180 -p 8181:8181 -v <your_local_path_to_pretrained_models>:/app/app/models fimochka/gb_docker_flask_example
```

### Переходим на localhost:8181
