# === FRONTEND STAGE ===
FROM node:18 AS frontend
WORKDIR /app
COPY frontend/ .
RUN npm install
RUN npm run build

# === BACKEND STAGE ===
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY backend/target/*.jar app.jar
COPY --from=frontend /app/build /app/static
ENTRYPOINT ["java", "-jar", "app.jar"]
