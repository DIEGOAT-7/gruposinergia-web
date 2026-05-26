# Grupo Sinergia Consultores — Sitio Web

Sitio web corporativo para **Grupo Sinergia Consultores S.A.S.**, firma especializada en Propiedad Horizontal. Desarrollado por [La Sucursal del Cielo Agency](mailto:diegoortizare@gmail.com).

## Stack

- **Framework:** Astro 6 (SSG — salida 100% estática)
- **CSS:** Tailwind CSS v4
- **Node:** v22 (via nvm)
- **Package manager:** pnpm

## Comandos

Todos los comandos se corren desde este directorio (`web/`):

```bash
pnpm dev --host --port 4322   # servidor local → http://100.67.113.83:4322
pnpm build                    # build de producción → dist/
pnpm preview                  # previsualizar el build
pnpm astro check              # type-check de archivos .astro
```

## Páginas

| Ruta | Archivo | Estado |
|---|---|---|
| `/` | `src/pages/index.astro` | ✅ Listo |
| `/quienes-somos` | `src/pages/quienes-somos.astro` | ✅ Listo |
| `/servicios` | `src/pages/servicios.astro` | ✅ Listo |
| `/servicios/recibo-zonas-comunes` | `src/pages/servicios/recibo-zonas-comunes.astro` | ✅ Listo |
| `/contacto` | `src/pages/contacto.astro` | ✅ Listo |
| `/preguntas-frecuentes` | `src/pages/preguntas-frecuentes.astro` | 🔲 Pendiente |
| `/blog` | `src/pages/blog/index.astro` | 🔲 Pendiente |

## ⚠️ Pendientes antes de lanzar

### 1. Formspree — Formulario de contacto
El formulario en `/contacto` necesita un endpoint real para enviar los mensajes.

**Pasos:**
1. Crear cuenta en [formspree.io](https://formspree.io) con el correo del cliente
2. Crear un nuevo form ("Contacto Grupo Sinergia")
3. Copiar el endpoint generado (formato: `https://formspree.io/f/xxxxxxxx`)
4. Reemplazar en `src/pages/contacto.astro` línea 8:
   ```js
   const FORM_ENDPOINT = 'https://formspree.io/f/XXXXXXXX'
   ```

### 2. Calendly — Agendamiento en línea
El embed de Calendly en `/contacto` necesita el enlace real del calendario.

**Pasos:**
1. Crear cuenta en [calendly.com](https://calendly.com) con el correo del cliente
2. Conectar Google Calendar o Outlook
3. Crear evento "Consulta inicial" (30–45 min)
4. Copiar el enlace del evento (formato: `https://calendly.com/usuario/consulta`)
5. Reemplazar en `src/pages/contacto.astro` línea ~215:
   ```html
   data-url="https://calendly.com/USUARIO-PENDIENTE"
   ```

### 3. WhatsApp — Número de contacto
El botón de WhatsApp usa un número placeholder en todo el sitio.

**Pasos:**
1. Confirmar el número de WhatsApp del cliente (formato: `57` + número sin espacios)
2. Reemplazar en `src/pages/contacto.astro` línea 12:
   ```js
   const WA_NUMBER = '57XXXXXXXXXX'
   ```
3. Actualizar también los `href="https://wa.me/57"` en:
   - `src/pages/index.astro`
   - `src/pages/servicios/recibo-zonas-comunes.astro`

### 4. Logo SVG
Actualmente el header usa texto como wordmark. Pendiente extraer el logo a SVG para usarlo como imagen.

- Fuente: `../logos_gs/logo_GrupoSinergia.pdf`
- Reemplazar el wordmark en `src/components/Header.astro`

### 5. Dominio y despliegue en Hostinger
- Registrar dominio (`gruposinergia.com.co` o `gruposinergiaconsultores.com`)
- Subir el contenido de `dist/` vía FTP o Git deployment en Hostinger
- Configurar SSL

### 6. Correos corporativos
Reemplazar los correos Yahoo actuales (`sinergiaci@yahoo.com`) por correos con dominio propio una vez registrado.
- Actualizar en `src/components/Footer.astro`
- Actualizar en `src/pages/contacto.astro`
