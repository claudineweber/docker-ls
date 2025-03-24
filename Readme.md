# Docker container to honour the BD71 (UTBM) Exercise / TP1

## Container Structure

This Docker container is structured specifically to align with the BD71 (UTBM) TP1 exercise requirements. Note that this structure serves as a practical example and **is not the complete TP solution**.

### Folder Structure

The directory structure inside the `docker-ls` project is organized as follows:

```
docker-ls/
├── docker-compose.yml       # Defines and manages container setup and runtime behavior
└── logstash
    ├── Dockerfile           # Defines the Logstash container build process
    ├── config
    │   └── logstash.yml     # General Logstash settings, such as disabling Elasticsearch monitoring
    ├── data                 # Logstash internal data and persistence (equivalent to teacher's "data2")
    ├── input                # Directory for input log files
    │   └── auth.log
    ├── logs                 # Directory for Logstash log files
    ├── output               # Directory for Logstash output files
    └── pipeline             # Pipeline configurations (equivalent to teacher's "conf" folder)
        └── my-first-test
            └── logstash.conf
```

### Explanation of Files:

#### `docker-compose.yml`
- Defines how the Docker containers should be built and run.
- Mounts local directories (`data`, `input`, `output`) into the container for persistent data management.
- Starts the Logstash container interactively using the provided Dockerfile configuration.

#### `Dockerfile`
- Builds a Docker image based on the official Logstash Docker image.
- Copies pipeline configurations and the `logstash.yml` file into the container.
- Sets up a persistent volume for Logstash data storage.

#### `config/logstash.yml`
- Contains global Logstash configurations, such as disabling Elasticsearch monitoring (`xpack.monitoring.enabled: false`).

#### `pipeline/my-first-test/logstash.conf`
- Defines the pipeline configurations (input, output, and optional filtering) to process log data according to the TP exercises.

## Create and Start the Docker Container

To launch the Docker container interactively and access its shell, execute:

```bash
docker compose run --rm --entrypoint bash logstash
```

## Starting the Exercise

### Generic Logstash Configuration Test

To test Logstash using a generic configuration, run:

```bash
logstash --log.level=error -e "input { stdin { type =>stdin } } output { stdout { codec =>rubydebug } }"
```

### Running the Exercise Pipeline

To select and run the specific pipeline defined in `my-first-test` as required in Exercise 1.2.1, execute:

```bash
logstash -f /usr/share/logstash/pipeline/my-first-test/logstash.conf
```

### Important Note

This Docker container and structure are designed to assist with exercise TP1, providing a starting point for pipeline testing and interaction. Further adjustments and configurations will be necessary to complete the entire TP.