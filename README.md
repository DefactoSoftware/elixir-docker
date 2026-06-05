## Defacto's Elixir base images

Docker images based on hex.pm's Elixir images.
<br>
<br>

Included:
- Erlang
- Elixir
- NodeJS
- ImageMagick
- Some build tools (for dependencies that require compilation steps)
<br>

### Adding a new version

1. Create a new directory named after the Elixir version (e.g. `1.20.0-otp-28/`) containing a `Dockerfile`. When publishing multiple Erlang/OTP variants of the same Elixir version, suffix the directory with the OTP major (e.g. `1.20.0-otp-28/`, `1.20.0-otp-29/`).
2. Open a PR — the `Build and publish` workflow builds the image to verify the Dockerfile compiles.
3. On merge to `master`, the workflow pushes the image to Docker Hub as `defactosoftware/elixir:<version>`.

### Required Docker Hub secrets

The publish workflow needs two repository secrets configured in **Settings → Secrets and variables → Actions**:

- `DOCKERHUB_USERNAME` — a Docker Hub account with push access to `defactosoftware/elixir`
- `DOCKERHUB_TOKEN` — a Docker Hub access token (create one at https://hub.docker.com/settings/security)

### Building locally

If you need to build the image on your machine (e.g. to test ahead of pushing):

```
cd VERSION
docker build --platform=linux/amd64 -t defactosoftware/elixir:VERSION .
docker push defactosoftware/elixir:VERSION   # optional
```

Docker Desktop, Colima, OrbStack and Podman all work — anything that provides a `docker` CLI with buildx.
