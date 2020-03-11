# kafka-grafana
After you've cloned the repository, just run

docker-compose up

1. Kafka uses Yammer Metrics for metrics reporting in the server. Klienci Java korzystają z Kafka Metrics, czyli wbudowanego rejestru metryk, który minimalizuje zależności, które klienci wczytywują do swoich aplikacji

2. Kafka disables by default:
    a) remote JMX by default - enable remote monitoring using JMX by setting the environment variable JMX_PORT
    b) SSL security - in production you must enable security
    c) authentication is disabled for JMX by default - setting the environment variable KAFKA_JMX_OPTS

3. Wszystkie metryki Kafki mają odpowiadający im wskaźnik CAŁKOWITEJ WARTOŚCI (TOTAL) dla tej metryki z suffixem -total np: For example, records-consumed-rate has a corresponding metric named records-consumed-total

4. Najłatwiejszym sposobem sprawdzenia dostępnych wskaźników jest uruchomienie jconsole i skierowanie jej na działającego klienta lub serwer Kafka; pozwoli to na przeglądanie wszystkich danych za pomocą JMX.

Kafka produces its metric through JMX → Prometheus store Kafka's JMX metrics → visualize them using Grafana



to jest prosta kafka z 3 brokerami wykonana na docker-compose.yml,
w celu przetestowania KSQL - był problem z wprowadzeniem zmiennej KAFKA_OPTS i okazało się że dla KSQL należy zmienić nazwę na KSQL_OPTS aby opcje dla Javy się doinstalowały.
plik file.yaml jest pobrany z kubernetes LH - może zawierać prywatne informacje 


This will run a Kafka broker, Prometheus and Grafana in the same host. You must configure grafana to import Prometheus data source [which is described at the end of the main article](https://medium.com/@mousavi310/monitor-apache-kafka-using-grafana-and-prometheus-873c7a0005e2).