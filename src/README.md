## Setup ##
```sh
brew install go ;
go get -u github.com/cloudflare/cfssl/cmd/... ;
```

## Usage ##
```sh
cfssl gencert \
  -initca "./src/cauth.json" \
  | cfssljson \
  -bare \
  "./build/cauth" - \
  ;
openssl x509 \
  -text \
  -noout \
  -in "./build/cauth.pem" \
  ;
cfssl gencert \
  -ca "./build/cauth.pem" \
  -ca-key "./build/cauth-key.pem" \
  -config "./src/default.json" \
  -profile "( profile )" \
  "./src/( csr ).json" \
  | cfssljson \
  -bare \
  "./build/( csr )" \
  ;
openssl x509 \
  -text \
  -noout \
  -in "./build/( csr ).pem" \
  ;
```
