# Squid Proxy Docker Setup

This repository provides a Docker Compose configuration for deploying a Squid Proxy server using the `ubuntu/squid` Docker image. The proxy server can be used for caching, content filtering, or anonymizing internet traffic.

## Requirements

- Docker
- Docker Compose

## Services

### Proxy Service (Squid)

- **Container Name**: `proxy`
- **Hostname**: `proxy`
- **Image**: `ubuntu/squid:5.2-22.04_beta`
- **Port Mapping**: `3128:3128`
- **Environment Variables**:
  - `TZ=UTC`: Sets the time zone to UTC.
  
- **Volumes**:
  - `/var/log/squid`: Stores Squid's log files.
  - `/var/spool/squid`: Squid cache directory.
  - `/etc/squid`: Configuration directory for Squid.
  - `/usr/local/squid`: Another Squid-related directory for customization.

- **Network**: The service is connected to the default network (`default`).

- **Sysctls**:
  - `net.ipv6.conf.all.disable_ipv6=0`: Enables IPv6 support.

## Volumes

The following Docker volumes are used for persistent storage:

- **proxy-log**: Stores Squid logs.
- **proxy-spool**: Stores Squid cache.
- **proxy-data1**: Stores Squid configuration files.
- **proxy-data2**: Additional Squid-related data storage.

## Notes

- Squid is configured to listen on port `3128`, which is the default proxy port. If you want to change this, modify the `ports` section in the `docker-compose.yml` file.
- Ensure that the Squid proxy is properly configured for your use case, as this setup uses the default configuration from the Docker image. You may want to customize the Squid config files in the `/etc/squid` volume.
- You can check Squid's logs in the `proxy-log` volume for debugging or monitoring proxy activity.

## License

This project is licensed under the [MIT License](LICENSE). See the license file for details.

## Issues, Feature Requests or Support

Please use the Issue > New Issue button to submit issues, feature requests or support issues directly to me. You can also send an e-mail to akin.bicer@outlook.com.tr.
