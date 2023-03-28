FROM maven:3.8.3-openjdk-17 AS BUILD
COPY src /usr/src/app/src
COPY pom.xml /usr/src/app
RUN mvn --file /usr/src/app/pom.xml clean package

FROM openjdk:17
COPY --from=build /usr/src/app/target/jmx-0.0.1-SNAPSHOT.jar /usr/app/jmx-0.0.1-SNAPSHOT.jar
EXPOSE 8088
ENTRYPOINT ["java","-jar","/usr/app/jmx-0.0.1-SNAPSHOT.jar"]