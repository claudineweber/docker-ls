
# Docker container to honour the BD71 (UTBM) Exercise / TP1
## Create and start the docker container
<code>docker compose run --rm --entrypoint bash logstash</code>

Note that the teachers "conf" folder is named "pipeline" in this example and the teachers "data2" is named "data". This to be coherent with Logstatsh 

## From there on, you can start the exercice 
To test with the generic logstash.conf run:

<code>logstash --log.level=error -e "input { stdin { type =>stdin } } output { stdout { codec
=>rubydebug } }"</code>

To select the correct pipeline containing the wanted logstash.conf file as equested in Exercise 1.2.1 execute

<code>logstash -f /usr/share/logstash/pipeline/my-first-test/logstash.conf</code>
