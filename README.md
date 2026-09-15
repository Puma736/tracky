# Everyday — Agenda ejecutiva (proyecto "tracky")

Aplicación de una sola página (HTML + CSS + JavaScript, sin dependencias ni servidor).
Se abre haciendo doble clic en `everyday.html` con Chrome, Edge, Firefox o Safari actualizados.

## Archivos

| Archivo | Descripción |
|---|---|
| `everyday.html` | La aplicación completa, versión actual. |
| `respaldo/everyday_original.html` | Versión original recibida por WeTransfer (13/09/2026), sin cambios. |
| `capturas/*.png` | Capturas de cada vista de la aplicación. |
| `README.md` | Este documento. |

## Vistas

Hoy · Semana · Mes · Año · Reportes · Rendimiento · Panel BI · Privacidad

## Cambios realizados el 13/09/2026

1. **Corrección**: el formulario "+ Nueva rutina" y el selector de días aparecían siempre visibles
   (faltaba la regla `[hidden]{display:none!important}`).
2. **PIN + cifrado local**: al abrir la app se crea/pide un PIN de 4–8 dígitos. Todos los datos se
   cifran con AES-256-GCM (clave derivada con PBKDF2-SHA256, 250.000 iteraciones) antes de guardarse
   en `localStorage` bajo la clave `everyday.v2`. La clave nunca se almacena. Incluye bloqueo manual,
   bloqueo automático por inactividad, cambio de PIN, copia de seguridad cifrada, restauración y
   borrado total. Los datos de la versión anterior (`everyday.v1`, en texto plano) se migran y se
   eliminan automáticamente al crear el PIN.
3. **Filtro de contenido**: no se pueden guardar tareas, notas, objetivos, metas ni rutinas con
   términos de sustancias ilícitas o controladas, bullying/acoso o actividades indecentes.
   Coincidencia por palabra completa, sin distinguir mayúsculas ni acentos. Se pueden añadir
   términos propios desde la vista Privacidad.
4. **Semana dinámica**: encabezado de cada día abre la vista diaria; resumen semanal en vivo
   (tareas, rutinas, prioridad alta, vencidas); progreso por día; casillas de completado; tareas
   vencidas marcadas; rutinas del día visibles y marcables desde la semana.
5. **Recordatorio por WhatsApp** (vista Reportes): genera un mensaje con los pendientes de hoy,
   de mañana, de la semana o de las tareas urgentes y lo abre en WhatsApp (`wa.me`), con número
   opcional. El mensaje también se copia al portapapeles.
6. **Notificaciones automáticas** (vista Reportes): aviso previo a cada tarea con hora, resumen
   diario a la hora configurada y recordatorio de rutinas pendientes por la tarde. Funcionan
   mientras la app esté abierta en una pestaña y desbloqueada.

## Privacidad

La aplicación no envía información a ningún servidor. La única conexión externa es la descarga de
la tipografía Manrope desde Google Fonts (si no hay internet se usa la fuente del sistema).
Si se olvida el PIN los datos no se pueden recuperar: conviene generar copias de seguridad
periódicas desde la vista Privacidad.
