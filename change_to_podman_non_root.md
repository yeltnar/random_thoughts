## If using systemd
Add user to systemd. For example:
```
User=podman                              
Group=podman
```
Ensure that any directories needed are accessible to the new user. For example, the `%t` systemd syntax refers to `/run`, but you may need to change this to something like `%T` so it uses `/tmp` instead

## Change file owner

Change all host file system mounts to be owned by the user inside the container. Podman has a mapping between the container user, and the host user. In my case, the container user was 1001, and the host user was 100025. So all directories needed to be owned by the container user as known by the host (100025). 

This was recursively done with `chown -R 100025:100025 $PATH_TO_DIR`