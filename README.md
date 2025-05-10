<div align="center">

  <img src="assets/logo.png" alt="logo" width="200" height="auto" />
  <h1>HLL-GEOFENCE</h1>
  
<!-- Badges -->
<p>
  <a href="https://github.com/2KU77B0N3S/hll-geofences/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/2KU77B0N3S/hll-geofences" alt="contributors" />
  </a>
  <a href="">
    <img src="https://img.shields.io/github/last-commit/2KU77B0N3S/hll-geofences" alt="last update" />
  </a>
  <a href="https://github.com/2KU77B0N3S/hll-geofences/network/members">
    <img src="https://img.shields.io/github/forks/2KU77B0N3S/hll-geofences" alt="forks" />
  </a>
  <a href="https://github.com/2KU77B0N3S/hll-geofences/stargazers">
    <img src="https://img.shields.io/github/stars/2KU77B0N3S/hll-geofences" alt="stars" />
  </a>
  <a href="https://github.com/2KU77B0N3S/hll-geofences/issues/">
    <img src="https://img.shields.io/github/issues/2KU77B0N3S/hll-geofences" alt="open issues" />
  </a>
  <a href="https://github.com/2KU77B0N3S/hll-geofences/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/2KU77B0N3S/hll-geofences.svg" alt="license" />
  </a>
</p>
   
<h4>
    <a href="https://github.com/2KU77B0N3S/hll-geofencesr">Documentation</a>
  <span> · </span>
    <a href="https://github.com/2KU77B0N3S/hll-geofences/issues/">Report Bug</a>
  <span> · </span>
    <a href="https://github.com/2KU77B0N3S/hll-geofences/issues/">Request Feature</a>
  </h4>
</div>

<br />

<!-- Table of Contents -->
# Table of Contents

- [About the Project](#about-the-project)
- [Tech Stack](#tech-stack)
- [Basic Seeding Setup (Midcap Only)](#Basic-Seeding-Setup-(Midcap-Only))
- [Set Up Discord Bot (Midcap Only)](#SetUp-Discord-Bot-(Optional))
> [!Notice]
> There is an extended variant
- [Extended Seeding Setup (Last Two Lines Blocked)](#Extended-Seeding-Setup-(Last-Two-Lines-Blocked))
- [Set Up Discord Bot (Extended Version)](#SetUp-Discord-Bot-(Extended-Version))
- [Running Scripts Persistently with PM2](#Running-Scripts-Persistently-with-PM2)
- [Usage](#usage)
- [Roadmap](#roadmap)
- [License](#license)
- [Contact](#contact)
> [!TIP]
> To use both bots you need 2 bot directories and one main directory!

---

## About the Project
This repository (**HLL-GEOFENCE**) provides scripts for managing seeding configurations for Hell Let Loose (HLL) servers using geofencing. It includes two setups: Basic Seeding (Midcap only) and Extended Seeding (last two lines blocked). Both setups can be configured for different player counts and include Docker and Discord integration options. Below are the setup instructions for each.

---

## Tech Stack
- **Programming language:** JavaScript
- **Libraries:** `discord.js`, `dotenv`, `node-fetch`, `requests`
- **Dev-Libraries:** nodemon

---

## Basic Seeding Setup (Midcap Only)

- 1. Clone the Repository
```bash
git clone https://github.com/2KU77B0N3S/hll-geofences
```
- 2. Rename the Folder:
```bash
mv hll-geofences hll-geofences-basic
cd hll-geofences-basic
```
- 3. Select Player Count Configuration: Choose one of the following commands based on the desired player count:
```bash
# 40 Player
mv seeding.midcap.40player.config.yml config.yml
```
or
```bash
# 50 Player
mv seeding.midcap.50player.config.yml config.yml
```
or
```bash
# 60 Player
mv seeding.midcap.60player.config.yml config.yml
```
### 4. Edit Configuration: 
Open config.yml and fill in SERVER-IP, RCON-PORT, and RCON-PW.
- 1. Rename the Docker configuration file
```bash
mv midcap.docker-compose.yml docker-compose.yml
```
- 2. Build the Docker image (required after changing files):
```bash
docker compose build
```
- 3. Start the Docker container:
```bash
docker compose up -d
```
- 4. Stop the Docker container (when needed):
```bash
docker compose down
```

## Set Up Discord Bot (Optional):
- 1. Rename and fill out the environment file: Channel ID must be not the same as Extended Seeding (script clears channel on startup)
```bash
mv midcap.example.env .env
```
- 2. Rename the script:
```bash
mv midcap.main.mjs main.mjs
```
- 3. Install dependencies:
```bash
npm install
```
- 4. Start the script:
```bash
node main.mjs
```

---

> [!Notes]
> if you also want to use the extended version and you are still in the directory hll-geofences-basic go back to the main directory

```bash
cd ..
```
## Extended Seeding Setup (Last Two Lines Blocked)

- 1. Clone the Repository
```bash
git clone https://github.com/2KU77B0N3S/hll-geofences
```
- 2. Rename the Folder:
```bash
mv hll-geofences hll-geofences-extended
cd hll-geofences-extended
```
- 3. Select Player Count Configuration: Choose one of the following commands based on the desired player count:
```bash
# 60 Player
mv seeding.3caps.60player.config.yml config.yml
```
or
```bash
# 70 Player
mv seeding.3caps.70player.config.yml config.yml
```
or
```bash
# 80 Player
mv seeding.3caps.80player.config.yml config.yml
```
### 4. Edit Configuration: 
Open config.yml and fill in SERVER-IP, RCON-PORT, and RCON-PW.
- 1. Rename the Docker configuration file
```bash
mv extended.docker-compose.yml docker-compose.yml
```
- 2. Build the Docker image (required after changing files):
```bash
docker compose build
```
- 3. Start the Docker container:
```bash
docker compose up -d
```
- 4. Stop the Docker container (when needed):
```bash
docker compose down
```
## Set Up Discord Bot (Extended Version):
- 1. Rename and fill out the environment file: Channel ID must be not the same as Extended Seeding (script clears channel on startup)
```bash
mv extended.example.env .env
```
- 2. Rename the script:
```bash
mv extended.main.mjs main.mjs
```
- 3. Install dependencies:
```bash
npm install
```
- 4. Start the script:
```bash
node main.mjs
```

---

## Running Scripts Persistently with PM2
To run either or both scripts in the background with automatic restarts, use PM2.
- 1. Install PM2 Globally:
```bash
npm install -g pm2
```
- 2. Set Up PM2 Autostart:
```bash
pm2 startup
```
- 3. Start Scripts:
    - For Basic Seeding:
    ```bash
    cd hll-geofences-basic
    pm2 start main.mjs --name hll-geofence-basic
    ```
    - For Extended Seeding:
    ```bash
    cd hll-geofences-extended
    pm2 start main.mjs --name hll-geofence-extended
    ```
- 4. Save PM2 Configuration:
```bash
pm2 save
```
- 4. Enable PM2 Autostart:
```bash
pm2 startup
```
### Managing PM2 Processes
- View Running Processes:
  ```bash
  pm2 status
  ```
- Monitor Processes:
  ```bash
  pm2 monit
  ```
- Control Processes (replace `id` with the process ID from `pm2 status`):
  - Stop: `pm2 stop id`
  - Restart: `pm2 restart id`
  - Start: `pm2 start id`
  - Delete: `pm2 delete id`
- Recover Processes (if not showing):
  ```bash
  pm2 resurrect
  ```
  
---

## Usage
The bot runs as a Discord bot and can be controlled via buttons.

---

## Roadmap
* [ ] Language file (en,esp,fr,de)?????

---

## License
Dieses Projekt ist unter der **MIT License** lizenziert.

---

## Contact
Created by **2KU77B0N3S**. For questions or suggestions, please create an issue on GitHub.

📧 **Contact:** [Discord](https://discord.com/users/785886867073400903)

