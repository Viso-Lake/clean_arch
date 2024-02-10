# Шаблон чистой архитектуры банка "Арванд"

Пример структуры проекта, реализующего чистую архитектуру.

### Использование шаблона:

1. Создайте форк этого репозитория, нажав на кнопку "**Fork**".

2. Клонируйте ваш форк в локальное хранилище на вашем компьютере:

```
git clone https://github.com/arvand_tech/clean_arch.git
```

3. Перейдите в склонированную директорию:

```
cd clean_arch
```

4. Создайте свой собственный репозиторий в вашем аккаунте:

```
git create ВАШ_НИКНЕЙМ/example_service
```

5. Установите удаленный upstream репозиторий (замените "НАЗВАНИЕ ПРОЕКТА"), чтобы получать обновления из оригинального репозитория:

```
git remote add upstream https://github.com/НАЗВАНИЕ_ПРОЕКТ/example_service.git
```

# ИЛИ

1. Нажмите на `Use this template`,
2. Выберите `Create a new repository`
3. Укажите название
4. Создайте новый репозиторий
5. Следуйте инструкции

## Структура проекта:

- **cmd**: Содержит точки входа для приложения.

  - **app**: Основной входной файл для приложения.
    - app.go - Создание и настройка объекта app
    - main.go - Входной файл для приложения, использующий объект app
  - **console**: Входной файл для консольного приложения (если есть).
    - main.go

- **pkg**: Все, что разрешено импортировать снаружи.

  - **api**:
    - **http**: Все, что касается REST API.
      - **middlewares**: Middleware для HTTP API.
        - middleware.go
      - **handlers**: Обработчики запросов HTTP.
        - example.go
      - **routes**: Определение маршрутов HTTP.
        - example.go
    - **grpc**:
      - **clients**: Клиенты для вызова методов gRPC из других сервисов.
        - example-client.go
      - **pb**: Автогенерация proto данных в pb и grpc_pb.
        - example.pb.go
        - example.grpc_pb.go
      - **proto**: Описываемая структура для передачи данных.
        - example.proto
      - **handler**: Сервер обработчиков gRPC (handler).
        - example-handler.go

- **internal**: Все, что ЗАПРЕЩАЕМ импортировать снаружи.

  - **database**:
    - database.go: Конфигурация БД и DB_CONNECT.
    - **migrations**: Миграции и автомиграции БД, ORM, SQL и другие.
      - automigrate.go
    - **seeders**: Сиды для заполнения базы после автомиграции.
      - seed.go
  - **domain**: Компоненты, связанные с доменной логикой.
    - **dto**: Data Transfer Objects для взаимодействия между слоями.
      - example-dto.go
    - **entities**: Сущности, представляющие предметную область.
      - example-entity.go
    - **repositories**: Репозитории для взаимодействия с хранилищем данных.
      - example-repository.go
    - **usecases**: Use Cases, описывающие бизнес-логику.
      - example-usecase.go

- **utils**: Общие утилиты и функции.

- **deployments**: Все, что касается CI/CD, контейнеров, деплоя и кластера.

  - **k8s**:
    - ...: Конфигурации Kubernetes.
  - **docker**: Конфигурации Docker.
    - Dockerfile
    - docker-compose.yml
    - .dockerignore
  - **ci**: Конфигурации CI/CD.
    - .gitlab-ci.yml
  - **env**: Environments.
    - .env.local
    - .env.prod

- **tests**: Тесты для компонентов.

  - **mocks**:
    - example_repository_mock.go
  - **unit**:
    - example_service_test.go
  - **integration**:
    - example_integration_test.go

- **scripts**: Скрипты для автоматизации задач.

- **docs**: Документация проекта.

  - api.swagger.yml

- **.gitignore**: Файл для игнорирования файлов и папок при использовании системы контроля версий Git.

- **Makefile**: Файл для управления задачами с помощью утилиты make.

- **README.md**: Файл с описанием проекта.
