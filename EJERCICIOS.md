# EJERCICIOS PARTE 2 - Git y GitHub

```bash
# Ejercicio 1: Ciclo básico de Git
echo "## Mis asignaturas" > notas.md     # Crea el archivo notas.md con la cabecera
git add notas.md                           # Añade el archivo al stage para commit
git commit -m "feat: añade notas iniciales" # Hace commit del archivo en local
git push origin main                       # Sube el commit a GitHub

echo "-DWEC" >> notas.md                   # Añade DWEC al archivo
echo "-DWES" >> notas.md                   # Añade DWES al archivo
git commit -am "feat: amplía notas.md"     # Hace commit directo de cambios modificados
git push origin main                       # Sube los cambios a GitHub

# Ejercicio 2: Ramas
git checkout -b feature-tareas             # Crea y cambia a la rama feature-tareas
echo "-Hacer tareas pendientes" >> notas.md # Añade tareas pendientes en notas.md
git add notas.md                            # Añade cambios al stage
git commit -m "feat: añade tareas pendientes" # Commit en la rama feature-tareas
git push -u origin feature-tareas          # Sube la rama al remoto y la vincula

git checkout main                           # Cambia de nuevo a main
git merge feature-tareas                    # Fusiona los cambios de feature-tareas en main
git push origin main                        # Sube los cambios fusionados a GitHub

git branch -d feature-tareas                # Borra la rama local
git push origin --delete feature-tareas     # Borra la rama en remoto

# Ejercicio 3: Borrado y restauración
echo "Archivo temporal" > temporal.txt     # Crea un archivo temporal
git add temporal.txt                        # Añade al stage
git commit -m "chore: añade archivo temporal" # Commit en local
git rm temporal.txt                         # Elimina el archivo del repo
git commit -m "chore: elimina archivo temporal" # Commit de borrado
git push origin main                        # Sube los cambios al remoto

echo "Archivo temporal" > temporal.txt     # Vuelve a crear el archivo
git restore temporal.txt                    # Restaura el archivo desde el último commit

# Ejercicio 4: Logs y diffs
git log --oneline --graph --all            # Muestra historial de commits resumido y gráfico
git diff HEAD~1 HEAD                        # Muestra diferencias entre último commit y el anterior

# Ejercicio 5: Conflictos intencionados
git checkout -b feature-conflicto          # Crea y cambia a la rama feature-conflicto
# Editar notas.md en feature-conflicto
git commit -am "feat: cambios en feature-conflicto" # Commit de cambios en la rama

git checkout main                           # Volver a main
# Editar la misma línea en main
git commit -am "feat: cambios en main"     # Commit en main

git merge feature-conflicto                 # Intenta fusionar, genera conflicto
# Resolver manualmente el conflicto en notas.md
git add notas.md                            # Marca el conflicto como resuelto
git commit -m "fix: resuelto conflicto entre main y feature-conflicto" # Commit final del conflicto
git push origin main                        # Sube cambios resueltos al remoto

# Ejercicio 6: Tags
git tag v1.0                               # Crea un tag ligero v1.0
git push origin --tags                      # Sube todos los tags al remoto

git tag -a v1.1 -m "Primera versión estable" # Crea un tag anotado con mensaje
git push origin --tags                       # Sube el tag anotado al remoto
