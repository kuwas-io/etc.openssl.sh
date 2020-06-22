<!--
# #####
# TERRAFORM LIFECYCLE MANAGED
# All changes will be overwritten
#####
-->

# etc.openssl.sh #

[ ![ Actions ][ actions-ico ] ][ actions-url ]  
[ ![ Coverages ][ coverages-ico ] ][ coverages-url ]  
[ ![ Issues ][ issues-ico ] ][ issues-url ]  
[ ![ Languages ][ languages-ico ] ][ languages-url ]  
[ ![ Version ][ version-ico ] ][ version-url ]  

- - -
> etc » openssl » sh

- - -
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

## Notes ##
* n/a

- - -
## Contributions ##
* n/a

- - -
[ ![ License ][ license-ico ] ][ license-url ]  

[ license-ico ]: https://img.shields.io/github/license/kuwas-io/etc.openssl.sh?style=for-the-badge&logo=github
[ license-url ]: https://choosealicense.com/licenses/isc

[ actions-ico ]: https://img.shields.io/github/workflow/status/kuwas-io/etc.openssl.sh/default?style=for-the-badge&logo=github
[ actions-url ]: https://github.com/kuwas-io/etc.openssl.sh/actions
[ coverages-ico ]: https://img.shields.io/coveralls/github/kuwas-io/etc.openssl.sh?style=for-the-badge&logo=github
[ coverages-url ]: https://coveralls.io/github/kuwas-io/etc.openssl.sh
[ issues-ico ]: https://img.shields.io/github/issues/kuwas-io/etc.openssl.sh?style=for-the-badge&logo=github
[ issues-url ]: https://github.com/kuwas-io/etc.openssl.sh/issues
[ languages-ico ]: https://img.shields.io/github/languages/top/kuwas-io/etc.openssl.sh?style=for-the-badge&logo=github
[ languages-url ]: https://github.com/kuwas-io/etc.openssl.sh/pulls
[ version-ico ]: https://img.shields.io/github/v/release/kuwas-io/etc.openssl.sh?style=for-the-badge&logo=github
[ version-url ]: https://github.com/kuwas-io/etc.openssl.sh/releases
