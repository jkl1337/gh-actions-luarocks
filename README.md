# Github Action for LuaRocks

### `jkl1337/gh-actions-luarocks`

[![Actions Status](https://github.com/jkl1337/gh-actions-luarocks/workflows/test/badge.svg)](https://github.com/jkl1337/gh-actions-luarocks/actions)

Builds and installs LuaRocks from source into the `.luarocks/` directory in the working directory. Configures `PATH`, `LUA_PATH`, and `LUA_CPATH` environment variables to be able to use the `luarocks` command directly in workflows, and require installed modules in Lua.

[`jkl1337/gh-actions-lua`](https://github.com/marketplace/actions/install-lua-luajit) can be used to install Lua, which is required for LuaRocks to build and run. (This action will use any Lua installed in `.lua/`).

## Usage

Installs Lua, LuaRocks, then install a module:

```yaml
- uses: jkl1337/gh-actions-lua@v11
- uses: jkl1337/gh-actions-luarocks@v5

# Install some package
- name: install a module
  run: luarocks install moonscript
```

For a more complete example see: https://github.com/jkl1337/gh-actions-lua/blob/master/README.md#full-example

## Inputs

### `luarocksVersion`

**Default**: `"3.8.0"`

Specifies which version of LuaRocks to install. Must be listed on https://luarocks.github.io/luarocks/releases/

Example:

```yaml
- uses: jkl1337/gh-actions-luarocks@v5
  with:
    luarocksVersion: "3.1.3"
```

### `withLuaPath`

**Default**: `null` (Optional)

Manually specify the path to an existing Lua installation to use. This is not
necessary if you are using `jkl1337/gh-actions-lua`. Will build LuaRocks with
`./configure --with-lua=$withLuaPath`

Example:

```yaml
- uses: jkl1337/gh-actions-luarocks@v5
  with:
    withLuaPath: "/usr/local/openresty/luajit/"
```
