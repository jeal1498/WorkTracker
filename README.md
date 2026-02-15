# ControlCheck 🚐

**App de control de asistencia y comisiones para operadores de transporte turístico.**

PWA (Progressive Web App) de un solo archivo HTML que funciona offline en cualquier dispositivo — sin servidores, sin instalación, sin dependencias externas.

---

## ✨ Funcionalidades

### Registro Diario
- Registro rápido de jornada vía modal QR con hora de entrada/salida
- Estados: Trabajado, Descanso, Permiso, Festivo, Falta
- Cálculo automático de horas (incluye turnos nocturnos que cruzan medianoche)
- Auto-detección de días festivos oficiales de México 2026 con tarifa especial
- Campos deshabilitados automáticamente en días de descanso

### Comisiones
- Comisiones preconfiguradas por ruta y tipo de vehículo (Crafter/Sprinter, Suburban/Navigator, Autobús)
- Agregar comisiones personalizadas con monto libre
- Modal de confirmación antes de registrar cada comisión
- Registro rápido post-jornada con sugerencia automática

### Calendario
- Vista mensual con indicadores de color por estado
- Monto diario visible en cada celda
- Navegación por mes con selector rápido
- Click en cualquier día para crear o editar registro (pasado y futuro)
- Mini-calendario integrado en la pestaña de Resumen

### Dashboard / Resumen
- Detección automática del periodo de comisión quincenal en curso
- Total a recibir con desglose: trabajo base, comisiones, gastos
- Indicador de día de cobro (ej. "Cobro: día 27")
- Actividad del periodo con barras de progreso por estado
- Tarjetas de estadísticas: días trabajados, comisiones, mejor día, horas promedio

### Historial
- Filtros colapsables por periodo, estado y búsqueda de texto
- Mini resumen: días, comisiones netas, total
- Tarjetas compactas con estado, unidad, horario y tags de comisión/gasto
- Modal de detalle al tocar cada registro
- Selección múltiple para eliminación masiva

### Exportación
- **PDF** y **CSV** con nombre y número de empleado del usuario
- Selector de periodo de comisiones (24 quincenas del año)
- Formato especial para reporte de comisiones con desglose por ruta
- Formato de nómina con tabla de registros
- Respaldo/restauración completa en JSON

### Periodos de Comisiones
- 24 periodos quincenales del calendario oficial 2026
- Fechas exactas de inicio, corte, entrega de comisiones y día de pago
- Filtrado automático de registros por periodo activo

---

## 🛠️ Stack Técnico

| Tecnología | Uso |
|---|---|
| **React 18** | UI reactiva (cargado desde CDN) |
| **Tailwind CSS 3** | Estilos utility-first |
| **Lucide React** | Iconografía |
| **jsPDF + AutoTable** | Generación de PDFs |
| **LocalStorage** | Persistencia de datos offline |
| **Service Worker** | Caché offline (PWA) |

**Archivo único** — Todo el código (HTML, CSS, JS, React) está contenido en `index-3.html` (~306 KB, ~4,500 líneas).

---

## 📱 Instalación

### Opción 1: Uso directo
1. Descarga `index-3.html`
2. Ábrelo en cualquier navegador móvil o de escritorio
3. Listo — funciona sin conexión a internet

### Opción 2: Instalar como PWA
1. Abre el archivo en Chrome (Android) o Safari (iOS)
2. Toca **"Agregar a pantalla de inicio"** / **"Instalar app"**
3. La app aparecerá como ícono en tu dispositivo

### Opción 3: Hosting (GitHub Pages)
1. Sube `index-3.html` como `index.html` a un repositorio
2. Activa GitHub Pages en Settings → Pages → Branch: main
3. Accede desde `https://tu-usuario.github.io/tu-repo/`

---

## 🎨 Temas

La app detecta automáticamente el tema del sistema operativo:
- **Modo oscuro** — Fondo negro con acentos esmeralda
- **Modo claro** — Fondo blanco/gris con contraste adaptado

No requiere configuración manual. Cambia en tiempo real al cambiar el tema del dispositivo.

---

## ♿ Accesibilidad

- Fuentes mínimas de 12px (WCAG AA)
- Áreas de toque mínimas de 44×44px
- Contraste de texto validado para modo claro y oscuro
- Etiquetas ARIA en botones de navegación y cierre
- Placeholders con contraste suficiente

---

## 📊 Estructura de Datos

Cada registro se guarda en LocalStorage con esta estructura:

```json
{
  "id": 1707900000000,
  "date": "2026-02-14",
  "status": "worked",
  "unit": "UV07 - Crafter/Sprinter/Transporter/Urvan",
  "unitType": "crafter",
  "startTime": "08:00",
  "endTime": "16:00",
  "hoursWorked": 8,
  "baseSalary": 383.11,
  "commissions": [
    { "name": "Cancún Centro", "amount": "60.00" },
    { "name": "Puerto Morelos", "amount": "140.00" }
  ],
  "totalComm": 200,
  "expenses": [],
  "totalExp": 0,
  "description": ""
}
```

---

## 🗓️ Días Festivos Oficiales 2026

| Fecha | Nombre |
|---|---|
| 1 Enero | Año Nuevo |
| 2 Febrero | Día de la Constitución |
| 16 Marzo | Natalicio de Benito Juárez |
| 1 Mayo | Día del Trabajo |
| 16 Septiembre | Día de la Independencia |
| 16 Noviembre | Día de la Revolución |
| 25 Diciembre | Navidad |

Al registrar trabajo en estas fechas, el estado cambia automáticamente a **Festivo** con tarifa especial ($1,149.33).

---

## 📋 Tarifas Base (por defecto)

| Estado | Tarifa diaria |
|---|---|
| Trabajado | $383.11 |
| Descanso | $383.11 |
| Permiso | $383.11 |
| **Festivo** | **$1,149.33** |
| Falta | $0.00 |

Las tarifas son editables desde el área de configuración (ícono de usuario).

---

## 🔒 Privacidad

- **Sin servidor** — todos los datos permanecen en tu dispositivo
- **Sin tracking** — no hay analytics, cookies ni telemetría
- **Sin cuenta** — no requiere registro ni login
- **Respaldo manual** — exporta/importa tus datos en JSON cuando quieras

---

## 📄 Licencia

MIT License — uso libre para fines personales y comerciales.

---

<p align="center">
  <b>ControlCheck</b> — Hecho para operadores de transporte turístico en Cancún 🌴
</p>
