
## Shell
- deploy - [( code )](https://github.com/nemecdev/devops-scripts/blob/main/src/deploy)

## Usage/Examples
### deploy
*Deploys all in current location to ~/bin/( current location name )*
```sh
deploy . ~/bin
```
___
\
*Deploys all in current location to /tmp/script-deploy-target.XXXXX*
```sh
deploy --dry-run . ~/bin
```
___
\
*Deploys all in current location to root.*

It fails if insufficient permissions
```sh
deploy /
```
___
\
*More complex one*
```sh
yes | deploy -D -C
             --web-server nginx\
             --conf-file my-awesome-conf.[nginx]\
             --target-dir /var/www/\
             --target-name unlimited-api-project
```
**Explanation**
- **yes**
    - while script is running it passes yes to it
- **SOURCE-DIR**
    - if **-s** or **--source-dir** is not used, script takes **"."** as default source
- **-D**
    - dry run ( --dry-run )
- **--web-server**
    - choose web server technology running on your server, same as **-w**
- **--conf-file**
    - choose which conf files will be used for web server **relativelly** to ***SRC-DIR**
      or with **absolute path**. By default if this option is ommited, based on choosed
      **--web-server** script recognizes files with **.conf** for ( httpd | apache2 ) and
      **.nginx** for nginx.\
      **NOTICE**: There can be more than 1 conf file in SRC-DIR but only first find is used,
      sorted alphabetically.
- **--target-dir**
    - target dir for deployment, it is not meant to upload files just into that location
      it will use **SOURCE-DIR** name by default or **--target-name | -n**
- **--target-name**
    - name for the DIR where files will be put into