# Frontend para Pronóstico Clima Jauja-Huancayo

Este repositorio contiene el frontend para la aplicación de pronóstico del clima de Jauja-Huancayo, diseñado para ser desplegado en Vercel e integrado con la aplicación en Hugging Face Spaces.

## Instrucciones de Despliegue

### 1. Preparar Archivos

Antes de desplegar en Vercel, asegúrate de:

1. Actualizar la URL de iframe en `index.html` para que apunte a tu espacio en Hugging Face:
   ```html
   <iframe src="https://huggingface.co/spaces/TU_USUARIO/prediccion-clima-jauja" ...>
   ```

2. Actualizar los enlaces en el footer:
   ```html
   <a href="https://github.com/TU_USUARIO/prediccion-clima-jauja" ...>
   <a href="https://huggingface.co/spaces/TU_USUARIO/prediccion-clima-jauja" ...>
   ```

### 2. Despliegue en Vercel

#### Opción 1: Usando la interfaz web

1. Crear una cuenta en [Vercel](https://vercel.com) si aún no tienes una
2. Iniciar sesión y hacer clic en "Add New..." → "Project"
3. Conectar con tu cuenta de GitHub y seleccionar el repositorio
4. Configurar el proyecto:
   - Root Directory: `frontend_vercel` (si tienes todo el proyecto en GitHub)
   - Build Command: Dejar en blanco
   - Output Directory: `.`
5. Hacer clic en "Deploy"

#### Opción 2: Usando la CLI de Vercel

1. Instalar la CLI de Vercel:
   ```bash
   npm install -g vercel
   ```

2. Iniciar sesión:
   ```bash
   vercel login
   ```

3. Navegar a la carpeta `frontend_vercel` y ejecutar:
   ```bash
   vercel
   ```

4. Seguir las instrucciones en la terminal

### 3. Configuración de CORS (ya incluida)

El archivo `vercel.json` ya incluye configuraciones para permitir que tu frontend se comunique correctamente con Hugging Face Spaces a través del iframe:

```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "Content-Security-Policy",
          "value": "frame-ancestors 'self' https://huggingface.co"
        },
        {
          "key": "X-Frame-Options",
          "value": "ALLOW-FROM https://huggingface.co"
        }
      ]
    }
  ]
}
```

## Estructura de Archivos

- `index.html` - Página principal con la interfaz de usuario
- `package.json` - Información del proyecto para Vercel
- `vercel.json` - Configuraciones para el despliegue en Vercel
- `README.md` - Este archivo de instrucciones

## Personalización

Puedes personalizar el frontend modificando:

- Colores y estilos en la sección CSS dentro de `index.html`
- Textos descriptivos en las diferentes secciones
- Imágenes (la imagen del héroe y otras que quieras añadir)

## Solución de Problemas

- **El iframe no carga:** Asegúrate de que tu espacio en Hugging Face esté correctamente configurado y funcionando
- **Problemas de CORS:** Si hay problemas con el iframe, verifica las configuraciones en `vercel.json`
- **Errores 404:** Asegúrate de que la estructura de archivos sea exactamente como se describe aquí

## Licencia

Este proyecto está disponible bajo la licencia MIT. 