# base-date
Домашнее задание к занятию «Базы данных, их типы» -  Александр Романенко



Кейс
Крупная строительная компания, которая также занимается проектированием и девелопментом, решила создать правильную архитектуру для работы с данными. Ниже представлены задачи, которые необходимо решить для каждой предметной области.

Какие типы СУБД, на ваш взгляд, лучше всего подойдут для решения этих задач и почему?

1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков. СУБД должна гарантировать целостность и чёткую структуру данных.

1.1.* Хеширование стало занимать длительно время, какое API можно использовать для ускорения работы?

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM? СУБД должны быть гибкими и быстрыми.

1.2.* Можно ли эту задачу закрыть одной СУБД? И если да, то какой именно СУБД и какой реализацией?

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру.

1.3.* Можно ли под эту задачу использовать уже существующую СУБД из задач выше и если да, то как лучше это реализовать?

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.

1.4.* Можно ли к этой СУБД подключить отдел закупок или для них лучше сформировать свою СУБД в связке с СУБД логистов?

1.5.* Можно ли все перечисленные выше задачи решить, используя одну СУБД? Если да, то какую именно?

Приведите ответ в свободной форме.


# ОТВЕТЫ


### 1 .1 Реляционная СУБД
 ### 1 .1.* готовые API ,типа Google KMS.
 ### 1.2. CRM и Landing page - Реляционная СУБД
 ### 1.2.* PostgreSQL
### 1.3. Документо-ориентированные или Реляционные СУБД
### 1.3.* Реляционную СУБД, PostgreSQL
### 1.4.  Графовая СУБД (Neo4j)
### 1.5  PostgreSQL

## Задание 2. Транзакции
2.1  Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

2.1.* Какие действия должны произойти, если пополнение счёта телефона происходило бы через автоплатёж?

Приведите ответ в свободной форме.


### 2.1 -
1. **Проверка данных**  
   Система проверяет сумму, номер телефона и реквизиты карты.  
   **Логирование** записывается попытка транзакции 

2. **Резервирование средств**  
   Деньги временно блокируются на карте/кошельке.  
   **Логирование:** фиксируется факт резерва ID

3. **Запрос к оператору связи**  
   Система отправляет запрос оператору.  
   **Логирование:** сохраняется отметка о времени запроса и ответа оператора.  

4. **Подтверждение оператора**  
   Оператор проверяет данные и подтверждает возможность пополнения.  
   **Логирование:** записывается ответ оператора (успешно/ошибка)

5. **Завершение транзакции**  
   Списание денег с карты и зачисление на баланс телефона.  
   **Логирование:** финальный статус (успешно/отказ), время выполнения.  

6. **Уведомление пользователя**  
   Отправка SMS/email/push-уведомления.  
   **Логирование:** отметка о доставке уведомления.  


### 2.1* - ###  
В нужное пользователю время планировщик запускает действия 
1 Проверка подписки
2 Проверка баланса карты
3 Автоматическое выполнение шагов 1-6 из 2.1

## Задание 3. SQL vs NoSQL
3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

3.1.* Какие, на ваш взгляд, преимущества у NewSQL систем перед SQL и NoSQL.

Приведите ответ в свободной форме.


## 3.1 - ## 
1 Чёткочть структуры
2 Надёжность - при прирывании либо отмена либо выполнение, нету половинчатых результатов
3 Сложные запросы - например расчёт покупки и возврата товара в разное время
4 Перепроверка данных - запрет на запись
5 Стандартизация языка SQL  - можно работать PostgrsSQL  MySQL одинаковый синтаксис


## 3.1* - ##  
NewSQL - быстрее обробатывает данные , можно использовать и sql и nosql в одной системе, проще в управление , горизонтальная масшабируемость,автоматическое шардирование

## Задание 4. Кластеры ##
Необходимо производить большое количество вычислений при работе с огромным количеством данных, под эту задачу выделено 1000 машин.

На основе какого критерия будете выбирать тип СУБД и какая модель распределённых вычислений здесь справится лучше всего и почему?

** Приведите ответ в свободной форме.
Для 1000 серверов и больших данных нужна MPP-СУБД(Massively Parallel Processing) - например Greenplum
Делит данные и раскидывает их на все машины, чтобы не перегружать одну.
Считает параллельно — каждая машина обрабатывает свой кусок задачи **





 
