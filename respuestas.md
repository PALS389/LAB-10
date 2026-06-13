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
Prometheus está diseñado exclusivamente para trabajar con métricas (series de tiempo numéricas, como % de CPU o contador de peticiones). No tiene la capacidad de almacenar ni procesar texto libre. Para capturar descripciones de errores, eventos o trazas de la aplicación, necesitamos un motor especializado en logs como Loki CLARO PE y si esta mal ps OÑO.

**2. ¿Qué ventaja aporta que las fuentes de datos de Grafana estén aprovisionadas como código y no creadas a mano?**
El aprovisionamiento automático garantiza que el entorno sea 100% reproducible y escalable. Elimina el riesgo de errores humanos (como equivocarse al tipear una IP, si me paso), ahorra tiempo cada vez que se levanta el laboratorio y permite llevar un control de versiones de la configuración a través de Git.

**3. El panel "CPU contenedor" y el panel "CPU host" pueden mostrar valores muy distintos. ¿Por qué? ¿Cuál usarías para alertar sobre una aplicación concreta?**
El "CPU host" mide el porcentaje de procesamiento de toda la máquina física, la cual corre múltiples procesos al mismo tiempo. El "CPU contenedor" mide el aislamiento de recursos de una sola aplicación. Para alertar sobre una aplicación concreta, se debe usar la métrica del contenedor, ya que nos dice exactamente si esa aplicación está fallando, independientemente de si el host tiene capacidad sobrante.

**4. ¿Qué diferencia hay entre el evaluation interval y el pending period de una alarma?**
El evaluation interval es la frecuencia con la que Grafana ejecuta la consulta para revisar los datos (por ejemplo, "revisar la CPU cada 10 segundos"). El pending period es un tiempo de gracia; exige que la condición crítica se mantenga por un tiempo prolongado (ej. 30 segundos continuos) antes de disparar la alerta. Esto evita que micro-picos momentáneos de CPU generen falsas alarmas