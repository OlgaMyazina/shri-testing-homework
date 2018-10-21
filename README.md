### комментарий для интеграционного тестирования:

вынесла REPO в конфиг (`config/default.json`) - для интеграционного тестирования можно прописать

```
{
  "path": "./test/integrationTestRepo"
}
```

по-умолчанию:

```
"path": "."
```

### Логические блоки системы и их сценарии:

Приложение состоит из следующих частей:

- Отображение истории
  - Отображение хлебных крошек
  - Отображение истории коммитов
  - Форматированный вид истории коммитов
- Отображение папок
  - Отображение хлебных крошек до вложенных папок
  - Отображение файловой структуры коммита
  - Отображение файловой структуры коммита по указанному пути
- Отображение содержимого файла
  - Отображение хлебных крошек
  - Формирование url до файла
  - Отображение файла

Тестирование этих сценариев описано в файлах:

- Проверка навигации по ссылкам:

  - Формируется url к папке до элемента и от заданного элемента по заданной вложенности
  - Формируется url к папке до указанного элемента
  - Формируется url до файла от при указании элемента и относительного пути до файла
  - Хлебные крошки:
    - Первый элемент - история
    - Содержимое коммита - HISTORY/ROOT
    - Содержимое коммита и пустой путь вложенности - HISTORY/ROOT
    - У последнего элемента должен быть пустой адрес
    - Отображаются хлебные крошки вложенных папок
      - отображаются хлебные крошки первого уровня вложенности
      - отображаются хлебные крошки второго уровня вложенности

- Проверка работы с git:

  - Отображается история
  - Форматирование истории (указание страниц = 2 и сообщений в выводе = 3)
  - Отображается файловая структура коммита
  - Отображается файловая структура коммита по указанному пути
  - Отображается содержимое файла

# Домашнее задание: автотесты

Вам дано приложение на JavaScript и нужно написать для него автотесты: интеграционные тесты на интерфейс и модульные тесты на серверную часть.

## Предметная область

Приложение отображает в браузере информацию из git репозитория: список коммитов, файловую систему для выбранного коммита, содержимое выбранного файла (поддерживаются только текстовые форматы). Для удобства навигации на каджой странице отображаются "хлебные крошки".

## Как запустить

```sh
git clone git@github.com:dima117/shri-testing-homework.git
cd shri-testing-homework.git
npm i
npm start
```

## Интеграционные тесты

Сценарии для интеграционных тестов

- на всех страницах (история коммитов, просмотр файловой системы, просмотр содержимого файла) правильно отображается их содержимое;
- правильно работают переходы по страницам
  - из списка коммитов на список файлов
  - из списка файлов во вложенную папку
  - из списка файлов на страницу отдельного файла
  - переходы по хлебным крошкам

## Модульные тесты

- нужно добавить в README список логических блоков системы и их сценариев
- для каждого блока нужно написать модульные тесты
- если необходимо, выполните рефакторинг, чтобы реорганизовать логические блоки или добавить точки расширения
