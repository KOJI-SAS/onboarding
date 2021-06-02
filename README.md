# On Boarding

Welcome at KOJI.

For your first day, you will have to install your Mac. You can following the instructions bellow:

- Download this repository as a zip file
- Extract the file to your desktop
- Open the "Terminal" application
- Drag and drop the extracted folder in the Terminal app
- Press enter to open the directory in the terminal
- Execute the following command: `sh setup.sh`

This installation could take a while. At some points you will be required to enter your password. Don't forget to plug your macbook, you don't want this script to fail because your mac goes out of battery.

## VSCode Configuration

To have a consistent programming environment we provide a default configuration for VSCode, you must use this configuration at first. But you can modify it afterwards if you want to change something.

You will need the [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) extension to synchronize your configuration with the default one.

After installing the extenson you should use the following command: `Sync: Advanced Options > Ouvrir les paramètres` and enter `a90dc89436151831fd1bf8629080ade3` in the Gist id field. When it's done you can use `Sync: Download Settings`.

If everything goes fine, you will see a debug window opening. Wait for the completion message. The installation could take a while, but if you see some error this might be because one of the extension we use has been removed from the store. Ask your manager to check that with you.

> Reminder: To use a command in VSCode the shortcut is `Cmd+Shift+P`

From now you're free to use any theme or extension you want if it's not conflicting with our code convention and guidelines. If you're not sure about what can break the configuration, ask your manager.

## Docker Containers

This are the containers we use all the times. In the future each project will have its own docker compose, but for the moment it's easier to have one container for all.

> If your a project manager you're not required to follow these instructions

### Minio ( Fake S3 Bucket  Server )

```bash
cd ~/Documents/Containers
mkdir minio
cd minio
docker run -p 9000:9000 --name minio -d -e "MINIO_ACCESS_KEY=AZERTYUIOP" -e "MINIO_SECRET_KEY=AZERTYUIOP" --mount type=bind,src="$(pwd)",target=/data minio/minio server /data
```

### MariaDB ( SQL )

```bash
cd ~/Documents/Containers
mkdir mariadb
cd mariadb
docker run -p 3306:3306 --name mariadb -d --env MYSQL_ROOT_PASSWORD=root --env MYSQL_DATABASE=database --mount type=bind,src="$(pwd)",target=/var/lib/mysql mariadb
```

### Postgres ( SQL )

```bash
cd ~/Documents/Containers
mkdir mariadb
cd mariadb
docker run -p 5432:5432 --name postgres -d --env MYSQL_ROOTPOSTGRES_PASSWORD_PASSWORD=root --env MYSQL_DATABASE=database --mount type=bind,src="$(pwd)",target=/var/lib/mysql postgres
```

### MongoDB ( NoSQL )

```bash
cd ~/Documents/Containers
mkdir mongodb
cd mongodb
docker run -p 27017-27019:27017-27019 --name mongodb -d --env MONGO_INITDB_ROOT_USERNAME=root --env MONGO_INITDB_ROOT_PASSWORD=root --mount type=bind,src="$(pwd)",target=/data/db mongo
```
