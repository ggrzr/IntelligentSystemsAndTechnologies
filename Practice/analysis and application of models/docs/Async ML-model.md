# Ассинхронный режим выполнения ML-моделей

Усовик С.В. (usovik@mirea.ru)

## Содержание:

1. Требования
2. Apache Kafka
3. Рекомендации

## Требования

Для работы необходимо следующее ПО:
- Python 3+
- Apache Kafka
- Docker и Docker Compose

## Apache Kafka

Ассинхронная обработка представляет собой процесс непрерывной обработки
данных, поступающих из внешних источников. Основная задача состоит в обработке
всего потока сообщений, без скопления очередей.
За процесс гарантированной безошибочной доставки сообщений отвечает брокер сообщений.
Наиболее ярким представителем является Apache Kafka. Брокер сообщений может быть установлен
в качестве докер-контейнеров при помощи декларативного [yml-файла](../projects/async-ML-model/docker-compose.yml).

В [примере](../projects/async-ML-model/kafka_producer.py) показан производитель сообщений 
в брокере, который забирает данные из удаленного источника.
В проекте представлен [пример](../projects/async-ML-model/kafka_consumer.py) потребителя
сообщений разбитого на темы.

Брокер, продюсер и консумер могут быть запущены при помощи скриптов: [kafka_consumer.sh](../projects/async-ML-model/kafka_consume.sh)
и [word-count-ex.sh](../projects/async-ML-model/word-count-ex.sh).


## Рекоммендации