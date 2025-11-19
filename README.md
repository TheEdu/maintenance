# 🔧 Página de Mantenimiento / Fuera de Servicio

Página web estática, responsiva y sobria para mostrar mensajes de estado cuando un servicio no está disponible. Configurable mediante query strings para diferentes escenarios.

## 📋 Descripción

Esta es una solución simple y elegante para redirigir tráfico cuando necesitas desactivar temporalmente una aplicación web. Solo tienes que apuntar el DNS o hacer un redirect a esta página con los parámetros correspondientes.

## ✨ Características

- **100% estático**: Solo HTML, CSS y JavaScript vanilla - sin dependencias
- **Completamente responsivo**: Funciona perfectamente en móviles, tablets y escritorio
- **Diseño sobrio y profesional**: Interfaz limpia y moderna
- **Configurable vía query strings**: Cambia el mensaje y nombre de la app sin modificar código
- **3 estados predefinidos**: Mantenimiento, Fuera de servicio, y Actualizaciones
- **Timestamp automático**: Muestra cuándo se cargó la página

## 🚀 Uso Rápido

### Ejemplos de URLs

```bash
# Mantenimiento (por defecto) - Solo título, sin mensaje adicional
https://tu-dominio.com/?app=app.test.com.ar&company=focustech.com.ar

# Fuera de servicio - Solo título
https://tu-dominio.com/?status=offline&app=api.ejemplo.com&company=Mi%20Empresa

# Actualizaciones - Solo título
https://tu-dominio.com/?status=updating&app=dashboard.test.com&company=TechCorp

# Mensaje personalizado - Con mensaje propio
https://tu-dominio.com/?status=custom&app=portal.ejemplo.com&company=Ejemplo%20SA&message=Volvemos%20el%20lunes%20a%20las%208am
```

## 📖 Parámetros del Query String

### `status` (opcional)

Define el tipo de mensaje a mostrar:

| Valor | Descripción | Icono | Contenido |
|-------|-------------|-------|-----------|
| `maintenance` | Mantenimiento programado (por defecto) | 🔧 | Solo título |
| `offline` | Servicio fuera de línea | ⚠️ | Solo título |
| `updating` | Implementando actualizaciones | 🚀 | Solo título |
| `custom` | Mensaje completamente personalizado | 📋 | Título + mensaje del parámetro `message` |

**Nota:** Los estados predefinidos (maintenance, offline, updating) **NO** muestran mensaje adicional, solo el título para mantener la página limpia.

### `app` (opcional)

El nombre de tu aplicación, servicio o dominio.

- **Por defecto**: "Servicio"
- **Ejemplo**: `?app=app.test.com.ar`

### `company` (opcional)

El nombre de la empresa dueña del producto/servicio.

- **Por defecto**: (no se muestra)
- **Ejemplo**: `?company=focustech.com.ar`

### `message` (solo para status=custom)

Mensaje personalizado que se mostrará como mensaje principal.

- **Uso**: Solo con `status=custom`
- **Ejemplo**: `?status=custom&message=Estaremos%20de%20vuelta%20el%20lunes%20a%20las%208am`
- **Nota**: Los espacios se codifican como `%20`

## 💡 Ejemplos Visuales de Uso

### Ejemplo 1: Mantenimiento Básico
```
https://mantenimiento.tu-dominio.com/?app=app.test.com.ar&company=focustech.com.ar
```
**Muestra:**
```
🔧

app.test.com.ar
focustech.com.ar

En Mantenimiento

┌─────────────────────────────────────────────────┐
│ Lamentamos las molestias ocasionadas.          │
│ Estaremos de vuelta pronto.                     │
└─────────────────────────────────────────────────┘

Última actualización: 19 de noviembre de 2025, 14:30
```

### Ejemplo 2: Fuera de Servicio
```
https://mantenimiento.tu-dominio.com/?status=offline&app=api.miempresa.com&company=Mi%20Empresa
```
**Muestra:**
```
⚠️

api.miempresa.com
Mi Empresa

Fuera de Servicio

┌─────────────────────────────────────────────────┐
│ Disculpa las molestias.                         │
│ Te agradecemos tu paciencia.                     │
└─────────────────────────────────────────────────┘
```

### Ejemplo 3: Actualizaciones
```
https://mantenimiento.tu-dominio.com/?status=updating&app=dashboard.ejemplo.com&company=Ejemplo%20SA
```
**Muestra:**
```
🚀

dashboard.ejemplo.com
Ejemplo SA

Recibiendo Actualizaciones

┌─────────────────────────────────────────────────┐
│ Gracias por tu paciencia mientras mejoramos     │
│ tu experiencia.                                  │
└─────────────────────────────────────────────────┘
```

### Ejemplo 4: Mensaje Personalizado
```
https://mantenimiento.tu-dominio.com/?status=custom&app=portal.test.com&company=TestCorp&message=Volvemos%20el%20lunes%20a%20las%208am
```
**Muestra:**
```
📋

portal.test.com
TestCorp

Aviso

Volvemos el lunes a las 8am

┌─────────────────────────────────────────────────┐
│ Gracias por tu comprensión.                     │
└─────────────────────────────────────────────────┘
```

## 💡 Casos de Uso Reales

### 1. Mantenimiento Programado
```
https://mantenimiento.tu-dominio.com/?app=app.test.com.ar&company=focustech.com.ar
```
Ideal para mantenimientos rutinarios. Muestra solo el título "En Mantenimiento" sin mensajes adicionales.

### 2. Problema Técnico Inesperado
```
https://mantenimiento.tu-dominio.com/?status=offline&app=api.miempresa.com&company=Mi%20Empresa
```
Cuando hay un problema técnico y el servicio no está disponible.

### 3. Deploy en Progreso
```
https://mantenimiento.tu-dominio.com/?status=updating&app=dashboard.ejemplo.com&company=Ejemplo%20SA
```
Mientras estás desplegando una nueva versión.

### 4. Mensaje Específico con Fecha/Hora
```
https://mantenimiento.tu-dominio.com/?status=custom&app=portal.test.com&company=TestCorp&message=Estaremos%20de%20vuelta%20el%20lunes%2020/11%20a%20las%208am
```
Cuando necesitas comunicar información específica como fechas de retorno.

## 🧪 Prueba Local

### En WSL (Windows Subsystem for Linux)

Si estás usando WSL, puedes levantar un servidor local y acceder desde tu navegador de Windows:

#### Opción 1: Python (ya viene instalado)

```bash
# Python 3
python3 -m http.server 8000

# O Python 2
python -m SimpleHTTPServer 8000
```

Luego abre en tu navegador de Windows: `http://localhost:8000`

#### Opción 2: PHP (si lo tienes instalado)

```bash
php -S localhost:8000
```

Luego abre: `http://localhost:8000`

#### Opción 3: Node.js con npx (si tienes Node)

```bash
npx http-server -p 8000
```

Luego abre: `http://localhost:8000`

**Nota WSL**: Gracias a la integración de WSL2 con Windows, `localhost` funciona automáticamente entre ambos sistemas. Si tienes problemas, también puedes usar la IP de WSL que obtienes con `ip addr show eth0`.

### Prueba con Query Strings

```bash
# Mantenimiento básico
http://localhost:8000/?app=app.test.com.ar&company=focustech.com.ar

# Fuera de servicio
http://localhost:8000/?status=offline&app=api.ejemplo.com&company=Mi%20Empresa

# Actualizaciones
http://localhost:8000/?status=updating&app=portal.test.com&company=TestCorp

# Mensaje personalizado
http://localhost:8000/?status=custom&app=web.test.com&company=TestCorp&message=Volvemos%20el%20lunes%20a%20las%208am

# Solo con app (mínimo)
http://localhost:8000/?app=miapp.com
```

## 🌐 Despliegue en Producción

### Opción 1: GitHub Pages (Gratis)

1. Sube este repositorio a GitHub
2. Ve a Settings → Pages
3. Selecciona la rama `master` o `main`
4. Tu página estará disponible en `https://tu-usuario.github.io/maintenance/`

### Opción 2: Netlify (Gratis)

1. Conecta este repositorio a Netlify
2. Deploy automático
3. Obtienes una URL tipo `https://tu-app.netlify.app`

### Opción 3: Vercel (Gratis)

1. Importa el repositorio en Vercel
2. Deploy instantáneo
3. URL: `https://tu-app.vercel.app`

### Opción 4: Servidor Propio

Simplemente sube el archivo `index.html` a cualquier servidor web (Apache, Nginx, etc.).

## 🔄 Integración con tus Servicios

### Nginx

Cuando necesites activar el modo mantenimiento:

```nginx
location / {
    return 302 https://mantenimiento.tu-dominio.com/?status=maintenance&app=Tu%20App;
}
```

### Apache

```apache
RewriteEngine On
RewriteRule ^(.*)$ https://mantenimiento.tu-dominio.com/?status=maintenance&app=Tu%20App [R=302,L]
```

### Cloudflare

Usa Cloudflare Workers o Page Rules para redirigir todo el tráfico:

```javascript
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  return Response.redirect(
    'https://mantenimiento.tu-dominio.com/?status=maintenance&app=Mi%20App',
    302
  )
}
```

## 🎨 Personalización

Si quieres modificar los mensajes, colores o agregar nuevos estados, edita el objeto `statusConfig` en el JavaScript dentro de `index.html`:

```javascript
const statusConfig = {
    miNuevoEstado: {
        icon: '🎯',
        iconClass: 'mi-clase',
        title: 'Mi Título',
        message: 'Mi mensaje principal',
        subMessage: 'Mi submensaje',
        detailsMessage: 'Detalles adicionales'
    }
};
```

Y agrega los estilos CSS correspondientes para `.icon.mi-clase`.

## 📱 Compatibilidad

- ✅ Chrome/Edge (últimas versiones)
- ✅ Firefox (últimas versiones)
- ✅ Safari (iOS y macOS)
- ✅ Opera
- ✅ Navegadores móviles

## 🤝 Contribuciones

Las sugerencias y mejoras son bienvenidas. Siéntete libre de abrir un issue o pull request.

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.

---

**Tip**: Guarda la URL de tu página de mantenimiento en tu gestor de contraseñas o documentación interna para tenerla siempre a mano cuando la necesites. 🚀
