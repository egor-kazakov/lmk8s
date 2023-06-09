# Роль для разворачивания Prometheus
## Задача
1. Установка Prometheus
2. Добавление systemd service файла для его запуска
3. Создание нужных пользователей и директорий с нужными правами и владельцами
4. Добавление конфигурации с прописанным таргетом для мониторинга самого Prometheus (см. https://prometheus.io/docs/prometheus/latest/getting_started/#configuring-prometheus-to-monitor-itself)
5. Запуск и релоад сервиса при изменении глобальных параметров конфигурации (не забудьте вынести эти параметры в defaults)

## Описание
Роль создает системного пользователя, скачиает архив с **github**, устанавливает Prometheus (бинарный файл в /usr/local/bin/), создает необходимые директории, формирует конфигурационный файл (в зависимости от Node Exporters), создает и запускает сервис.

## Доступ
- Prometheus доступен по ссылке http://localhost:9090/
