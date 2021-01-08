# NGEN Kubernetes
> A collection of kubernetes yamls and such for NGEN.

This repository is a small collection of kubernetes yamls used to set up the NGEN kubernetes cluster.

**NOTE**

Never commit secrets / passwords / anything else senstive to this repository. It is public.
Secrets are to be managed directly in the cluster in order to prevent leaking sensitive data.

### Traefik
> Traefik is used as our ingress provider and SSL certbot.

Traefik is installed via it's [public helm chart](https://github.com/traefik/traefik-helm-chart) (`traefik/traefik`).
The `traefik-values.yaml` is used to customize the traefik install.

command to update / install (must have helm cli installed on your computer):
```bash
helm upgrade --install -n ingress -f traefik-values.yaml traefik traefik/traefik
```

What does this command do?
* upgrades or installs the helm chart located at `traefik/traefik` (helm chart repository)
* the release is named `traefik`
* override values from the file (`-f`) `traefik-values.yaml`
* install to the namespace (`-n`) `ingress` (must be previously created)
