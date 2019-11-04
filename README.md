# A _git-secret in docker_ demo

This is a simple demo of how to dockerize the [`git-secret`](https://git-secret.io) command.

## Building the image

To build docker image run:

```
$ docker build -t git-secret .
```

## Using `git-secret`

Assuming you already have:

* a cloned git repository with secrets installed and configured (`/path/to/your/git/repo/with/secrets` below),
* a `gpg` RSA key-pair, by default stored in `~/.gnupg` (`/home/user/.gnupg` below),

and you want to reveal stored secrets, run:

```
$ docker run \
    --rm \
    -it \
    -v /path/to/your/git/repo/with/secrets:/app \
    -v /home/user/.gnupg:/root/.gnupg \
    -w /app \
    git-secret \
    reveal
```
