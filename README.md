# 🗳️ Election Management API - Quarkus

Este repositório contém uma aplicação Quarkus para o gerenciamento de eleições e candidatos, utilizando uma arquitetura organizada em camadas com boas práticas de desenvolvimento. A base do projeto está estruturada para permitir escalabilidade, observabilidade e facilidade de integração com banco de dados relacional e Redis.


## 🧩 Visão Geral das Tecnologias

- **Java 17**
- **Quarkus 2.16.4.Final**
- **Hibernate ORM** com suporte a JPA
- **Flyway** para versionamento de banco de dados
- **MariaDB** (com JDBC driver)
- **Redis** (cliente reativo)
- **OpenTelemetry** para tracing
- **RESTEasy Reactive** para APIs REST
- **SmallRye OpenAPI** para documentação Swagger
- **FreeBuilder** para builders automáticos de classes imutáveis
- **JUnit5 + Mockito + Instancio** para testes unitários

---

## ⚙️ Configuração e Execução

### ✅ Requisitos
- Java 17 instalado
- Maven 3.8+
- Banco de dados **MariaDB** local ou remoto (ou Docker)
- Redis opcional (se quiser testar repositórios reativos)

### 🔧 Configuração local no `application.properties`

```properties
quarkus.datasource.jdbc.url=jdbc:mariadb://localhost:3306/elections
quarkus.datasource.username=root
quarkus.datasource.password=
quarkus.redis.hosts=redis://localhost:6379
```

### ▶️ Rodar a aplicação

```bash
./mvnw quarkus:dev
```

---

## 🧪 Testes

Este projeto já vem com configuração para testes unitários e de integração utilizando:

- **JUnit5**
- **Mockito** para mocks
- **Instancio** para gerar objetos de teste automaticamente
- **RestAssured** para testes de API REST

Execute os testes com:
```bash
./mvnw test
```

---

## 🛠️ Sobre o `pom.xml`

O `pom.xml` está configurado com:

- Importação do BOM do Quarkus (para gestão de dependências)
- Plugins de build do Quarkus e Maven
- Plugins de testes (`surefire` e `failsafe`)
- Perfil para compilação *native* com GraalVM (`-Dnative`)

```xml
<profile>
  <id>native</id>
  <activation>
    <property>
      <name>native</name>
    </property>
  </activation>
  <properties>
    <skipITs>false</skipITs>
    <quarkus.package.type>native</quarkus.package.type>
  </properties>
</profile>
```

---

## 📦 Build de Produção

```bash
./mvnw clean package -DskipTests
```

Para gerar binário nativo (com GraalVM configurado):
```bash
./mvnw clean package -Dnative -DskipTests
```

---

## 🔍 Observabilidade

Com `quarkus-opentelemetry` você já pode rastrear requisições via OTEL Collector ou Jaeger:

```properties
%prod.quarkus.opentelemetry.enabled=true
```

---

## 📃 Licença

MIT - use, modifique e contribua!

---

Caso precise, posso gerar o `docker-compose.yml`, adicionar Swagger UI customizada ou gerar scripts SQL de migração. É só pedir! 🚀
