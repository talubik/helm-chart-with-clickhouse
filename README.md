# Helm-чарт для развертывания ClickHouse

Этот Helm-чарт позволяет развернуть одну инсталляцию (single-instance) базы данных ClickHouse в кластере Kubernetes.

## Установка

1.  **Установите Helm**.
2.  **Установите и запустите minikube*.
3.  **Склонируйте репозиторий** с этим чартом.
4.  **Установите чарт** с помощью команды:

    ```bash
    helm install my-clickhouse ./clickhouse-chart
    ```

## Параметры конфигурации

Основные параметры можно изменить в файле `values.yaml` или передать через командную строку при установке.

### Изменение версии ClickHouse

Чтобы установить другую версию ClickHouse (например, 23.8), выполните команду:

```bash
helm install my-clickhouse ./clickhouse-chart --set image.tag="23.8"
```

### Настройка пользователей

Список пользователей и их пароли настраиваются в секции `clickhouse.users` в файле `values.yaml`.

Пример:
```yaml
clickhouse:
  users:
    - name: user1
      password: password1
    - name: user2
      password: password2
```

Пароли автоматически хешируются (SHA256) и передаются в ClickHouse через переменные окружения для безопасности.
