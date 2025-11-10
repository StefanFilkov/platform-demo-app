FROM amazoncorretto:21-alpine

WORKDIR /app/

COPY target/*.jar app.jar

EXPOSE 8080

CMD ["sh", "-c", "java -jar app.jar"]