# Grupo Sinergia Consultores — Sitio Web

Sitio web corporativo para **Grupo Sinergia Consultores S.A.S.**, firma especializada en Propiedad Horizontal. Desarrollado por [La Sucursal del Cielo Agency](mailto:diegoortizare@gmail.com).

**Producción:** [gruposinergiaconsultores.com](https://gruposinergiaconsultores.com)

## Stack

- **Framework:** Astro 6 (SSG — salida 100% estática)
- **CSS:** Tailwind CSS v4
- **Node:** v22 (via nvm)
- **Package manager:** pnpm
- **Hosting:** Netlify (deploy automático desde `main`)

## Desarrollo local

Todos los comandos se corren desde este directorio (`web/`):

```bash
pnpm install                  # instalar dependencias
pnpm dev --host --port 4322   # servidor local → http://100.67.113.83:4322
pnpm build                    # build de producción → dist/
pnpm preview                  # previsualizar el build
pnpm astro check              # type-check de archivos .astro
```

## Deploy

Cada `git push` a `main` dispara un redeploy automático en Netlify. No se requiere ningún paso manual.

```
Editar código → git push origin main → Netlify redespliega en ~2 min
```

## Páginas

| Ruta | Archivo | Estado |
|---|---|---|
| `/` | `src/pages/index.astro` | ✅ |
| `/quienes-somos` | `src/pages/quienes-somos.astro` | ✅ |
| `/servicios` | `src/pages/servicios.astro` | ✅ |
| `/servicios/recibo-zonas-comunes` | `src/pages/servicios/recibo-zonas-comunes.astro` | ✅ |
| `/contacto` | `src/pages/contacto.astro` | ✅ |
| `/preguntas-frecuentes` | `src/pages/preguntas-frecuentes.astro` | ✅ |
| `/blog` | `src/pages/blog/index.astro` | ✅ |

## Pendientes — requieren datos del cliente

### 1. Formspree — Formulario de contacto
El formulario en `/contacto` envía a un endpoint placeholder.

1. Crear cuenta en [formspree.io](https://formspree.io) con el correo del cliente
2. Crear form "Contacto Grupo Sinergia" y copiar el endpoint
3. Reemplazar en `src/pages/contacto.astro` línea 8:
   ```js
   const FORM_ENDPOINT = 'https://formspree.io/f/XXXXXXXX'
   ```

### 2. Calendly — Agendamiento en línea
1. Crear cuenta en [calendly.com](https://calendly.com) con el correo del cliente
2. Crear evento "Consulta inicial" (30–45 min) y copiar el enlace
3. Reemplazar en `src/pages/contacto.astro` línea ~215:
   ```html
   data-url="https://calendly.com/USUARIO-PENDIENTE"
   ```

### 3. WhatsApp — Número de contacto
1. Confirmar número del cliente (formato: `57` + número sin espacios ni guiones)
2. Reemplazar en `src/pages/contacto.astro` línea 12:
   ```js
   const WA_NUMBER = '57XXXXXXXXXX'
   ```
3. Actualizar también en:
   - `src/pages/index.astro`
   - `src/pages/servicios/recibo-zonas-comunes.astro`

### 4. Correos corporativos
Reemplazar los correos Yahoo (`sinergiaci@yahoo.com`) cuando el cliente tenga correos con dominio propio:
- `src/components/Footer.astro`
- `src/pages/contacto.astro`
