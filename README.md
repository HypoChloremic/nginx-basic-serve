# basic nginx static serve server
## preqs
nixos
`nix-shell -p nginx`

## Running
```bash
$ bash run.sh
```

very simple. Ensure that when `nginx -c <abs path to the conf file>` you provide the entire path to the file nad not just a relative path.
That includes the paths to the static html files as well.
