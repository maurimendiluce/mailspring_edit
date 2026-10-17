# Mi Configuración

Este documento resume la configuración de un entorno de trabajo para Python, Julia, y Mailspring

---

## 1. Python

### Windows

#### Verificar la instalación

```powershell
python --version
where python
```

o

```powershell
py --version
```

---

### Crear un entorno virtual

Desde la carpeta del proyecto:

```powershell
python -m venv .venv
```

o

```powershell
py -m venv .venv
```

---

### Activar el entorno

PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

CMD

```cmd
.venv\Scripts\activate.bat
```

---

### Desactivar

```powershell
deactivate
```

---

### Eliminar un entorno

Simplemente borrar la carpeta

```
.venv
```

---

### Instalar paquetes

Actualizar pip

```powershell
python -m pip install --upgrade pip
```

Instalar paquetes

```powershell
pip install numpy scipy matplotlib pandas jupyter basedpyright
```

---

## Linux

### Crear un entorno virtual

```bash
python3 -m venv .venv
```

---

### Activar

```bash
source .venv/bin/activate
```

---

### Desactivar

```bash
deactivate
```

---

### Eliminar

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

## 3. LaTeX

Se recomienda instalar

- MiKTeX (Windows)
- TeX Live (Linux)

Configurar MiKTeX para instalar paquetes automáticamente.

---

## 4. Mailspring

Descomprimir los .zip de la carpeta mailspring_edit y copiarlos (o instalarlos) en %appdata%\Mailspring\packages (windows)