##comando para quitar carpetas mapeadas en git y no le hagas git add .
git rm -r --cached TestRolf
## Comando parqa quitar archivos 
git rm --cached #TestRolf.ts

## quita todos los git de add .
 git checkout -- node_modules dist  --> descartar cambios
 git reset HEAD --> Eliminar cambios del indice
 git reset HEAD -- dist --> Eliminar cambios del indice de una carpeta especifico 
 git restore . --> elimina todo los archivos

## Alternativa: `git pull --rebase`
Si prefieres mantener un historial de commits más limpio, puedes usar `git pull --rebase` en lugar de un simple `git pull`. Esto re-aplicará tus cambios sobre los cambios traídos del remoto:

git pull --rebase origin nombre-de-tu-rama

### Nota
##Si estás seguro de que quieres sobrescribir los cambios remotos con tus cambios locales (lo cual puede llevar a perder cambios en el remoto), puedes forzar el push con:

git push --force origin nombre-de-tu-rama

### Para regresar a un commit específico en Git, puedes usar el siguiente comando:

git reset --hard <hash_del_commit>

####Para eliminar una rama local en Git, puedes usar el siguiente comando:

git branch -d nombre_de_la_rama

##
#Este comando elimina la rama especificada si ya ha sido fusionada con la rama principal (generalmente main o master). Si la rama no ha
# sido fusionada y contiene cambios que aún no han sido compartidos, Git te advertirá de que hay cambios sin fusionar.
#Si quieres eliminar la rama incluso si contiene cambios sin fusionar, puedes usar el flag -D:

git branch -D nombre_de_la_rama

####Abortar el merge 

git merge --abort

#### forzar el merge (para que no halla conflictos de fusion) pero estaras forzando que se sobrescriba todo de la rama Rolando
 
git merge -X theirs Rolando

###Limpiar archivos sin seguiento 

git clean -f

####eliminar node modules del seguimiento

git rm -r --cached node_modules

git rm -r --cached dist


## subir proyecto con contraseña (si se tiene dos cuentas )

git remote set-url origin https://Rol331:<tu-token>@github.com/Rol331/tu-repositorio.git
git push origin main
