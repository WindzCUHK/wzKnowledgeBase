
# package.json
1. `npm init -y`
1. `node -v`
1. add to `package.json`
    ```json
    "engines": {
      "node": "4.2.1"
    }
    ```

# .npmrc
1. `~/.npmrc`
1. `npm config set save=true``
1. `npm config set save-exact=true``

# node options
1. `node --optimize_for_size --max_old_space_size=460 --gc_interval=100 server.js`

# node ENV
1. `NODE_PATH=.`
