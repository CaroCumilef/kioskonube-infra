# KioskoNube - Infraestructura

Docker Compose para desplegar KioskoNube en AWS EC2.

## Servicios

| Servicio | Puerto | Descripción |
|---|---|---|
| rabbitmq | 15672 | Broker de mensajería (consola de administración) |
| rabbit-admin-service | 8085 | Administración de colas, exchanges y bindings |
| notificaciones-service | 8086 | Productor/consumidor de notificaciones por correo |
| despachos-service | 8084 | Despachos (PostgreSQL en RDS, consume orden.creada y publica despacho.actualizado) |

## Despliegue en la EC2

Los repositorios de los microservicios deben estar clonados al lado de esta carpeta:

    ~/kioskonube/
    ├── kioskonube-infra/
    ├── kioskonube-rabbit-admin-service/
    └── kioskonube-notificaciones-service/

1. Copiar `.env.example` a `.env` y completar los valores reales (nunca subir `.env`).
2. Levantar todo:

       docker compose up -d --build