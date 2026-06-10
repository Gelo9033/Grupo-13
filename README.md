##  Aplicación Profesional de la Práctica

Actualmente trabajo en el área de desarrollo de software. Aunque estoy en pleno proceso de aprendizaje sobre temas de infraestructura, mi verdadero interés y hacia donde quiero orientar mi carrera es hacia la arquitectura y ciberseguridad.

## El Desafío de los Datos

En mi día a día, gestionamos un volumen enorme de información. Los datos más críticos que generamos son:

* Registros de eventos (logs) de nuestros microservicios.
* Tráfico que atraviesa nuestros API Gateways.
* Alertas de nuestro stack de observabilidad (notificaciones de fallos vía Telegram).

Generamos muchísimos datos, pero el problema es que, operativamente, esa información está dispersa y actualmente solo la usamos de forma reactiva para apagar incendios.

## Arquitectura Propuesta: El Valor de la Integración

Aquí es donde veo un valor enorme en integrar PostgreSQL, Docker y Python, con un enfoque puramente de seguridad. Como nuestra arquitectura central ya funciona sobre bases de datos Oracle (11g y 19c), no usaría PostgreSQL para reemplazar la transaccionalidad de los microservicios.

En su lugar, la implementación ideal sería:

* **PostgreSQL:** Como un repositorio centralizado exclusivo para auditoría y seguridad (un Security Data Warehouse).
* **Python:** Para construir un script ETL que extraiga constantemente los logs crudos y las alertas, los limpie y los guarde estructurados.
* **Docker / Kubernetes:** Como todos nuestros servicios ya están en contenedores y planeamos escalar a Kubernetes, empaquetar este motor de análisis nos asegura que pueda convivir en la misma infraestructura de forma aislada, portable y segura.

> "El mayor beneficio de implementar este proceso ETL en mi equipo sería cambiar nuestra mentalidad de reactiva a proactiva."

## Resolución de Problemas y Beneficios

Las notificaciones de Telegram son geniales para saber qué se cayó hoy, pero un proceso ETL nos daría memoria histórica. Dejaríamos de revisar archivos de texto sueltos durante un incidente y pasaríamos a tener datos consultables en segundos.

Finalmente, analizar esta información estructurada nos permitiría resolver problemas de fondo, logrando:

* **Medir la carga exacta:** Monitorear el consumo y rendimiento de cada microservicio.
* **Detectar brechas de seguridad:** Al tener un historial limpio, sería posible identificar patrones de ataques recurrentes.
* **Trazabilidad:** Rastrear de qué IPs provienen las peticiones anómalas a los gateways y ver qué servicios son los más golpeados.

Toda esta inteligencia nos daría la base técnica para definir políticas de seguridad estrictas y mejorar nuestros estándares de desarrollo, construyendo un software mucho más robusto.
## Nombre Integrante
Luis Felipe Guamán León