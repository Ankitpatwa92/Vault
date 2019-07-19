vault kv put secret/hello foo=world

vault kv get secret/foo

vault kv get -field=one   secret/foo 

vault kv delete secret/hello

vault token renew 96ddf4bc-d217-f3ba-f9bd-017055595017


vault token  create   -policy=read-only -period=768h


#How to configure Vault server

1 Donwload appropiate vault version
https://www.vaultproject.io/downloads.html

2.export VAULT_ADDR = http://127.0.0.1:8200

3.create config.hcl file

```
ui = true

backend "file" {
  path = "/hasicorp"
}

disable_mlock=true    //This should be false for production

listener "tcp" {
  address     = "127.0.0.1:8200",
  tls_disable = 1
}
```

4.Initilize vault
```vault operator init -key-shares=1 -key-threshold=1```
~


5. Vault Create Kubernates Auth Role
```
curl -X POST \
  http://VAULT_URL/v1/auth/cbx-k8s/login \
  -H 'Content-Type: application/json' \
  -d '{	
	"jwt":"fasdfsd",
	"role":"service"	
}'
```

6. Vault health check
```
curl \
    http://127.0.0.1:8200/v1/sys/health
```    
