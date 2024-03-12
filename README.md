# Курсовая работа «E-Commerce». Профессия «Специалист по информационной безопасности»

## Описание

Компания Y предоставляет комплексное веб-приложение в сфере электронной коммерции `Necommerce`. Компания недавно столкнулась с массовой утечкой данных о своих пользователях и их покупках. «Брешь», через которую произошла утечка, вроде как устранили.

Саму разработку приложения компания Y заказывает у подрядчика — фирмы-разработчика.

Своих специалистов по информационной безопасности у компании Y нет, поэтому вас пригласили провести комплексный анализ процесса разработки и протестировать на наличие других веб-уязвимостей. Детали по найденным и исправленным уязвимостям не дали, так как вы профессионал и должны проверить всё с начала.

Разработчики со стороны подрядчика также максимально пошли вам на встречу и предоставили исчерпывающую информацию о приложении — две ссылки на репозитории с кодом:
* [Frontend](https://github.com/netology-code/necommerce-frontend).
* [Backend](https://github.com/netology-code/necommerce-backend).

**По словам разработчиков:**
1. Вся разработка ведётся в приватных репозиториях в GitHub. *Это легенда, для удобства мы вам дали открытые репозитории*.

2. Весь код, а также зависимости и контейнеры, регулярно  проходят проверку открытыми инструментами:
    * [Dependabot](https://dependabot.com).
    * [Detekt](https://detekt.github.io/detekt/).
    * [Snyk](https://snyk.io/) и т. д.
    
3. Сам код покрыт автоматическими тестами, включая проверку механизмов безопасности (отработка неверных логинов и паролей), которые регулярно прогоняются при каждом push в репозиторий.

4. Разработчики прекрасно знакомы с `OWASP Top 10`, а некоторые даже с `ASVS` и `WSTG`.

5. Они придерживаются строгих правил разработки и не разрешают отправлять `push` в `master` без соответствующего `Code Review` как минимум двух человек и прохождения автоматизированных проверок.

6. После прохождения всех проверок автоматически собираются образы `Docker` и публикуются в `GitHub Container Registry` для дальнейшего разворачивания в Production.

Отчёты этих инструментов скрыты из публичного доступа. При желании вы можете `Fork`'нуть репозиторий и самостоятельно настроить репозиторий, либо обратиться к руководителю курса, чтобы он вас добавил временно в репозиторий для просмотра настроек инструментов.

## Инструкция по запуску

Используйте файл `docker compose`:
```
version: '3.7'
services:
  backend:
    image: ghcr.io/netology-code/necommerce-backend
    ports:
      - 9999:9999
  frontend:
    image: ghcr.io/netology-code/necommerce-frontend
    environment:
      - API=http://backend:9999
      - MEDIA=http://backend:9999
    ports:
      - 8888:80
    depends_on:
      - backend
```

## Задача

**Ваша ключевая задача** — провести комплексное исследование функционирующего приложения и исходных кодов. Обратите внимание на код приложения, всё ли в порядке с зависимостями, верно ли собираются контейнеры и т. д.

В задачу не закладывается требование выучить используемые в системе языки программирования. Достаточно знания английского языка и умения гуглить важные моменты, например, как в том или ином языке работать с генерацией случайного набора данных, или что такое `CORS`, `CSRF` и т. д.

**Задача разделена на 3 этапа:**
1. Планирование.
2. Выполнение работы.
3. Подготовка отчётных документов по итогам.

### Планирование

После начала работы над дипломом в течение 3 рабочих дней вы должны сдать руководителю план работ, в котором описано:

* что вы будете проверять;
* как вы будете это проверять: инструменты, подходы, используемые нормативные документы, стандарты или руководства;
* интервальная оценка с учётом рисков в часах;
* план сдачи работ: когда будут выполнены работы и готов отчёт.

Руководитель выступает в роли представителя по стороны Заказчика, поэтому именно он определяет правила выполнения и сдачи работ. Если его требования расходятся с указанными в этом документе, то приоритет имеют требования руководителя.

Руководитель может скорректировать ваш план работ, указав:

* какие работы делать не нужно;
* какие работы нужно сделать дополнительно.

### Выполнение работ

На этом этапе вы выполняете работу. Можете консультироваться с руководителем по поводу вопросов, требующих уточнения. Например: является ли данная функциональность запланированной или нет.

### Отчётные документы по итогам тестирования

В качестве отчётных документов прикладываются:
1. Документ (doc, odf, pdf или issue в GitHub) со скриншотами и описанием обнаруженных проблем, если они есть.
2. Документ с рекомендациями улучшения процесса, кода, подходов, применения новых практик и т. д.

## О документах

Если просим вас подготовить документ, достаточно прислать текст объёмом страницы А4. Пишите только то, что действительно важно. 

## Критерии приёма курсовой работы

1. Подготовлен отчёт.
2. Подготовлены рекомендации по улучшению процесса.
# Comprehensive-study-of-a-functioning-application-and-source-codes
