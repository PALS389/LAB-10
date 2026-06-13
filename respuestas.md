# Laboratorio de Observabilidad

## Instrucciones para validar el trabajo
Para levantar y verificar este proyecto en cualquier entorno local con Docker, siga estos pasos:

1. Clonar el repositorio.
2. Ejecutar el comando para levantar la infraestructura:
   `docker compose up -d --build`
3. Verificar que los servicios estén activos en los siguientes puertos:
   - Frontend: http://localhost:8080
   - Backend: http://localhost:3001
   - Grafana: http://localhost:3000
   - Prometheus: http://localhost:9090
   - Loki: http://localhost:3100
4. Generar tráfico utilizando los botones de la interfaz del Frontend.
5. Para detener el laboratorio y limpiar los volúmenes:
   `docker compose down -v`

---

## Respuestas a las Preguntas del Laboratorio

**1. ¿Por qué necesitamos Loki además de Prometheus si ya tenemos `/metrics`?**
[Respuesta pendiente]

**2. ¿Qué ventaja aporta que las fuentes de datos de Grafana estén aprovisionadas como código y no creadas a mano?**
[Respuesta pendiente]

**3. El panel "CPU contenedor" y el panel "CPU host" pueden mostrar valores muy distintos. ¿Por qué? ¿Cuál usarías para alertar sobre una aplicación concreta?**
[Respuesta pendiente]

**4. ¿Qué diferencia hay entre el evaluation interval y el pending period de una alarma?**
[Respuesta pendiente]