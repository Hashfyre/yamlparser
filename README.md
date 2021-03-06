# BASH YAML Parser

## Description

The `yamlparser` script uses `sed` and `awk` to parse through a strict `YAML`  
list and produces a set of `key=value` BASH variables which are then  
directly usable inside the script.

This script is essentially called as a dependency from within another BASH script.  
It helps make various hierarchical / conditional / contextual variable-name creation,  
and `key=value`like access a piece of cake by externalizing all script configurations  
as a parsable YAML list and passing it to `yamlpaser` in the lifetime of The original script.  

## Usage

### YAML list

create a `${BASENAME}.conf` file for your script and store configurations as:

```YAML
---
local:
  log:
    dir: somedir
    file: somefile
  others:
    user: x
remote:
  log:
    dir: remotedir
    file: remotefile
  others:
    user: Y
```

### In-script Usage

```shell
eval "(yamlparser ${yaml_file})"
```

### Access values of hierarchical variables

```shell
host_user=${host}_user
host=local
echo ${!host_user} # -> X
host=remote
echo ${!host_user} # -> Y
```

## Contributing

1. Fork the repo
2. Submit a pull request :D

## History

I am not the author of the script. I just chose to host it and use it extensively
in most of my `bash` scripts as a dependency that lets me do `configuration over code`
in `bash`.

This code is copied from the [stackoverflow thread](http://stackoverflow.com/questions/5014632/how-can-i-parse-a-yaml-file-from-a-linux-shell-script)

## Credits

[Stefan Farestam](http://stackoverflow.com/users/1792684/stefan-farestam)

## License

CC-BY-SA
[Stefan Farestam](http://stackoverflow.com/users/1792684/stefan-farestam)

Re-released under MIT-License by Joy Bhattacherjee
