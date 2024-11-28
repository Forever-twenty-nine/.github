## **Guía Rápida: Herramientas de Build y Preview en Astro**

### 1. **Construir el Proyecto**
   - Utiliza el comando:
     ```bash
     npm run build
     ```
   - **Qué hace:** Genera los archivos estáticos del sitio en la carpeta `dist` (o la que hayas configurado).
   - **Propósito:** Preparar el proyecto para ser desplegado en un servidor.

---

### 2. **Previsualizar el Proyecto Construido**
   - Utiliza el comando:
     ```bash
     npm run preview
     ```
   - **Qué hace:** Inicia un servidor local que sirve los archivos generados en la carpeta `dist`.
   - **Propósito:** Ver cómo se verá tu proyecto en un entorno de producción.

---

### 3. **Consideraciones Adicionales**
   - **Configurar rutas base (opcional):** Si tu sitio se despliega en un subdirectorio, asegúrate de configurar `base` en el archivo `astro.config.mjs`:
     ```javascript
     import { defineConfig } from 'astro/config';

     export default defineConfig({
       base: '/nombre-del-subdirectorio/', 
     });
     ```

   - **Archivos de salida:** Todos los archivos construidos estarán en la carpeta `dist` (por defecto). Si necesitas cambiar esta carpeta, ajusta la configuración en `astro.config.mjs`:
     ```javascript
     outDir: './nombre-de-la-carpeta'
     ```

---

### Resumen de Comandos
| **Comando**          | **Acción**                                      |
|-----------------------|------------------------------------------------|
| `npm run build`       | Construye el proyecto y genera los archivos.   |
| `npm run preview`     | Previsualiza los archivos construidos.         |

---