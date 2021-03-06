# Dead simple vsftpd server for single user

Docker image is autogenerated from https://github.com/onjin/docker-alpine-vsftpd

This image contains vsftpd server configured with only one user `files` with
volume `/home/files`. Password is set from `PASSWORD` env variable or generated
if not provided.


## Environment variables

 * PASSWORD - password for default user `files`; autogenerated if not provided


## Simple usage

Example usage:

    $ docker run -it --rm  -v ${PWD}/files:/home/files onjin/alpine-vsftpd
    Generated password for user 'files': fF3X25cg
    Password for 'files' changed

    $ docker run -it --rm  -v ${PWD}/files:/home/files -e PASSWORD=files onjin/alpine-vsftpd
    Password for 'files' changed

    $ docker run -it --rm  -v ${PWD}/files:/home/files -e PASSWORD=files \
        -p 20:20 -p 21:21 \
        onjin/alpine-vsftpd
    Password for 'files' changed


## Passive mode

Passive ports are:
 * min port - 10090
 * max port - 10100

 Example usage:

    $ docker run -it --rm  -v ${PWD}/files:/home/files -e PASSWORD=files \
        -p 20:20 -p 21:21 -p 21100-21110:21100-21110 \
        onjin/alpine-vsftpd
