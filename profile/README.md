# 🏋️‍♂️ Sistema de Microservicios - Gimnasio

## 📋 Descripción General

Este proyecto implementa una arquitectura de microservicios para la gestión integral de un gimnasio, diseñada para proporcionar escalabilidad, mantenibilidad y flexibilidad en el desarrollo de aplicaciones empresariales.

## Autores ✒️

> - Juan David Colonia Aldana - A00395956
> - Miguel Angel Gonzalez Arango - A00395687
> - Juan Felipe Plaza - A00365963
> - Brian Matasca A00378

## 🏛️ Diagrama de Componentes

El siguiente diagrama ilustra la arquitectura completa del sistema de microservicios del gimnasio, mostrando las relaciones entre componentes, contenedores de ejecución y flujos de comunicación:

![Diagrama de Componentes](../images/Gym%20Microservices%20-%20Components%20Diagram.png)

_Diagrama que muestra la interacción entre clientes (web/mobile), API Gateway, servidor de descubrimiento Eureka, y los microservicios de dominio (member, coach, equipment, class) con sus respectivas bases de datos H2._

## 🏗️ Arquitectura del Sistema

### Componentes Principales

#### **Eureka Server** (`eureka-server`)

- **Propósito**: Servidor de descubrimiento de servicios
- **Función**: Centraliza el registro y descubrimiento de todos los microservicios
- **Puerto**: 8761

#### **API Gateway** (`gateway`)

- **Propósito**: Punto de entrada único para todas las solicitudes
- **Función**: Enruta las peticiones a los microservicios correspondientes
- **Puerto**: 8086
- **Rutas disponibles**:
  - `/api/members/**` → Member Microservice
  - `/api/coaches/**` → Coach Microservice
  - `/api/equipment/**` → Equipment Microservice
  - `/api/classes/**` → Class Microservice

### Microservicios de Dominio

#### **Member Microservice** (`member-microservice`)

- **Propósito**: Gestión de miembros del gimnasio
- **Puerto**: 8081
- **Responsabilidades**: Información personal, membresías, estado de cuenta

#### **Coach Microservice** (`coach-microservice`)

- **Propósito**: Gestión de entrenadores
- **Puerto**: 8082
- **Responsabilidades**: Perfiles de entrenadores, especialidades, disponibilidad

#### **Equipment Microservice** (`equipament-microservice`)

- **Propósito**: Gestión de equipamiento del gimnasio
- **Puerto**: 8083
- **Responsabilidades**: Inventario, estado, mantenimiento

#### **Class Microservice** (`class-microservice`)

- **Propósito**: Gestión de clases y sesiones
- **Puerto**: 8084
- **Responsabilidades**: Programación, reservas, asistencia

## 🐳 Herramientas

### Docker

- **Propósito**: Orquestación de todos los servicios
- **Red**: `gym-network` (bridge)
- **Dependencias**: Servicios escalonados para garantizar el orden de inicio

### Tecnologías Base

- **Java**: Versión 17
- **Spring Boot**: 3.5.4
- **Spring Cloud**: 2025.0.0
- **Maven**: Gestión de dependencias y construcción

## 🔄 Flujo de Comunicación

```
Cliente → API Gateway → Eureka Server → Microservicio Específico
```

## 📁 Estructura

```
Gym-Microservices/
├── .github/                    # Configuración de GitHub
├── eureka-server/             # Servidor de descubrimiento
├── gateway/                   # API Gateway
├── member-microservice/       # Gestión de miembros
├── coach-microservice/        # Gestión de entrenadores
├── equipament-microservice/   # Gestión de equipamiento
├── class-microservice/        # Gestión de clases
├── parent/                    # POM padre para dependencias comunes
└── docker-compose.yml         # Orquestación de servicios
```

## 🚀 Beneficios de la Arquitectura

- **Desarrollo Paralelo**: Equipos pueden trabajar en diferentes microservicios simultáneamente
- **Despliegue Independiente**: Cada servicio puede ser desplegado sin afectar a otros
- **Tecnología Flexible**: Posibilidad de usar diferentes tecnologías por servicio
- **Escalado Selectivo**: Escalar solo los servicios que requieren más recursos
- **Mantenimiento Simplificado**: Cambios localizados en servicios específicos
