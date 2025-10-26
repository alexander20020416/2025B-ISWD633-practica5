# Ejercicio
Configurar SonarQube utilizando Docker Compose, para esto necesitas dos servicios:
- Servicio: SonarQube
- Desde el host es necesario acceder a SonarQube por lo que necesitas mapear el puerto correspondiente.
- Servicio: PostgreSQL (existen otras opciones: Microsoft SQL Server, Oracle)
- Coloca un healtcheck para cada uno de los servicios.
- Los dos servicios deben pertenecer a una red de tipo bridge
- Investiga cuáles son los volúmenes necesarios para cada servicio
- Investiga cuáles son las variables de entorno para que los servicios funcionen de manera adecuada.
  
# Una vez creado tu archivo .yaml realiza la respectiva prueba 
# COMPLETAR CON UNA CAPTURA DE PANTALLA LUEGO DE EJECUTAR EL ARCHIVO
```
version: '3.8'

services:
  postgres-service:
    image: postgres:15
    container_name: sonarqube-postgres
    environment:
      POSTGRES_USER: sonar
      POSTGRES_PASSWORD: sonar123
      POSTGRES_DB: sonarqube
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - sonar-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U sonar"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 30s

  sonarqube-service:
    image: sonarqube:community
    container_name: sonarqube-server
    ports:
      - "8081:9000"
    environment:
      SONAR_JDBC_URL: jdbc:postgresql://postgres-service:5432/sonarqube
      SONAR_JDBC_USERNAME: sonar
      SONAR_JDBC_PASSWORD: sonar123
    volumes:
      - sonarqube-data:/opt/sonarqube/data
      - sonarqube-extensions:/opt/sonarqube/extensions
      - sonarqube-logs:/opt/sonarqube/logs
    networks:
      - sonar-network
    healthcheck:
      test: ["CMD", "wget", "-qO-", "http://localhost:9000/api/system/status"]
      interval: 30s
      timeout: 10s
      retries: 5
      start_period: 60s
    restart: unless-stopped
    depends_on:
      postgres-service:
        condition: service_healthy

volumes:
  postgres-data:
  sonarqube-data:
  sonarqube-extensions:
  sonarqube-logs:

networks:
  sonar-network:
    driver: bridge
```
# ACCEDER A LOCALHOST:puertoDefinido para ingresar a SonarQube
<img width="1920" height="912" alt="imagen" src="https://github.com/user-attachments/assets/2dc02df8-0537-4ce5-a4c2-a019d2a2438a" />
