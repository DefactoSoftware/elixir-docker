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

*There is currently no GitHub Action to automatically build the images, so building and publishing has to be done manually through Docker Desktop or CLI for now.*
<br>
<br>

### To Build (Docker Desktop)

*First, install/setup Docker Desktop and login.*

```
cd VERSION
docker build --platform=linux/amd64 -t defactosoftware/elixir:VERSION .
```
<br>

### To Publish (Docker Desktop)

- Find the built image under **images**
- Click the *three-dot* menu and select **Push to Docker Hub**
