
# **Guía de trabajo con ramas y Pull Requests**

Esta guía establece las reglas y pasos para trabajar con ramas y Pull Requests en nuestro repositorio de GitHub. El objetivo es mantener un flujo organizado y colaborar eficazmente.

---

## **Estructura del repositorio**

### **1. Ramas principales**

- **`main`:**
  - Contiene el código estable y listo para producción.
  - **Ningún cambio se realiza directamente en esta rama.**
  - Todos los cambios deben pasar por un **Pull Request (PR)** desde una rama temporal.

---

### **2. Ramas temporales**

Existen dos tipos de ramas temporales para desarrollar nuevas funcionalidades o corregir errores:

1. **Feature branches**:
   - Se crean para añadir nuevas funcionalidades o realizar mejoras.
   - Convención para nombrar: `feature/nombre-descriptivo`.
   - Ejemplo: `feature/login-usuario`.

2. **Bugfix branches**:
   - Se crean para solucionar errores específicos.
   - Convención para nombrar: `bugfix/nombre-descriptivo`.
   - Ejemplo: `bugfix/corregir-boton`.

---

## **Flujo de trabajo**

### **1. Crear una rama temporal**

Antes de realizar cualquier cambio, crea una nueva rama desde `main`:

```bash
git checkout main         # Asegúrate de estar en la rama main
git pull origin main      # Obtén los últimos cambios de main
git checkout -b feature/nombre-descriptivo
```

Ejemplo:
```bash
git checkout -b feature/login-usuario
```

---

### **2. Realizar cambios y confirmarlos**

Realiza los cambios necesarios en tu rama y guarda tus avances con **commits** claros:

```bash
git add .
git commit -m "Descripción breve de los cambios"
```

Ejemplo:
```bash
git commit -m "Añade formulario de login y validación básica"
```

---

### **3. Subir la rama al repositorio remoto**

Cuando hayas avanzado lo suficiente o terminado tu tarea, sube la rama a GitHub:

```bash
git push origin feature/nombre-descriptivo
```

---

### **4. Crear un Pull Request**

1. Ve a GitHub y selecciona la rama que acabas de subir.
2. Haz clic en **Pull Requests** > **New Pull Request**.
3. Configura el PR para fusionar tu rama en `main`.
4. Agrega un título claro y una descripción explicando los cambios realizados.

---

### **5. Revisar el Pull Request**

- **Autor del PR:**
  - Asegúrate de que el PR esté limpio y listo para revisión.
  - Soluciona los comentarios o sugerencias que surjan.

- **Revisor:**
  - Verifica que los cambios funcionen correctamente y cumplan con los requisitos.

---

### **6. Fusionar el Pull Request**

Una vez aprobado:

1. Haz clic en **Merge Pull Request** en GitHub.
2. Elimina la rama temporal desde GitHub para mantener el repositorio limpio.

---

### **7. Actualizar tu rama local**

Después de fusionar un PR, actualiza tu rama `main` localmente para reflejar los últimos cambios:

```bash
git checkout main
git pull origin main
```

---

## **Reglas de colaboración**

1. **No modificar directamente `main`:**
   - Todos los cambios deben pasar por un PR.

2. **Escribir commits claros:**
   - Usa descripciones que expliquen el propósito de los cambios.

3. **Un PR por tarea:**
   - Cada PR debe resolver una sola tarea o problema específico.

4. **Elimina ramas temporales:**
   - Una vez fusionadas, elimina las ramas para mantener el repositorio ordenado.

---

## **Ejemplo práctico**

Supongamos que queremos implementar un formulario de login:

1. Crear una rama:
   ```bash
   git checkout -b feature/login-usuario
   ```

2. Hacer cambios y confirmarlos:
   ```bash
   git add .
   git commit -m "Añade formulario de login con validaciones"
   ```

3. Subir la rama y crear un PR:
   ```bash
   git push origin feature/login-usuario
   ```

4. Revisar y fusionar el PR:
   - Crear el PR desde GitHub.
   - Revisar con tu compañero.
   - Fusionar el PR cuando esté listo.

5. Eliminar la rama:
   ```bash
   git branch -d feature/login-usuario
   git push origin --delete feature/login-usuario
   ```

---

Siguiendo esta guía, podremos colaborar de manera eficiente y mantener un flujo de trabajo limpio y organizado. 

Si tienes dudas, revisemos un ejemplo juntos. 😊