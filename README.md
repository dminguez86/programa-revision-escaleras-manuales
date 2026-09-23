# Revisión de escaleras manuales

Aplicación web de una sola página (HTML) para inspecciones de escaleras de mano según RD 2177/2004, UNE-EN 131 y práctica PRL (INSST / AFESPO). Marca PREVIJOB.

## Cómo abrirla

1. **Recomendado:** sírvala por HTTPS (p. ej. Render) o con un servidor local:
   ```bash
   cd programa-revision-escaleras
   python3 -m http.server 8080
   ```
   y entre en `http://localhost:8080`.
2. También puede abrir `index.html` con doble clic (`file://`), pero **la generación de PDF usa una biblioteca desde CDN** (`html2pdf.js`). En `file://` muchos navegadores bloquean ese script: use HTTPS/Render (o un servidor local con red) para descargar/enviar el informe PDF.

El formulario, el checklist y la foto funcionan sin backend. El envío usa la aplicación de correo del dispositivo (`mailto:`); el informe completo va en un **PDF** que hay que adjuntar.

## Uso

1. Complete los datos de la revisión (revisor, fecha, identificación de la escalera, tipo, correo de destino).
2. (Opcional) Añada una **foto de la escalera** con la cámara o desde la galería; se comprime e incluye en el PDF.
3. Responda **todos** los puntos del checklist: Clear / Conforme / No conforme / No aplica.
4. Si marca No conforme o Clear, indique observaciones en ese punto.
5. El resultado se calcula solo: **APTO** o **NO APTO / RETIRAR DE USO**.
6. Si es NO APTO, confirme que la escalera está retirada o señalizada.
7. Pulse **Enviar informe** (o **Descargar informe (PDF)** para una copia local).

## Informe PDF y envío (mailto)

Biblioteca: **html2pdf.js** 0.10.1 (cdnjs; incluye html2canvas + jsPDF).

El botón **Enviar informe**:

1. Valida el formulario.
2. Genera un **PDF** en el navegador (logo PREVIJOB, datos de cabecera, resultado, checklist con observaciones, foto si hay, marca de tiempo).
3. **Descarga** el PDF (`informe-escalera-[id]-[fecha].pdf`).
4. Si el dispositivo lo permite (`navigator.canShare` con archivos), ofrece **compartir** el PDF (Web Share API).
5. Abre la **aplicación de correo** (`mailto:`) con destinatario, asunto y un **resumen** en texto plano, con instrucción clara de **adjuntar el PDF descargado** (`mailto:` no puede adjuntar archivos).

Debe pulsar **Enviar** en esa aplicación para remitir el mensaje. No hay envío automático en segundo plano ni FormSubmit.

También puede usar solo **Descargar informe (PDF)** y enviarlo por otro medio.

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
