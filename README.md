## Задача 1: Обеспечить разработку

Я бы предложил связку Gitlab и Jenkins.

Обоснование:
GitLab — это сервис для хранения кода, управления версиями и совместной разработки программного обеспечения. Работа сервиса основана на популярной системе контроля версий Git, что является плюсом с моей точки зрения.
Одни из возможностей GitLab:
1. Управление публичными и приватными git-репозиториями.
2. Управление пользователями и группами, правами доступа к git-репозиториям.
3. Отслеживание ошибок, сборка, анализ кода.
4. Интеграция с разными CI-системами CI (Jenkins и т. п.), организация самостоятельного процесса CI посредством встроенных средств, что тоже является большим плюсом.
5. Возможность работать с GitLab  по-разному: через командную строку, Web IDE (встроенный IDE для работы в браузере), так и через сторонние Git-клиенты.
Вывод : Gitlab практически полностью удовлетворяет условиям CI/CD, контроль версий и у него есть свой Docker Regestry, а также организовано  хранение артефактов. Jenkins,  как один из популярнейших средств автоматизированного создания, тестирования и развертывания программного обеспечения, хорошая развернутая документация. В случае столь широкого ТЗ можно использовать И GitHub + Dockerhub + Sentry
Jenkins является одним из популярнейших средств автоматизированного создания, тестирования и развертывания программного обеспечения. Он имеет хорошую и  развернутую документацию. Из-за этого я остановил свой выбор на нём.

## Задача 2: Логи

В зависимости от размеров проекта можно использовать ELK. С моей точки зрения - это хороший выбор инструментария.
Обоснование :
1. ELK используется для централизованного логирования (ведения журналов) с разных серверов.
2. ELK позволяет надёжно, быстро  и безопасно получать данные из любого источника во всех форматах и работать с этими данными.
3. ELK осуществляет поиск по ним, анализизирует и визуализирует их в режиме реального времени.
Вывод : Все эти факторы являются большими плюсами, при выборе этого инструмента. 

В случае, если проект маленький и достаточно простой, то можно использовать более простые инструменты, к примеру - Syslog-Ng.
Обоснование :

Syslog-ng — это бесплатная и открытая реализация протокола syslog для Unix и Unix-подобных систем.
1. Расширяет оригинальную модель Syslogd контентной фильтрацией, гибкими опциями конфигурации и добавляет важные функции, например использование TCP для транспорта. 
2. Также обладает дополнительными функциями, включая сверхбыстрый текстовый поиск, унифицированный поиск, контентную сигнализацию и поддержку первого уровня.
3. Вывод : хороший и бесплатный вариант для небольшого и относительно простого проекта. 

## Задача 3: Мониторинг

Мониторинг зависит от системы на которой установлены микросервисы: 
A. Если у нас микросервисы в облаке (в т.ч. и On-prem) то лучше использовать встроенный мониторинг.
Преимущества on-premise:
1. Контроль.Организации имеют полный контроль над своими данными, оборудованием и программным обеспечением. 
2. Настройка. Поскольку программное обеспечение устанавливается непосредственно на личном сервере клиента, оно может быть тщательно настроено под специфические потребности бизнеса. 
3. Однократные затраты. Во многих случаях покупка лицензии на программное обеспечение on-prem предполагает однократные затраты, в отличие от подписок на облачные сервисы, где платежи производятся регулярно. 
Недостатки on-premise:
1. Начальные затраты. Высокие начальные затраты на приобретение серверов, оборудования и лицензий на программное обеспечение, а также расходы на создание и поддержку IT-инфраструктуры. 
2. Обслуживание и поддержка. Организация самостоятельно несёт ответственность за обслуживание, обновления, резервное копирование и восстановление после сбоев, что требует наличия квалифицированных IT-специалистов. 3
Масштабируемость. Увеличение масштаба инфраструктуры для поддержки роста или изменений в бизнесе может быть сложным и дорогостоящим. 
3. Неподвижность. Физическое размещение инфраструктуры ограничивает доступность и мобильность, в отличие от облачных решений, которые доступны отовсюду, где есть интернет. 
Вывод :
On-premise подходит компаниям, которым в первую очередь важна безопасность и кастомизация. Выбор между решениями всегда зависит от индивидуальных требований бизнеса.

B. Если мы имеем отдельные контейнеры, то вероятно, что подошли бы Prometheus и Grafana. Этохороший выбор - большое коммьюнити, большое количество кейсов и мануалов. Есть возможность тонко настраивать метрики под собственные нужды.
Обоснование :
Grafana — бесплатная программная система визуализации данных (есть платная версия, обладающая дополнительными возможнотями), ориентированная на данные систем ИТ-мониторинга. Она реализована как веб-приложение  с диаграммами, графиками, таблицами и предупреждениями, что является плюсом с моей точки зрения.
Основные характеристики платформы:
1. Взаимодействие с любыми информационными источниками, в том числе с базами данных, сервисами мониторинга, статистическими материалами.
2. Имеет настройки дашбордов, позволяющие показывать нужные сведения в удобном для пользователя виде. 
3. Масштабируемость и поддержка множества плагинов, что делает возможным интеграцию с другими системами и добавление новых функций.
4. Наличие службы уведомлений и оповещений, что позволяет пользователям оперативно реагировать на изменения в массивах данных или в статусе системы. 
5. Наличие средств для верификации и авторизации пользователей, что обеспечивает безопасный доступ к информации, что является несомненным достоинством.
6. Grafana можно установить на все популярные операционные системы, включая Windows и Linux во всех модификациях (версиях). 

