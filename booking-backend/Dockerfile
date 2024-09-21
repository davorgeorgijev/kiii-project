FROM maven:3.8.5-openjdk-17 AS build
WORKDIR /booking-backend
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM amazoncorretto:17
WORKDIR /booking-backend
COPY --from=build /booking-backend/target/*.jar app.jar
COPY wait-for-it.sh /wait-for-it.sh
RUN chmod +x /wait-for-it.sh
EXPOSE 8080
ENTRYPOINT ["/wait-for-it.sh", "db:5432", "--timeout=30", "--", "java", "-jar", "app.jar"]