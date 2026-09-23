# Revisión de escaleras manuales

Aplicación web de una sola página (HTML) para inspecciones de escaleras de mano según RD 2177/2004, UNE-EN 131 y práctica PRL (INSST / AFESPO).

## Cómo abrirla

1. Abra el archivo `index.html` con doble clic (navegador: Chrome, Edge, Firefox, Safari).
2. O sírvalo con un servidor estático, por ejemplo:
   ```bash
   cd programa-revision-escaleras
   python3 -m http.server 8080
   ```
   y entre en `http://localhost:8080`.

No hace falta instalar nada ni compilar. El formulario, el checklist y la descarga del informe funcionan **sin conexión**. El envío usa la aplicación de correo del dispositivo (`mailto:`).

## Uso

1. Complete los datos de la revisión (revisor, fecha, identificación de la escalera, tipo, correo de destino).
2. (Opcional) Añada una **foto de la escalera** con la cámara o desde la galería; se comprime e incluye en el informe HTML descargado.
3. Responda **todos** los puntos del checklist: Clear / Conforme / No conforme / No aplica.
4. Si marca No conforme o Clear, indique observaciones en ese punto.
5. El resultado se calcula solo: **APTO** o **NO APTO / RETIRAR DE USO**.
6. Si es NO APTO, confirme que la escalera está retirada o señalizada.
7. Pulse **Enviar informe** (o **Descargar informe (HTML)** para una copia local).

## Envío de correo (mailto)

El botón **Enviar informe**:

1. Valida el formulario.
2. **Descarga** una copia HTML completa del informe.
3. Abre la **aplicación de correo** del dispositivo (`mailto:`) con el destinatario, el asunto y un cuerpo en texto plano.

Debe pulsar **Enviar** en esa aplicación para remitir el mensaje. No hay envío automático en segundo plano.

- El destinatario se indica en cada envío (campo del formulario).
- Asunto: `Informe revisión escalera [ID] — [APTO/NO APTO]`.
- Si el cuerpo es muy largo (límite práctico de `mailto:`), se incluye un **resumen** (datos, resultado, conteo conforme/no conforme, observaciones) y se indica que el detalle está en el HTML descargado, que puede adjuntarse.
- La foto de la escalera (si la hay) va en el HTML descargado, no en el cuerpo `mailto:`; adjunte ese archivo para enviarla.
- Funciona al abrir el archivo en local (`file://`) y desde el teléfono.

También puede usar solo **Descargar informe (HTML)** y enviarlo por otro medio.

## Contenido del checklist

| Sección | Ítems |
|--------|------:|
| 1. Identificación y marcado | 3 |
| 2. Estructura general (largueros) | 4 |
| 3. Peldaños | 4 |
| 4. Zapatas y apoyo | 3 |
| 5. Dispositivos de seguridad | 5 |
| 6. Estado general y limpieza | 3 |
| **Total** | **22** |

Más la sección 7 (resultado, observaciones y confirmación de retirada).

## Aviso

Documento de control interno. No sustituye las instrucciones del fabricante ni la evaluación de riesgos de la empresa.
