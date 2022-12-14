Launcher for zkBob API and Cloud Wallet
====

This repo contains files for rapid launch of [zkBob Api and Cloud Wallet](https://docs.zkbob.com/resources/hackathon#zkbob-api-and-cloud-wallet).

## Running the zkBOB API and Cloud Wallet

## Configuration

1) Create an empty directory somewhere on the VM (e.g. `/opt/cloud`)
2) Clone the repository with all necessary configs:
```bash
cd /opt/cloud
git clone https://github.com/zkBob/cloud-launch.git .
```
3) Create `.env` file from the example at `.env.sepolia` or `.env.polygon`. Put the the zkBOB relayer URL and the admin key in the config. Other values can be left without changes.
4) Put ZKP parameters to the `params` directory.

If it is required to send the service logs to a remote syslog server the following actions can be done:

5) Copy `./syslog/etc/logrotate.d/docker-logs` to `/etc/logrotate.d/`.
6) Copy `./syslog/etc/rsyslog.d/30-zkbob-local.conf` and `./syslog/etc/rsyslog.d/35-zkbob-remote-logging.conf` to `/etc/rsyslog.d/`.
7) Modify `target` and `port` in `/etc/rsyslog.d/35-zkbob-remote-logging.conf` to point to a remote syslog server.
8) Restart the rsyslog service by `systemctl restart syslog`.

## Running node

Run the following command to start the zkBOB Cloud:

```bash
docker compose up -d
```

To monitor boot up process, the logs can be accessible by

```
docker compose logs -f zkbob-cloud
```
