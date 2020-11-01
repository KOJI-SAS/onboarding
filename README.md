# On Boarding

Bienvenue chez KOJI, pour commencer cette incroyable aventure tu auras besoin de certains outils.

La majeure partie des projets sur lesquels on travaille fonctionne soit avec PHP soit avec NodeJS.

## Environment Koji

### Nécessaire

- [Chrome](https://www.google.com/intl/fr_fr/chrome/)
- [Firefox](https://www.mozilla.org/fr/firefox/new/)
- [ClickUp](https://clickup.com/)
- [Slack](https://slack.com/intl/fr-fr/)
- [Skype](https://www.skype.com/fr/)
- [Office](https://www.office.com/)
- [TeamViewer](https://www.teamviewer.com/fr/)

### Recommandé

- [Spectacle](https://www.spectacleapp.com/)

## Environment Javascript

### Nécessaire

- [Node.JS LTS](https://nodejs.org/en/download/)
- [Yarn ( Modern Package Manager )](https://yarnpkg.com/en/docs/install#mac-stable)
- [NVM ( Node Version Manager )](https://github.com/nvm-sh/nvm#install--update-script)
- [Docker](https://docs.docker.com/docker-for-mac/install/)
- [Vue CLI](https://cli.vuejs.org/guide/installation.html)

### Recommandé

- [iTerm2](https://www.iterm2.com/index.html)
- [SequelPro](https://www.sequelpro.com/)
- [MongoDB Compass Community](https://www.mongodb.com/download-center/compass)
- [Oh My ZSH](https://ohmyz.sh/)
- [agnoster.zsh-theme](https://github.com/agnoster/agnoster-zsh-theme)
- [Visual Studio Code](https://code.visualstudio.com/Download)
- [Vue.js Extension Pack](https://marketplace.visualstudio.com/items?itemName=mubaidr.vuejs-extension-pack)
- [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify)
- [Babel JavaScript](https://marketplace.visualstudio.com/items?itemName=mgmcdermott.vscode-language-babel)
- [DotENV](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)

## VSCode Configuration

You will need [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) visual studio code extension to synchronize your configuration with the default one.

After installing you should use the following command: `Sync: Advanced Options > Download Settings from public Gist` and enter `a90dc89436151831fd1bf8629080ade3` as Gist id.

From now you can install another theme of your choice if you don't like the provided one.

## Docker Containers

### Base

```bash
cd ~/Documents
mkdir Containers
```

### Minio ( Fake S3 Bucket  Server )

> Not used for the moment. Need to update the command, `access_key` passing method has changed

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
docker run -p 3306:3306 --name mariadb -d --env MYSQL_ROOT_PASSWORD=root --env MYSQL_DATABASE=database --mount type=bind,src="$(pwd)",target=/var/lib/mysql mariadb
```

### MongoDB ( NoSQL )

```bash
cd ~/Documents/Containers
mkdir mongodb
cd mongodb
docker run -p 27017-27019:27017-27019 --name mongodb -d --env MONGO_INITDB_ROOT_USERNAME=root --env MONGO_INITDB_ROOT_PASSWORD=root --mount type=bind,src="$(pwd)",target=/data/db mongo
```
