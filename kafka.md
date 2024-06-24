# ENV xy and login to kafka-console-0

gccdev


k exec -it kafka-console-0 /bin/bash

kafkactl consume UiProfilePublished -k
#list topics
kafkactl list topics
