##Algunos comandos básicos de tmux son:

- tmux: Inicia una nueva sesión de tmux.
- Ctrl+b d: Detiene la sesión actual.
- tmux attach: Une a una sesión existente.
- Ctrl+b c: Crea una nueva ventana.
- Ctrl+b n: Mueve al siguiente ventana.
- Ctrl+b p: Mueve al anterior ventana.
- Ctrl+b &: Mata la venatana

- Ctrl+b % : divida la ventan en dos paneles verticales
- Ctrl+b " : divude la ventana en dos panels horizontales
- Ctrl+b (flechas): ir al siguiente panel segun la dirección 
- Ctrl+b o : siguiente panel
- Ctrl+b x :Cierra el panel 
- Ctrl+b q : imprime el numero de panel 
- Ctrl+b t : tiempo en el panel 
- Ctrl+b f :buscar un panel 
- Ctrl+b [ : modo desplazamiento (no ejecuta comandos)
- q : salid de modo desplazamiento 
- Ctrl+b M+o : rotar paneles


### Creando y gestionando secciones en tmux

Tmux permite dividir la pantalla en varias secciones o paneles. Aquí te explico cómo hacerlo:

1. **Crear una nueva sección (panel)**:
   - Presiona Ctrl+b seguido de % para dividir la pantalla horizontalmente.
   - O presiona Ctrl+b seguido de " para dividir verticalmente.

2. **Navegar entre secciones**:
   - Usa las flechas de navegación (h, j, k, l) para moverte entre paneles.
   - Presiona Ctrl+b seguido de [ para ir al panel anterior y ] para ir al siguiente.

3. **Renombrar secciones**:
   - Presiona Ctrl+b, luego r, y luego el número del panel que quieres renombrar.

4. **Unir secciones**:
   - Presiona Ctrl+b seguido de ' para unir paneles adyacentes horizontalmente.
   - O presiona Ctrl+b seguido de + para unir paneles adyacentes verticalmente.

5. **Deshacer una acción**:
   - Si accidentalmente creaste una sección extra, puedes deshacer la última acción con Ctrl+b seguido de u.

6. **Configurar secciones por defecto**:
   - En tu archivo .tmux.conf, puedes definir el número inicial de paneles y su tamaño al iniciar tmux.

### Consejos adicionales

- Para ver una lista de comandos disponibles en tmux, presiona Ctrl+b seguido de ?.
- Puedes personalizar los atajos de teclado en tu archivo .tmux.conf.
- Si necesitas ayuda con un comando específico, puedes escribirlo después de Ctrl+b : para ejecutarlo directamente.
