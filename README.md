# On Boarding

Bienvenue chez KOJI, pour commencer cette incroyable aventure tu auras besoin de certains outils.

La majeure partie des projets sur lesquels on travaille fonctionne soit avec PHP soit avec NodeJS.

## Environment Javascript

### Nécessaire

- [Node.JS LTS](https://nodejs.org/en/download/)
- [Yarn ( Modern Package Manager )](https://yarnpkg.com/en/docs/install#mac-stable)
- [NVM ( Node Version Manager )](https://github.com/nvm-sh/nvm#install--update-script)
- [Docker](https://docs.docker.com/docker-for-mac/install/)
- [Vue CLI](https://cli.vuejs.org/guide/installation.html)

### Conseiller

- [iTerm2](https://www.iterm2.com/index.html)
- [Oh My ZSH](https://ohmyz.sh/)
- [agnoster.zsh-theme](https://github.com/agnoster/agnoster-zsh-theme)
- [Visual Studio Code](https://code.visualstudio.com/Download)
- [Vue.js Extension Pack](https://marketplace.visualstudio.com/items?itemName=mubaidr.vuejs-extension-pack)
- [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)
- [Babel JavaScript](https://marketplace.visualstudio.com/items?itemName=mgmcdermott.vscode-language-babel)
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)

## Docker Containers

### Base

```bash
cd ~/Documents
mkdir Containers
```

### Minio ( Fake S3 Bucket  Server )

```bash
cd ~/Documents/Containers
mkdir minio
cd minio
docker run -p 9000:9000 --name minio -d --env MINIO_ACCESS_KEY=root --env MINIO_SECRET_KEY=root --mount type=bind,src="$(pwd)",target=/data minio/minio server /data
```

### MariaDB ( SQL )

```bash
cd ~/Documents/Containers
mkdir mariadb
cd mariadb
docker run -p 3306:3306 --name mariadb-dqzdq -d --env MYSQL_ROOT_PASSWORD=root --env MYSQL_DATABASE=database --mount type=bind,src="$(pwd)",target=/var/lib/mysql mariadb
```

MongoDB ( NoSQL )

```bash
cd ~/Documents/Containers
mkdir mongodb
cd mongodb
docker run -p 27017-27019:27017-27019 --name mongodb-dqzdqzd -d --env MONGO_INITDB_ROOT_USERNAME=root --env MONGO_INITDB_ROOT_PASSWORD=root --mount type=bind,src="$(pwd)",target=/data/db mongo
```
