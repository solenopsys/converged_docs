# Каталог модулей

Этот указатель сгенерирован из реестра модулей Converged. Каждая запись ссылается на документацию, принадлежащую этому модулю; зависимости взяты из манифеста пакета workspace, а принадлежность к решениям — из `modules/solutions`.

## Доступ и безопасность

### [lm-secrets](/en/docs/modules/lm-secrets)

Предоставляет сервисный контракт для хранения, получения и удаления именованных секретных значений.

- Прямые зависимости: нет
- Решения: нет

### [rp-access](/en/docs/modules/rp-access)

rp-access — репозиторий в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [rp-auth](/en/docs/modules/rp-auth)

rp-auth — репозиторий в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [rp-environment](/en/docs/modules/rp-environment)

Хранит и извлекает конфигурацию окружения, связанную с пользователями платформы.

- Прямые зависимости: нет
- Решения: `security`

### [rp-identity](/en/docs/modules/rp-identity)

rp-identity — репозиторий в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [rp-oauth](/en/docs/modules/rp-oauth)

rp-oauth — репозиторий в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-auth](/en/docs/modules/sf-auth)

sf-auth — surface в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [sf-secrets](/en/docs/modules/sf-secrets)

Предоставляет административный интерфейс для создания, просмотра, обновления и удаления именованных секретных записей.

- Прямые зависимости: нет
- Решения: нет

### [sf-team](/en/docs/modules/sf-team)

sf-team — surface в домене sequrity. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

## ИИ и агенты

### [rp-assistant](/en/docs/modules/rp-assistant)

rp-assistant — репозиторий в домене ai. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `ai`

### [rp-contexts](/en/docs/modules/rp-contexts)

Обеспечивает хранение и получение именованных ИИ-контекстов, включая их языковые варианты.

- Прямые зависимости: нет
- Решения: `ai`

### [sf-assistants](/en/docs/modules/sf-assistants)

sf-assistants — surface в домене ai. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: `sf-requests`
- Решения: `ai`

### [sf-contexts](/en/docs/modules/sf-contexts)

Предоставляет ИИ-рабочую область для просмотра списка, редактирования и сохранения именованных контекстов на нескольких языках.

- Прямые зависимости: нет
- Решения: `ai`

## Аналитика и телеметрия

### [rp-counters](/en/docs/modules/rp-counters)

Хранит внешние конфигурации счетчиков аналитики для каждого тенанта (tracking ids, head-сниппеты) для SSR-инъекции.

- Прямые зависимости: нет
- Решения: `analitycs`

### [rp-dashboard](/en/docs/modules/rp-dashboard)

Хранит закрепленные пользователем индикаторы личной панели: какие виджеты закреплены, их порядок и метаданные отображения.

- Прямые зависимости: нет
- Решения: `analitycs`

### [rp-logs](/en/docs/modules/rp-logs)

rp-logs — репозиторий в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [rp-telemetry](/en/docs/modules/rp-telemetry)

rp-telemetry — репозиторий в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [rp-usage](/en/docs/modules/rp-usage)

rp-usage — репозиторий в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [sf-dasboards](/en/docs/modules/sf-dasboards)

sf-dasboards — surface в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [sf-logs](/en/docs/modules/sf-logs)

sf-logs — surface в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [sf-telemetry](/en/docs/modules/sf-telemetry)

sf-telemetry — surface в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

### [sf-usage](/en/docs/modules/sf-usage)

sf-usage — surface в домене analytics. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `analitycs`

## Автоматизация и оркестрация

### [lm-kubernetes](/en/docs/modules/lm-kubernetes)

Интегрирует автоматизацию платформы с ресурсами Kubernetes через выделенный клиент и сервисный контракт.

- Прямые зависимости: нет
- Решения: нет

### [rp-dag](/en/docs/modules/rp-dag)

rp-dag — репозиторий в домене automation. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `automation`, `requests`

### [rp-sheduller](/en/docs/modules/rp-sheduller)

rp-sheduller — репозиторий в домене automation. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `automation`

### [rp-webhooks](/en/docs/modules/rp-webhooks)

rp-webhooks — репозиторий в домене automation. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `automation`

### [sf-automation](/en/docs/modules/sf-automation)

sf-automation — surface в домене automation. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `automation`

## Бизнес-домен

### [rp-billing](/en/docs/modules/rp-billing)

rp-billing — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `billing`

### [rp-equipment](/en/docs/modules/rp-equipment)

rp-equipment — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [rp-events](/en/docs/modules/rp-events)

Обеспечивает создание, хранение и получение бизнес-событий.

- Прямые зависимости: нет
- Решения: `production`

### [rp-finance](/en/docs/modules/rp-finance)

Обеспечивает финансовые операции для транзакций, сводок за период, денежного потока, дебиторской и кредиторской задолженности.

- Прямые зависимости: нет
- Решения: нет

### [rp-invoices](/en/docs/modules/rp-invoices)

rp-invoices — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `billing`

### [rp-metering](/en/docs/modules/rp-metering)

rp-metering — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `billing`

### [rp-orders](/en/docs/modules/rp-orders)

Предоставляет сервисный контракт для создания, обновления, просмотра списка и отслеживания бизнес-заказов.

- Прямые зависимости: нет
- Решения: `production`

### [rp-requests](/en/docs/modules/rp-requests)

rp-requests — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [rp-reviews](/en/docs/modules/rp-reviews)

rp-reviews — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [rp-sales](/en/docs/modules/rp-sales)

rp-sales — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [rp-staff](/en/docs/modules/rp-staff)

rp-staff — репозиторий в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [sf-equipment](/en/docs/modules/sf-equipment)

sf-equipment — surface в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [sf-orders](/en/docs/modules/sf-orders)

Предоставляет интерфейс продаж для списков заказов и заявок, деталей заказов, фильтрации по статусу и операционных панелей.

- Прямые зависимости: нет
- Решения: `production`

### [sf-requests](/en/docs/modules/sf-requests)

sf-requests — surface в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [sf-reviews](/en/docs/modules/sf-reviews)

sf-reviews — surface в домене business. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

## Коммуникации

### [rp-calls](/en/docs/modules/rp-calls)

rp-calls — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `ai`

### [rp-chats](/en/docs/modules/rp-chats)

rp-chats — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [rp-community](/en/docs/modules/rp-community)

rp-community — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [rp-notify](/en/docs/modules/rp-notify)

rp-notify — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [rp-resonus](/en/docs/modules/rp-resonus)

Предоставляет конфигурацию связи для управляемых телефонных номеров и настроек LLM-шлюза.

- Прямые зависимости: нет
- Решения: нет

### [rp-support](/en/docs/modules/rp-support)

rp-support — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [rp-threads](/en/docs/modules/rp-threads)

rp-threads — репозиторий в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `ai`, `communications`

### [sf-calls](/en/docs/modules/sf-calls)

sf-calls — surface в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `ai`

### [sf-chats](/en/docs/modules/sf-chats)

sf-chats — surface в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [sf-community](/en/docs/modules/sf-community)

sf-community — surface в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [sf-support](/en/docs/modules/sf-support)

sf-support — surface в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`

### [sf-threads](/en/docs/modules/sf-threads)

sf-threads — surface в домене communications. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `ai`, `communications`

## Контент и документы

### [rp-classifier](/en/docs/modules/rp-classifier)

rp-classifier — репозиторий в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [rp-galery](/en/docs/modules/rp-galery)

rp-galery — репозиторий в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `content`

### [rp-markdown](/en/docs/modules/rp-markdown)

rp-markdown — репозиторий в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `content`

### [rp-scripts](/en/docs/modules/rp-scripts)

Обеспечивает операции хранения файлов скриптов, включая чтение, сохранение, хеширование и удаление.

- Прямые зависимости: нет
- Решения: нет

### [rp-static](/en/docs/modules/rp-static)

Предоставляет сервисный контракт для статического контента и метаданных SSR-кеша.

- Прямые зависимости: нет
- Решения: нет

### [rp-struct](/en/docs/modules/rp-struct)

rp-struct — репозиторий в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `content`

### [sf-classifier](/en/docs/modules/sf-classifier)

Предоставляет интерфейс классификатора для навигации по сущностям, сопоставлениям и древовидным структурам.

- Прямые зависимости: нет
- Решения: нет

### [sf-docs](/en/docs/modules/sf-docs)

sf-docs — surface в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-galery](/en/docs/modules/sf-galery)

sf-galery — surface в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-landing](/en/docs/modules/sf-landing)

sf-landing — surface в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-markdown](/en/docs/modules/sf-markdown)

sf-markdown — surface в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-static](/en/docs/modules/sf-static)

Предоставляет операционный интерфейс для проверки и очистки записей статического SSR-кеша.

- Прямые зависимости: нет
- Решения: нет

### [sf-struct](/en/docs/modules/sf-struct)

sf-struct — surface в домене content. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

## Файлы и хранилище

### [lm-compressors](/en/docs/modules/lm-compressors)

lm-compressors — lambda в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [rp-dumps](/en/docs/modules/rp-dumps)

rp-dumps — репозиторий в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [rp-files](/en/docs/modules/rp-files)

rp-files — репозиторий в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `communications`, `requests`

### [rp-store](/en/docs/modules/rp-store)

rp-store — репозиторий в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [sf-dumps](/en/docs/modules/sf-dumps)

sf-dumps — surface в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [sf-files](/en/docs/modules/sf-files)

sf-files — surface в домене data. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

## Провайдеры доставки сообщений

### [lm-lemonsqueezy](/en/docs/modules/lm-lemonsqueezy)

lm-lemonsqueezy — lambda в домене providers. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `billing`

### [lm-push](/en/docs/modules/lm-push)

lm-push — lambda в домене providers. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [lm-ses](/en/docs/modules/lm-ses)

lm-ses — lambda в домене providers. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `security`

### [lm-sms](/en/docs/modules/lm-sms)

lm-sms — lambda в домене providers. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [lm-smtp](/en/docs/modules/lm-smtp)

lm-smtp — lambda в домене providers. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

## Конвертация моделей

### [lm-modelconvertor](/en/docs/modules/lm-modelconvertor)

lm-modelconvertor — lambda в домене convertors. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

## Рабочие процессы

### [wf-dialogue-summary](/en/docs/modules/wf-dialogue-summary)

Суммирует необработанные диалоги чатов и звонков с помощью LLM, затем сохраняет заголовки, описания и классификацию шума.

- Прямые зависимости: нет
- Решения: нет

### [wf-equipment-incident](/en/docs/modules/wf-equipment-incident)

wf-equipment-incident — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [wf-file-analyze](/en/docs/modules/wf-file-analyze)

Анализирует один сохраненный неархивный файл, создавая превью моделей и оценки для ЧПУ или 3D-печати, когда это поддерживается.

- Прямые зависимости: нет
- Решения: `requests`

### [wf-file-unpack](/en/docs/modules/wf-file-unpack)

Разворачивает один загруженный архив в коллекцию сохраненных файлов для последующего анализа.

- Прямые зависимости: нет
- Решения: `requests`

### [wf-files-analyze](/en/docs/modules/wf-files-analyze)

wf-files-analyze — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [wf-files-process](/en/docs/modules/wf-files-process)

Обрабатывает загруженные файлы пакетами: разворачивает архивы, определяет файлы моделей и создает из них производственную заявку.

- Прямые зависимости: нет
- Решения: `requests`

### [wf-order-review-followup](/en/docs/modules/wf-order-review-followup)

wf-order-review-followup — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [wf-order-review-request](/en/docs/modules/wf-order-review-request)

wf-order-review-request — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [wf-payment-settle](/en/docs/modules/wf-payment-settle)

wf-payment-settle — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `billing`

### [wf-request-analyze](/en/docs/modules/wf-request-analyze)

wf-request-analyze — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `requests`

### [wf-request-to-order](/en/docs/modules/wf-request-to-order)

wf-request-to-order — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

### [wf-sales-import](/en/docs/modules/wf-sales-import)

wf-sales-import — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [wf-sales-review-outreach](/en/docs/modules/wf-sales-review-outreach)

wf-sales-review-outreach — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: нет

### [wf-team-invite](/en/docs/modules/wf-team-invite)

wf-team-invite — workflow в домене platform. Его подробное назначение поддерживается вместе с исходным кодом модуля.

- Прямые зависимости: нет
- Решения: `production`

## Зависимости решений

- `ai`: `security`
- `analitycs`: `security`
- `automation`: `security`
- `billing`: `security`
- `communications`: `security`
- `content`: `security`
- `production`: `security`, `analitycs`, `requests`
- `requests`: нет зависимостей решений
- `security`: нет зависимостей решений
