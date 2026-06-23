# Navium — Deploy Sucursal

Configuración de despliegue de la rebanada de **Sucursal**:
**BFF Sucursal + Agendamiento + Notificaciones**.

Las imágenes se bajan de DockerHub (publicadas por los pipelines de cada servicio).
La rama **`deploy`** contiene el `docker-compose.yml` que se levanta en la EC2.

## Levantar

```bash
docker compose up -d
```

## Arquitectura

- `agendamiento`, `notificaciones` → microservicios propios (puertos internos).
- `bff` → punto de entrada (puerto `8082` expuesto para los frontends).

El BFF llama a servicios de otros equipos (Usuarios, Contenedores, Andenes) por
internet, usando las URLs configuradas en el `docker-compose.yml`.
