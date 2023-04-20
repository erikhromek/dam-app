# DAM - API & Web app Híbrida


## API

- Ya incluye una DB con datos de prueba (2 válculas, 2 sensores, algunas mediciones y logs)
- Se encuentra dockerizada la base de datos, por lo que esta se levanta mediante el comando _docker compose up_ (o _docker-compose up_ para versiones viejas abriendo una terminal en la carpeta **/backend**)
- para levantar la API se debe hacer _npm install_ y _npm run dev_ la carpeta **/backend**, esto levantará la API en el puerto 3000; la API ya se encuentra conectada a la DB de Docker

Existen 6 endpoints:
1. **GET /devices** devuelve lista de dispositivos
2. **GET /valves/:valveId** devuelve lista de válvulas
3. **GET /devices/:deviceId** devuelve un dispositivo, junto a su última medición
4. **GET /measurements/:deviceId** devuelve el listado de mediciones de un dispositivo
5. **GET /logs/:valveId** devuelve los logs de aperturas/cierre sobre una válvula
6. **PUT /valves/:valveId** abre/cierra una válvula, generando un log y creando una medición aleatoria (de 0 a 100)

## Webapp

- Se debe moverse a la carpeta **frontend/** y correr npm install (node 18)
- el comando **ionic serve** iniciará un navegador con la app corriendo en *http://localhost:8100* (ya se encuentra apuntando a la API en el puerto 3000)

Se incorporaron:

- 1 directiva (StatusHighlightDirective) para setear el color del valor de una medición (verde, amarillo, naranja y rojo de acuerdo al valor)
- 4 servicios (LogService, DeviceService, ValveService, MeasurementService)
- 4 pantallas (Devices, Device-Detail, Logs, Measurements)
- 1 pipe (MeasurementUnitPipe) para formatear el valor de una medición (valor + unidad de medida Cb)
- 4 modelos (Device, Measurement, Valve, Log)
