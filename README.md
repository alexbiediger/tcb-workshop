# How to run

Ecosystem locally
`podman compose up -d --build; podman compose logs -f`

Integration tests
`mvn -f karate-microservices-testing/pom.xml test   -Dtest='*CustomRunnerTest' -'Dkarate.options'="classpath:integration"`

All tests
`mvn -f karate-microservices-testing/pom.xml clean verify`

# Troubleshooting

## User / password incorrect for docker.io
```bash
docker logout; podman logout --all
podman stop $(podman ps -aq); podman rm $(podman ps -aq); podman system prune --all -f; podman builder prune --all -f; podman image prune -fa; podman volume prune -f
podman pull docker.io/eclipse-temurin:21-jdk
podman pull docker.io/eclipse-temurin:21-jre
```

Then redo _How to run_.

## Connectivity / connection error

```bash
podman machine stop
podman machine set --user-mode-networking
podman machine start
```

Then redo _How to run_.
