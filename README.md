# Challenge NetSec

Examina el entorno, reúne evidencia para explicar el comportamiento y comprueba que tu corrección siga vigente al abrir otra shell interactiva en el mismo nodo.

Necesitas Docker con Docker Compose v2 y acceso a las imágenes del reto en Docker Hub.

## Configurar

Si todavía no tienes `.env`, copia el ejemplo. Si ya existe, actualiza allí `CHALLENGE_TAG=latest`:

```sh
cp .env.example .env
```

## Ejecutar

```sh
docker compose down --remove-orphans
docker compose config --images
docker compose pull
docker compose up -d node-b node-a
```

Abre el panel en [http://127.0.0.1:8080](http://127.0.0.1:8080). 

Entra a la consola de `node-a`:
```sh
docker compose exec -it --user ubuntu node-a bash -i
```

Puedes salir con `exit` y volver a entrar con el mismo comando; el contenedor sigue activo y cada shell recibe un ID de sesión distinto. El proceso que mantiene vivo el contenedor en segundo plano.

Conserva el panel activo mientras investigas. Para documentar la resolución, registra una observación inicial, explica la causa con evidencia y comprueba el resultado desde una shell interactiva nueva dentro del mismo `node-a`.

Para cerrar el entorno:

```sh
docker compose down
```
