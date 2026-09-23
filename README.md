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

No hace falta instalar nada ni compilar. Funciona sin conexión salvo el envío del correo.

## Uso

1. Complete los datos de la revisión (revisor, fecha, identificación de la escalera, tipo, correo de destino).
2. Responda **todos** los puntos del checklist: Clear / Conforme / No conforme / No aplica.
3. Si marca No conforme o Clear, indique observaciones en ese punto.
4. El resultado se calcula solo: **APTO** o **NO APTO / RETIRAR DE USO**.
5. Si es NO APTO, confirme que la escalera está retirada o señalizada.
6. Pulse **Enviar informe** (o **Descargar informe (HTML)** para una copia local).

## Envío de correo (FormSubmit)

El botón **Enviar informe** envía el informe por AJAX a:

`https://formsubmit.co/ajax/` + el correo que escriba el trabajador en el formulario.

- **No hay correo fijo** en el código: el destinatario se indica en cada envío.
- La **primera vez** que se envía a una dirección nueva, FormSubmit suele mandar un correo de **activación/confirmación** al destinatario. Hasta que confirme ese enlace, los informes pueden no llegar. Revise también spam/correo no deseado.
- Después de la confirmación, los envíos siguientes a esa dirección suelen llegar automáticamente.
- El asunto del mensaje sigue el patrón: `Informe revisión escalera [ID] — [APTO/NO APTO]`.

Si el envío falla (sin red, bloqueo del navegador, etc.), use **Descargar informe (HTML)** y remítalo por otro medio.

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
