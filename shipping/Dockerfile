#
# Build stage
#
FROM maven:3.9-eclipse-temurin-21 AS build

WORKDIR /opt/shipping

# Copy only pom.xml first for dependency caching
COPY pom.xml .
RUN mvn dependency:go-offline

# Copy the rest of the source
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests

#
# Runtime stage
#
FROM eclipse-temurin:21-jdk

WORKDIR /opt/shipping

# Environment variables
ENV CART_ENDPOINT=cart:8080 \
    DB_HOST=mysql

# Expose the port
EXPOSE 8080

# Copy the built JAR from build stage
COPY --from=build /opt/shipping/target/shipping-1.0.jar shipping.jar

# Run the app with specified JVM options
CMD ["java", "-Xmn256m", "-Xmx768m", "-jar", "shipping.jar"]
