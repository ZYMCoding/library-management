FROM adoptopenjdk/maven-openjdk8:latest
WORKDIR /usr/src/library-management
COPY . .
COPY src/main/resources/application.yml /etc/appserver/
RUN mvn -B -f pom.xml dependency:resolve
RUN mvn -B package -DskipTests
ENTRYPOINT ["java", "-jar", "-Dspring.profiles.active=test", "/usr/src/library-management/target/springboot-0.0.1-SNAPSHOT.jar", "--spring.config.location=file:/etc/appserver/application.yml"]
EXPOSE 9090