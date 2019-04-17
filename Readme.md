vault kv put secret/hello foo=world

vault kv get secret/foo

vault kv get -field=one   secret/foo 

vault kv delete secret/hello

vault token renew 96ddf4bc-d217-f3ba-f9bd-017055595017


vault token  create   -policy=read-only -period=768h


