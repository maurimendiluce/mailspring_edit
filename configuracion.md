# Configuración de un entorno de trabajo científico

Este documento resume la configuración de un entorno de trabajo para Python, Julia, LaTeX y Quarto utilizando Sublime Text.

---

# 1. Python

## Windows

### Verificar la instalación

```powershell
python --version
where python
```

o

```powershell
py --version
```

---

## Crear un entorno virtual

Desde la carpeta del proyecto:

```powershell
python -m venv .venv
```

o

```powershell
py -m venv .venv
```

---

## Activar el entorno

PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

CMD

```cmd
.venv\Scripts\activate.bat
```

---

## Desactivar

```powershell
deactivate
```

---

## Eliminar un entorno

Simplemente borrar la carpeta

```
.venv
```

---

## Instalar paquetes

Actualizar pip

```powershell
python -m pip install --upgrade pip
```

Instalar paquetes

```powershell
pip install numpy scipy matplotlib pandas jupyter basedpyright
```

---

# Linux

## Crear un entorno virtual

```bash
python3 -m venv .venv
```

---

## Activar

```bash
source .venv/bin/activate
```

---

## Desactivar

```bash
deactivate
```

---

## Eliminar

```bash
rm -rf .venv
```

---

# 2. Julia

Verificar instalación

```bash
julia --version
```

Abrir REPL

```bash
julia
```

Instalar paquetes

```julia
using Pkg

Pkg.add("LanguageServer")
Pkg.add("SymbolServer")
```

---

# 3. LaTeX

Se recomienda instalar

- MiKTeX (Windows)
- TeX Live (Linux)

Configurar MiKTeX para instalar paquetes automáticamente.

Visor PDF recomendado

- SumatraPDF

---

# 4. Quarto

Verificar instalación

```bash
quarto check
```

Renderizar un documento

```bash
quarto render archivo.qmd
```

---

# 5. Sublime Text

## Paquetes instalados

- Package Control
- LSP
- LSP-pyright
- Julia
- LaTeXTools
- GitSavvy
- MarkdownEditing
- Unicode Completion

---

## Proyectos

Abrir

File → Open Folder

Guardar

Project → Save Project As...

Se crea un archivo

```
Proyecto.sublime-project
```

---

## LaTeX

Instalar

```
LaTeXTools
```

Compilar

```
Ctrl+B
```

Visor

```
SumatraPDF
```

---

## Python

Instalar

```
LSP
```

```
LSP-pyright
```

Servidor

```powershell
pip install basedpyright
```

Características

- Autocompletado
- Go to Definition
- Diagnósticos
- Renombrado

---

## Julia

Instalar

```
Julia
```

Instalar

```
LSP-julia
```

(Configuración pendiente)

Unicode Completion permite escribir

```
\alpha<Tab>
```

↓

```
α
```

y cientos de símbolos Unicode.

---

## Build System para Julia

Crear

Tools → Build System → New Build System

```json
{
    "shell_cmd": "julia \"$file\"",
    "working_dir": "$file_path",
    "selector": "source.julia"
}
```

Guardar como

```
Julia.sublime-build
```

Ejecutar

```
Ctrl+B
```

---

## Build System para Quarto

```json
{
    "shell_cmd": "quarto render \"$file\"",
    "working_dir": "$file_path"
}
```

Guardar como

```
Quarto.sublime-build
```

---

## Build System para LaTeX

Lo proporciona automáticamente

```
LaTeXTools
```

Compilar

```
Ctrl+B
```

---

## Terminal

Se puede utilizar

- Windows Terminal

o

- Terminus (opcional)

---

# 6. Configuración recomendada de Sublime

Ocultar archivos auxiliares

```json
{
    "file_exclude_patterns":
    [
        "*.aux",
        "*.log",
        "*.toc",
        "*.out",
        "*.synctex.gz",
        "*.fls",
        "*.fdb_latexmk",
        "*.bbl",
        "*.bcf",
        "*.blg",
        "*.run.xml"
    ]
}
```

Ocultar carpetas

```json
{
    "folder_exclude_patterns":
    [
        ".git",
        ".venv",
        "__pycache__"
    ]
}
```

---

# 7. Flujo de trabajo recomendado

Python

```
Ctrl+B
```

ejecuta el script.

Julia

```
Ctrl+B
```

ejecuta el script.

LaTeX

```
Ctrl+B
```

compila el documento.

Quarto

```
Ctrl+B
```

renderiza el documento.

---

# 8. Pendientes

- Configurar LSP para Julia.
- Integrar Julia con Quarto utilizando el motor nativo.
- Automatizar la selección del Build System según el tipo de archivo.