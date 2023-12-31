# Kong Plugin - Frontier Auth

Kong plugin to use with [frontier](https://github.com/raystack/frontier/) auth server.
- Can exchange browser cookies/bearer header with user token
- Inject user token in all proxy request as bearer token
- Can verify if an endpoint is allowed based on user credentials by hitting frontier check APIs

### TODO
- Add test cases
- https://github.com/lunarmodules/luacheck
- cache frontier response - https://docs.konghq.com/gateway/latest/plugin-development/entities-cache/#cache-custom-entities

### Notes
- Add plugin configuration in kong.yml file where url is a required field
```yml
plugins:
- name: frontier-auth
  service: backend-app
  config: 
    url: http://host.docker.internal:7400/admin/v1beta1/users/self
```
- Configurable items
```
http_connect_timeout = {
    type = "number",
    default = 2000
},
http_send_timeout = {
    type = "number",
    default = 2000
},
http_read_timeout = {
    type = "number",
    default = 2000
},
header_name = {
    type = "string",
    default = "x-user-token"
},
http_method = {
    type = "string",
    default = "GET"
}
```
- For local development linting
```
brew install wget
brew install luarocks
luarocks install luacheck
```

### References
- https://github.com/Kong/kong-plugin
- https://docs.konghq.com/gateway/3.2.x/plugin-development/pdk/