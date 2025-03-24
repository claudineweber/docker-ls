# Start container in interactive mode
docker compose run --rm --entrypoint bash logstash

## From there on, you can start the exercice 
logstash --log.level=error -e "input { stdin { type =>stdin } } output { stdout { codec
=>rubydebug } }"

## To select the correct pipeline containing the wanted logstash.conf file run and use stdin, one must execute
logstash -f /usr/share/logstash/pipeline/my-first-test/logstash.conf
where my-first-test is the wanted pipeline