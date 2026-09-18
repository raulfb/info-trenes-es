# Info Trenes 🚂 🖥️

Configurador no oficial de las pantallas de salidas y llegadas de las estaciones españolas, en tiempo real.

> Este proyecto es un fork de [pantallas-estaciones](https://github.com/mariomnts/pantallas-estaciones), creado por [Mario Montes](https://github.com/mariomnts). Todo el mérito del trabajo original es suyo.

![Website](/public/card.png)

## 🚀 Demo

_Próximamente._

## 📡 De dónde salen los datos

Este proyecto no genera ni almacena datos de trenes. Todo se obtiene en tiempo real de los servicios públicos del sistema de información a viajeros (SIV) de ADIF:

- **Visor de pantallas**: la previsualización carga el visor web de ADIF (`info.adif.es/assets/gravita/gravita.html`) con los parámetros elegidos en el configurador: estación, vista, idioma, filtros, etc.
- **Datos en vivo**: se abre una conexión SignalR (WebSocket) con `info.adif.es/InfoStation` para recibir el estado de la estación en formato JSON.
- **Listado de estaciones**: `src/constants/stations.ts` contiene los códigos de estación de ADIF (5 dígitos). Ejemplos: Madrid Chamartín `17000`, Barcelona Sants `71801`, Santiago de Compostela `31400`.

Solo funcionan las estaciones gestionadas por ADIF que tienen el nuevo sistema de pantallas desplegado. El listado incluye también estaciones extranjeras (Portugal, Francia…) porque se usan como destino en los filtros, pero no tienen pantalla propia.

## 🗺️ Hoja de ruta

- [x] Mostrar solo estaciones españolas en el buscador principal
- [ ] Mensaje claro cuando una estación no tiene pantalla disponible
- [ ] Corregir erratas en el listado de estaciones
- [ ] Estaciones favoritas y recientes
- [ ] Sugerir la estación más cercana
- [ ] Script para comprobar qué estaciones tienen pantalla

## 🛠️ Tecnologías

- **Vue 3**: framework principal
- **Vite**: bundler y herramientas de desarrollo
- **Tailwind CSS**: estilos y diseño
- **SignalR**: conexión en tiempo real con los datos de ADIF
- **Vercel**: despliegue y hosting

## 🔧 Desarrollo

### Instalación

```bash
# Clonar el repositorio
git clone https://github.com/TU_USUARIO/info-trenes.git
cd info-trenes

# Instalar dependencias
npm install

# Ejecutar en desarrollo
npm run dev
```

### Limitación del iframe

ADIF bloquea que su visor se cargue en iframes de otros dominios, así que en local la previsualización aparecerá vacía. Para probarla hay dos opciones:

- Abrir Chrome con la seguridad web desactivada, usando un perfil aparte:

  ```bash
  google-chrome --disable-web-security --user-data-dir=/tmp/chrome-dev
  ```

- Usar una extensión que permita cargar iframes de otros dominios.

> ⚠️ Usa ese perfil de Chrome solo para desarrollar, nunca para navegar con normalidad.

## 📝 Nota legal

Este proyecto es **no oficial** y **no está afiliado con ADIF ni con Renfe**. Tiene un propósito educativo. La previsualización muestra contenido servido directamente por ADIF; esta web solo permite configurar los parámetros de visualización. Marcas, logotipos y datos mostrados en el panel son propiedad de ADIF.

El proyecto depende de servicios de ADIF no documentados, que pueden cambiar o dejar de funcionar en cualquier momento.

## 👨‍💻 Créditos

- **Proyecto original**: Mario Montes ([@mariomnts](https://x.com/mariomnts)), [pantallas-estaciones](https://github.com/mariomnts/pantallas-estaciones)
- **Fork**: Raul ([@TU_USUARIO](https://github.com/raulfb))

## 📄 Licencia

Distribuido bajo licencia [GPL-3.0](LICENSE), la misma que el proyecto original.
