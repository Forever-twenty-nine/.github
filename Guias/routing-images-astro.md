### **Tutorial: Manejo de Imágenes en Astro para GitHub Pages**

#### **1. El Problema**
Cuando desplegamos un proyecto en GitHub Pages, nuestra aplicación no está alojada en la raíz del dominio (`/`), sino en un subdirectorio como `/mi-repo`. Si las rutas de las imágenes son relativas (`/imagen.webp`), el navegador intentará buscar el archivo en `https://mi-dominio.com/imagen.webp` en lugar de `https://mi-dominio.com/mi-repo/imagen.webp`, lo que causa un error 404.

---

#### **2. Solución: Configurar el Prefijo de Base**

Astro ofrece una configuración para manejar esto: **`base` y `import.meta.env.BASE_URL`**.

- `base`: Es el prefijo del subdirectorio donde tu proyecto estará alojado (por ejemplo, `/mi-repo`).
- `import.meta.env.BASE_URL`: Contiene automáticamente el valor de `base`.

---

#### **3. Configuración de Astro**

Modifica el archivo `astro.config.mjs` para especificar el valor correcto de `base` y `site`:

```javascript
import { defineConfig } from 'astro/config';
import tailwind from '@astrojs/tailwind';
import compress from 'astro-compress';

export default defineConfig({
  base: '/mi-repo', // Cambia 'mi-repo' por el nombre de tu repositorio
  site: 'https://mi-usuario.github.io/mi-repo', // Cambia por tu URL en GitHub Pages
  integrations: [tailwind(), compress()],
});
```

Esto asegura que durante el build, Astro incluya el prefijo `/mi-repo` en las rutas generadas.

---

#### **4. Uso de `import.meta.env.BASE_URL` en Imágenes**

Cuando defines las rutas de las imágenes, asegúrate de incluir el prefijo base dinámicamente. Por ejemplo:

**ANTES (sin prefijo base):**

```tsx
<Image src="/imagen.webp" alt="Descripción" />
```

**DESPUÉS (con prefijo base):**

```tsx
<Image src={`${import.meta.env.BASE_URL}/imagen.webp`} alt="Descripción" />
```

Esto genera una ruta completa como:

```
https://mi-usuario.github.io/mi-repo/imagen.webp
```

Ahora las imágenes se cargarán correctamente en GitHub Pages.

---

#### **5. Estructura del Proyecto**

Organiza tus imágenes en carpetas para facilitar su gestión. Por ejemplo:

```
src/
  assets/
    images/
      hero.webp
```

Luego, utiliza rutas relativas en tu código:

```tsx
const img = "/assets/images/hero.webp";

<Image
  src={`${import.meta.env.BASE_URL}${img}`}
  alt="Hero Image"
  width={600}
  height={400}
/>
```

---

#### **6. Probar Localmente**

Cuando trabajas localmente, las rutas con `import.meta.env.BASE_URL` aún funcionan porque el prefijo base por defecto es `/`. Para probar con un subdirectorio similar a GitHub Pages:

```bash
npx serve dist --prefix /mi-repo
```

Esto simula el comportamiento en GitHub Pages.

---

#### **7. Verificar el Despliegue**

1. Ejecuta el build:
   ```bash
   npm run build
   ```

2. Sube los archivos de `dist` a la rama `gh-pages`.

3. Verifica las rutas de las imágenes en tu aplicación publicada en GitHub Pages. Asegúrate de que las rutas incluyan el prefijo `https://mi-usuario.github.io/mi-repo/`.

---

### **Por qué Funciona**
- **`base` en `astro.config.mjs`**: Le dice a Astro que agregue el prefijo `/mi-repo` a todas las rutas generadas, como imágenes, CSS, y JS.
- **`import.meta.env.BASE_URL`**: Se asegura de que las rutas relativas respeten el prefijo base configurado, evitando errores 404 al buscar recursos en subdirectorios.