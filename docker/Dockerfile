FROM maven:3.9-eclipse-temurin-21 AS build
WORKDIR /src

ARG MODULE
ENV MODULE=${MODULE}

COPY pom.xml .

COPY ${MODULE}/pom.xml ${MODULE}/pom.xml

RUN mvn -B -f ${MODULE}/pom.xml -DskipTests dependency:go-offline

COPY . .

RUN mvn -B -f ${MODULE}/pom.xml -DskipTests package


FROM amazoncorretto:21-alpine
WORKDIR /app

ARG MODULE
COPY --from=build /src/${MODULE}/target/*.jar /app/app.jar

EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
    


