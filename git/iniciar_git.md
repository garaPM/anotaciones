# Inicio con versión git

GIT Iniciar versionar con commit

[Read the guide](https://guides.github.com/activities/hello-world/)

## 1. Inicio Rapido

Get started by [creating a new file](https://github.com/garaPM/web-yt-traversy/new/master) or [uploading an existing file](https://github.com/garaPM/web-yt-traversy/upload). We recommend every repository include a [README](https://github.com/garaPM/web-yt-traversy/new/master?readme=1), [LICENSE](https://github.com/garaPM/web-yt-traversy/new/master?filename=LICENSE.md), and [.gitignore](https://github.com/garaPM/web-yt-traversy/new/master?filename=.gitignore).

### 1.1. crear un nuevo repositorio en un linea de comando

```sh
echo "# web-yt-traversy" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:garaPM/web-yt-traversy.git
git push -u origin master
                
```

### 1.2. Enviar datos a un repositorio ya creado desde la línea de comando

```sh
git remote add origin git@github.com:garaPM/web-yt-traversy.git
git push -u origin master
```