Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Fringilla phasellus faucibus scelerisque eleifend donec pretium vulputate. Volutpat maecenas volutpat blandit aliquam etiam erat. Lorem mollis aliquam ut porttitor. Proin libero nunc consequat interdum varius sit amet mattis vulputate. Faucibus a pellentesque sit amet porttitor eget dolor. Scelerisque varius morbi enim nunc.

Erat imperdiet sed euismod nisi porta. Imperdiet nulla malesuada pellentesque elit eget gravida cum. Velit dignissim sodales ut eu sem integer vitae justo. 

1. Primero se clono el repositorio de Butcket.
git clone git@bitbucket.org:orbisunt/orbis-example-training.git

2. Se verifica en que repositorio remoto nos encontramos
git remote -v
(Aqui debe figurar BitBucket)

3. Se crea un repositorio en GitHub con el mismo nombre y se 
redirecciona el repositorio remoto.
git remote set-url origin https://github.com/dylanlopez/orbis-example-training.git

4. Se verifica en que repositorio remoto nos encontramos
git remote -v
(Aqui debe figurar GitHub)

5. Se intenta pushear forzadamente.
git push --force
(Muestra un error que se está intentando pushear un archivo muy 
grande)

6. Verificar los SHA pesados
git verify-pack -v .git/objects/pack/pack-e121f70e46f7ec3df6d405dfb4895762265c6af7.idx

7. Verificar a que archivos pertenece dicho SHA
git rev-list --objects --all | grep cfc3322ec593c88d0e4d68c312de3583ca741041

8. Se elimina dicho archivo
git log --oneline --branches -- sc.16.tar.gz
git filter-branch --index-filter \ 'git rm --cached --ignore-unmatch sc.16.tar.gz' -- f3a6dc7^..
rm -Rf .git/refs/original
rm -Rf .git/logs/

9.Ejecutar el comando de limpieza del repositorio.
git gc

10. Creo el commit.
git commit -m "fix deleting large sc.16.tar.gz file"

11. Se realiza el push forzado
git push --force
