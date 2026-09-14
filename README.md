# Changuito — Riders

Frontend de la aplicación web **Changuito** orientado a los repartidores, encargados de retirar los pedidos en cada comercio y entregarlos en el domicilio del cliente.

## Enlaces del proyecto

- **Documentación:** https://paw-2026-changuito-docs.vercel.app/
- **Wireframes (Figma):** https://www.figma.com/design/ZeL7MqjxUKq20VJu6yR9Us/Changuito
- **Repositorios del TP Integrador:**
  - [Frontend Cliente](https://github.com/PAW-2026-DP/PAW-2026-Changuito-fn)
  - [Frontend Backoffice](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Backoffice-fn)
  - [Frontend Riders](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Riders-fn) (este repositorio)
  - [Backend](https://github.com/PAW-2026-DP/PAW-2026-Changuito-bn)
  - [Documentación](https://github.com/PAW-2026-DP/PAW-2026-Changuito-Docs)

## Objetivo del panel de repartidor

Interfaz web para el rol de logística de Changuito. Permite:

- Consultar el listado de tareas y pedidos asignados.
- Ver el detalle de cada retiro pendiente, incluyendo pedidos que involucran a más de un comercio.
- Registrar el retiro del pedido en cada comercio.
- Confirmar la entrega final al cliente.
- Consultar el historial de entregas.

La asignación de pedidos a un repartidor usa el mismo radio de cobertura que define qué comercios compiten en el motor de optimización: sólo son elegibles los repartidores dentro de ese rango respecto de los puntos de retiro y entrega. **Esa elegibilidad se valida en el servidor**, no en este frontend.

El pedido no puede pasar a *en camino* hasta que todas las órdenes de comercio que lo componen estén retiradas. Esa máquina de estados también se valida en el backend.

## Stack

- HTML5
- CSS3
- JavaScript sin frameworks ni librerías de terceros
- Comunicación con el backend mediante solicitudes HTTP sobre `fetch`

Es el frontend con mayor uso en pantalla chica del proyecto, así que el diseño se trabaja **mobile first**.

---

## Requisitos

| Componente | Notas |
| :---- | :---- |
| Navegador moderno | Chrome, Firefox, Edge o Safari en versión actual |
| Un servidor HTTP estático | Necesario para desarrollo: abrir los archivos con `file://` rompe las peticiones a la API por política de origen |
| [Backend de Changuito](https://github.com/PAW-2026-DP/PAW-2026-Changuito-bn) | Corriendo y accesible, con un usuario de rol repartidor y al menos un pedido asignado |

No hay dependencias que instalar ni proceso de build: son archivos estáticos.

---

## Puesta en marcha local

1. **Clonar el repositorio**

   ```bash
   git clone https://github.com/PAW-2026-DP/PAW-2026-Changuito-Riders-fn.git
   cd PAW-2026-Changuito-Riders-fn
   ```

2. **Configurar la URL de la API** apuntando al backend local (por ejemplo `http://localhost:8000/api`).

3. **Levantar un servidor estático**

   ```bash
   python -m http.server 5502
   ```

   O con la extensión **Live Server** de Visual Studio Code.

4. **Abrir** http://localhost:5502 e ingresar con un usuario de rol repartidor.

> **Nota:** cada frontend usa un puerto distinto en desarrollo (Cliente 5500, Backoffice 5501, Riders 5502) para poder tenerlos levantados en paralelo. Los tres orígenes deben estar habilitados en la configuración de CORS del backend.

> **TODO equipo:** el archivo de configuración del endpoint todavía no existe. Se define junto con la implementación, en la tercera entrega.

---

## Deployment

Sitio estático: puede publicarse en cualquier hosting de archivos estáticos o en el mismo servidor Apache que sirve la API, bajo su propio subdominio.

**Pasos:**

1. Configurar la URL de la API apuntando al backend de producción (por HTTPS).
2. Subir el contenido del repositorio al directorio público del hosting.
3. Verificar que el origen del sitio esté habilitado en la política de CORS del backend.
4. Servir todo el sitio por HTTPS.
5. Probar en pantalla de teléfono real, no sólo en el emulador del navegador: es el contexto de uso efectivo de esta aplicación.

**Checklist previo a publicar:**

- [ ] La URL de la API apunta a producción, no a `localhost`
- [ ] El sitio se sirve por HTTPS
- [ ] El origen está habilitado en el CORS del backend
- [ ] Verificado en pantalla chica
- [ ] No quedaron usuarios, credenciales ni datos de prueba en el código

---

## Estructura del repositorio

```text
PAW-2026-Changuito-Riders-fn/
├── assets/      Imágenes, íconos y recursos visuales
├── components/  Elementos reutilizables de interfaz
├── pages/       Pantallas del flujo del repartidor
├── services/    Comunicación con el backend
├── styles/      Hojas de estilo, variables y reglas responsive
└── utils/       Funciones auxiliares
```

## Estado actual

Wireframes definidos (login, tareas asignadas, detalle de tarea, registrar retiro, confirmar entrega, historial y perfil). La maquetación HTML/CSS y la lógica en JavaScript corresponden a la tercera entrega.
