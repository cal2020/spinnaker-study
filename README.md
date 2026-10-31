# Spinnaker Study — Quarkus and Delivery-Pipeline Sandbox

An older Java/Quarkus practice project with REST examples, an application health/metrics example, and Jenkins/Spinnaker-related deployment assets. The repository includes source code and configuration, **not a ready-made Spinnaker installation**.

## How it works

The application is built on **Java 11** and **Quarkus 2.6.3.Final** (see [pom.xml](pom.xml)). `src/main/java/org/acme/rest/json/` provides sample **Fruit** and **Legume** REST resources; `src/main/java/org/acme/metrics/` includes a prime-number checker. HTML examples live under `src/main/resources/META-INF/resources/`.

The [Jenkinsfile](Jenkinsfile), `terraform/` and Dockerfiles under `src/main/docker/` show integration and deployment patterns. They do **not** provision Jenkins, cloud credentials or a full running Spinnaker control plane automatically.

## Start the application

Prerequisites: JDK 11 (or a JDK compatible with this historical Quarkus release), Git and internet access for Maven dependencies. The repository ships a Maven wrapper.

```bash
git clone https://github.com/cal2020/spinnaker-study.git
cd spinnaker-study
chmod +x ./mvnw
./mvnw quarkus:dev
# inspect the local Quarkus server, normally http://localhost:8080/
```

For packaging, run `./mvnw package`. Review `src/main/resources/application.properties` and `src/main/docker/Dockerfile.jvm` to choose the correct container entrypoint. A current JDK/runtime is not guaranteed to support these old dependencies without upgrading them.

## Data, infrastructure and access

The Fruit/Legume records are **example application data**, not a procurement system or production catalog. No external dataset, paid API or model credentials are required for local development. Running cloud deployment examples requires separately provisioned registries, IAM rights, Jenkins/Spinnaker installations and suitable Terraform configuration; do not attempt production infrastructure changes without authorization.

The checked-in [setup.html](setup.html) and [spinnaker-material.zip](spinnaker-material.zip) are historical learning resources. Do not assume their instructions or dependencies are current. No verified UI screenshot gallery or standalone project license was identified at the root.
