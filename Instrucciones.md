# Tarea 1: Mi Primer Documento LaTeX y Flujo de Git

## 📋 Objetivos

En esta tarea aprenderás a:
- Compilar documentos LaTeX con TeXstudio
- Colaborar en equipo usando Git y ramas
- Resolver conflictos de merge
- Estructurar proyectos LaTeX profesionales

## 📝 Instrucciones

### Paso 1: Abre y Compila el Documento LaTeX

1. Abre **TeXstudio**
2. Carga el archivo `reporte.tex` desde tu repositorio
3. Compila el documento presionando `Ctrl+Shift+F5` o desde el menú `Tools → Compile`
4. Verifica que se genere el PDF sin errores

### Paso 2: Modifica la Portada en Equipo

1. En el mismo archivo `reporte.tex`, localiza la sección de portada
2. **Con tu equipo**, cambien los siguientes elementos:
   - Título del documento
   - Nombre de los autores
   - Fecha
   - Institución (ITH)
3. Cada miembro del equipo debe hacer un **commit** con estos cambios:
   ```bash
   git add reporte.tex
   git commit -m "Modificada portada del documento"
   git push origin main
   ```

### Paso 3: Crea la Sección "Espectativa"

1. En el documento principal `reporte.tex`, añade una nueva sección:
   ```latex
   \section{Espectativa}
   ```

### Paso 4: Crea Archivos Individuales en la Carpeta de Secciones

1. En la carpeta `secciones/`, cada miembro del equipo debe crear un archivo `.tex` con su nombre:
   ```
   secciones/
   ├── juan.tex
   ├── maria.tex
   └── carlos.tex
   ```

2. En cada archivo, escribe una breve descripción de lo que esperas aprender en este curso (3-5 líneas). Ejemplo para `secciones/juan.tex`:
   ```latex
   Espero aprender los fundamentos de la instrumentación y control de sistemas. 
   Quiero entender cómo funcionan los sensores y actuadores, 
   y cómo programar un Arduino para aplicaciones prácticas.
   ```

3. **Importante**: Cada miembro debe trabajar en su propia rama:
   ```bash
   git checkout -b seccion-[tu-nombre]
   # Edita tu archivo secciones/[tu-nombre].tex
   git add secciones/[tu-nombre].tex
   git commit -m "Añadida sección de espectativa de [tu-nombre]"
   git push origin seccion-[tu-nombre]
   ```

### Paso 5: Incluye los Archivos en el Documento Principal

En `reporte.tex`, dentro de la sección "Espectativa", incluye los archivos de tus compañeros usando:

```latex
\section{Espectativa}

\subsection{Mi Perspectiva}
\input{secciones/[tu-nombre].tex}

\subsection{Perspectiva de [Compañero 1]}
\input{secciones/[nombre-compañero1].tex}

\subsection{Perspectiva de [Compañero 2]}
\input{secciones/[nombre-compañero2].tex}
```

### Paso 6: Resuelve un Conflicto de Merge Intencionalmente

Para aprender a resolver conflictos:

1. **Miembro A** crea una rama, modifica `reporte.tex` (añade un párrafo en la introducción) y hace push:
   ```bash
   git checkout -b intro-mejora
   # Edita reporte.tex
   git add reporte.tex
   git commit -m "Mejorada la introducción"
   git push origin intro-mejora
   ```

2. **Miembro B** (sin actualizar) también modifica la **misma línea** de `reporte.tex`, hace commit y push en su rama:
   ```bash
   git checkout -b intro-alternativa
   # Edita reporte.tex en el MISMO lugar que Miembro A
   git add reporte.tex
   git commit -m "Alternativa para la introducción"
   git push origin intro-alternativa
   ```

3. **Desde GitHub**, crea un Pull Request e **intenta hacer merge**. GitHub detectará el conflicto.

4. **Resuelve el conflicto localmente**:
   ```bash
   git checkout main
   git pull origin main
   git merge intro-mejora
   # Git mostrará conflicto
   ```

5. Abre `reporte.tex` en TeXstudio. Verás marcas como:
   ```
   <<<<<<< HEAD
   Tu versión aquí
   =======
   Versión de la otra rama
   >>>>>>> intro-mejora
   ```

6. **Elige qué mantener**, elimina las marcas, y completa el merge:
   ```bash
   git add reporte.tex
   git commit -m "Conflicto resuelto en la introducción"
   git push origin main
   ```

## ✅ Checklist de Entrega

- [ ] El documento `reporte.tex` compila sin errores
- [ ] La portada fue modificada en equipo
- [ ] Existe la sección "Espectativa"
- [ ] Cada miembro tiene su archivo en `secciones/`
- [ ] Los archivos están incluidos en el documento principal con `\input{}`
- [ ] Hay **al menos 3 commits** del equipo
- [ ] Hay **al menos 1 merge con conflicto resuelto**
- [ ] El historial de Git muestra claramente el trabajo colaborativo

## 📌 Consejos

- Compila frecuentemente para detectar errores rápidamente
- Usa mensajes descriptivos en tus commits
- Coordina con tu equipo para evitar conflictos innecesarios
- El conflicto intencionado es parte del aprendizaje, ¡no tengas miedo!
