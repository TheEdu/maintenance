# 🔧 Página de Mantenimiento

Página web estática para mostrar cuando un servicio no está disponible.

## Uso

```bash
# Mantenimiento (por defecto)
?app=app.test.com.ar&company=focustech.com.ar

# Fuera de servicio
?status=offline&app=api.ejemplo.com&company=Mi%20Empresa

# Actualizaciones
?status=updating&app=dashboard.test.com&company=TechCorp

# Mensaje personalizado
?status=custom&app=portal.com&message=Volvemos%20el%20lunes%208am
```

## Parámetros

| Parámetro | Valores | Default |
|-----------|---------|---------|
| `status` | `maintenance`, `offline`, `updating`, `custom` | `maintenance` |
| `app` | Nombre de la app/dominio | `Servicio` |
| `company` | Nombre de la empresa | - |
| `message` | Texto personalizado (solo con `status=custom`) | - |

**Nota:** Los estados predefinidos solo muestran el título. Para un mensaje usa `status=custom`.
