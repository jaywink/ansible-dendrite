# Dendrite

Deploy a Dendrite (monolithic) Matrix server using Docker.

https://github.com/matrix-org/dendrite

Targeting Ubuntu 20.04, contributions welcome for a larger set of platforms.

## Requirements

Developed and tested on Ansible 2.9.6.

## Usage

You can install this role from Ansible Galaxy with:

```bash
ansible-galaxy install jaywink.ansible_dendrite
```

The Dendrite container exposes an HTTP endpoint on localhost port 8008. You will need to
set up a reverse proxy to handle TLS and proxy any `_matrix` path traffic to the container.

A PostgreSQL database is also required.

Set the required variables for your play.

Generate a signing key as follows. You'll need a Golang binary in your path.

```bash
go get github.com/matrix-org/dendrite/cmd/generate-keys
go run github.com/matrix-org/dendrite/cmd/generate-keys --private-key=matrix_key.pem
```

Copy the contents of the generated `matrix_key.pem` file into the `dendrite_matrix_key_pem` variable.

Now you can run the play and get a fresh Dendrite.

## Role Variables

### Required

* `dendrite_server_name` - Dendrite server name (ie `domain.tld`)
* `dendrite_matrix_key_pem` - The signing key
* `dendrite_db_host` - Database hostname to use (PostgreSQL)
* `dendrite_db_password` - Database password to use

### Optional

* `dendrite_name` - The name of the instance and user on the host to use, will be created (default: `dendrite`)
* `dendrite_container_name` - Name to use for the Docker container (defaults to value of `dendrite_name` variable)
* `dendrite_docker_image` - Docker image to use (defaults to: `matrixdotorg/dendrite-monolith:v0.8.1`)
* `dendrite_db_name` - Database name to use (defaults to value of `dendrite_name` variable)
* `dendrite_db_username` - Database user to use (defaults to value of `dendrite_name` variable)
* `dendrite_db_sslmode` - Database SSL mode, set to `false` if your database is within an internal network (defaults to `true`)
* `dendrite_metrics_enabled` - Whether to enable Prometheus metrics endpoint (default `false`)
* `dendrite_metrics_basic_auth_username` - Username for basic auth of metrics (defaults to empty - no basic auth)
* `dendrite_metrics_basic_auth_password` - Password for basic auth of metrics (defaults to empty - must be set if username is set)
* `dendrite_client_api_registration_enabled` - Whether to allow registrations (defaults to `true`)
* `dendrite_client_api_registration_shared_secret` - Registration shared secret for registering users (defaults to empty)
* `dendrite_container_labels` - Labels to add to the container (defaults to empty dictionary)
* `dendrite_docker_networks` - Additional docker networks to connect to (defaults to empty list)
* `dendrite_enabled_mscs` - A list of MSC's to enable (defaults to empty, list should have lowercase items, for example `msc2836`)
* `dendrite_logging_file` - Set to true to enable logging to file in addition to stdout (default false).
  Logs will go to `/var/log/dendrite`. WARNING! There is no auto-deletion of old logs.
* `dendrite_presence_enable_inbound` - Set to true to enable inbound presence (defaults to false)
* `dendrite_presence_enable_outbound` - Set to true to enable outbound presence (defaults to false)

### Dependencies

None

## License

BSD

## Author Information

Jason Robinson / `@jaywink:federator.dev` / https://jasonrobinson.me
