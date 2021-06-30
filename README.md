# MachinLearning_course

Итоговый проект курса "Машинное обучение в бизнесе"

Стек:

ML: sklearn, pandas, numpy
API: flask
Данные: с kaggle - https://www.kaggle.com/uciml/human-activity-recognition-with-smartphones

Задача: определить по показаниям датчиков мобильного устройства текущее действие человека.

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
Из измерений исключены идентификаторы пользователей, так как он не должен влиять на расчет модели

Модель: xgboost

в формате .ipynb в папке app\models лежат файлы fit.ipynb (обучение модели) и predictions.ipynb (проверка модели)

в проекте разработана серверная часть принимающая данные, клиенской части нет, так как требуется вводить вручную 561 показатель.
все показатели играют важную роль в расчете, так как показывают данные положения 10 основных измерений.

f1_score на тесте равен 0.9389209365456397
основной процент ошибки (68%) появляется при предсказании SITTING  STANDING, что объясняется тем, что оба положения тела в покое.

### Клонируем репозиторий и создаем образ
```
$ git clone https://github.com/zhuntovda/MachinLearning_course.git
$ cd GB_docker_flask_example
$ docker build -t fimochka/gb_docker_flask_example .
```

### Запускаем контейнер

Здесь Вам нужно создать каталог локально и сохранить туда предобученную модель (<your_local_path_to_pretrained_models> нужно заменить на полный путь к этому каталогу)
```
$ docker run -d -p 8180:8180 -p 8181:8181 -v <your_local_path_to_pretrained_models>:/app/app/models fimochka/gb_docker_flask_example
```

### Переходим на localhost:8181
