# Домашнее задание к занятию "`10.3 pacemaker`" - `Паромов Роман`

## Задание 1
Pacemaker служит для создания и управления кластерами.
Основные функции:
  поддержка кластеров любого размера;
  независимость от подсистемы хранения и типов ресурсов;
  Обнаружение и восстановление сбоев на уровне узлов и сервисов;
  поддержка практически любой избыточной конфигурации;
  автоматическая репликация конфига на все узлы кластера;
  возможность задания порядка запуска ресурсов, а также их совместимости на одном узле;
  поддержка расширенных типов ресурсов.
## Задание 2
Corosync - программный продукт, позволяющий реализовать кластер серверов. Основное назначение это знать и передавать состояние всех серверов кластера.
Основные функиции:
  отслеживание состояния приложений;
  оповещение приложений о смене активной ноды кластера;
  отправка одинаковых сообщений процессам на всех узлах кластера;
  предоставление доступа к базе данных с конфигурацией и статистикой, а также отправка уведомлений о ее изменениях.
## Задание 3
nodetwo
```
totem {
    version: 2
    cluster_name: newCluster
    transport: knet
    crypto_cipher: aes256
    crypto_hash: sha256
}

nodelist {
    node {
        ring0_addr: nodeone
        name: nodeone
        nodeid: 1
    }

    node {
        ring0_addr: nodetwo
        name: nodetwo
        nodeid: 2
    }
}

quorum {
    provider: corosync_votequorum
    two_node: 1
}

logging {
    to_logfile: yes
    logfile: /var/log/corosync/corosync.log
    to_syslog: yes
    timestamp: on
}
```
nodeone
```
totem {
    version: 2
    cluster_name: newCluster
    transport: knet
    crypto_cipher: aes256
    crypto_hash: sha256
}

nodelist {
    node {
        ring0_addr: nodeone
        name: nodeone
        nodeid: 1
    }

    node {
        ring0_addr: nodetwo
        name: nodetwo
        nodeid: 2
    }
}

quorum {
    provider: corosync_votequorum
    two_node: 1
}

logging {
    to_logfile: yes
    logfile: /var/log/corosync/corosync.log
    to_syslog: yes
    timestamp: on
}
```
![](https://github.com/Romera14/homework_pacemaker/blob/main/Снимок%20экрана%202022-12-06%20в%2019.31.03.png)
Мне показалось что командой pcs config backup filename, он создает файл. Не понял как его посмотреть.
