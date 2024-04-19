Привет.

Мы хотим найти классного стажера и готовы к тому, что ты что-то не умеешь, но нам важно, чтобы ты не боялся задач, был проактивным и самостоятельным.

#### Что нужно сделать

1. Тестируем продукт
   Тестируемый продукт: https://pay-test.raif.ru/pay/configurator/ Это сервис используемый менеджерами для демонстрации возможностей кастомизации формы и генерации кода для интеграции. Подробнее в документации: https://pay.raif.ru/doc/ecom.html

**Задание:**
На каких уровнях и что будете тестировать, конкретно по пунктам?
Придумать 5 тестовых сценариев и реализовать их.
Для каждого сценария придумай дефект и опиши дефект для разработчиков. 
   
2. Тестируем API
   Есть моделька ендпоинта в yaml файле
```
paths:
  '/mcp/rp-terminal/v1/clients/{cnum}/terminals':
    get:
      tags:
        - terminals
      summary: Возвращает список терминалов клиента
      description: Возвращает список терминалов клиента по cnum, на которые можно подключить СБП (TRADE, UNIPOS, Stand-Alone терминалы)
      operationId: getTerminalsByCnum
      parameters:
        - name: cnum
          in: path
          description: Номер клиента, терминалы которого нужно найти
          required: true
          schema:
            type: string
        - name: sbpAvailable
          in: query
          description: Поиск только среди терминалов, на которые можно подключить СБП
          required: false
          schema:
            type: boolean
            default: true
      responses:
        '200':
          description: Запрос обработан успешно
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/DeviceTerminalDto'
        '403':
          description: Ошибка авторизации
        '404':
          description: Клиент с таким cnum не найден
        '500':
          description: Внутренняя ошибка сервиса
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
              example: {
                "code": "INTERNAL_SERVER_ERROR",
                "message": "string",
                "traceId": "string"
              }
```
**Задание:**
Какими тестами будем покрывать?
Реализуйте их.


В идеале опубликовать результаты на **github**
