## Secets Injection into static config files

Sample YAML config file:

```
# static config.yml -- inject env values using pipeline variable substitution
Foods:  Burgers
Generics:
  - key1:
    subkey1: "${DB_USER}"
    subkey2: value1
Drinks: "EspressoMartini,Mojito"
```

Set the variable value in the environment:
```
$ export DB_USER=postgres1
```

Pipe the input file to 'envsubst' for it to replace the variable value $DB_USER with the exported value:

```
$ cat config.yml | envsubst
# static config.yml -- inject env values using pipeline variable substitution
Foods:  Burgers
Generics:
  - key1:
    subkey1: "postgres1"
    subkey2: value1
Drinks: "EspressoMartini,Mojito"
