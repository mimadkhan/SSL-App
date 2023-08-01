# SSLApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.0.1.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.


## Generate SSL Certificate and Key

1. Create certificate.cnf file.

[req]
default_bits = 2048
prompt = no
default_md = sha256
x509_extensions = v3_req
distinguished_name = dn

[dn]
C = PK
ST = KPK
L = KPK
O = GIK University
OU = GIK University Unit
emailAddress = no-reply@gik.edu.pk
CN = localhost

[v3_req]
subjectAltName = @alt_names

[alt_names]
DNS.1 = localhost

2. run the following command 
 openssl req -new -x509 -newkey rsa:2048 -sha256 -nodes -keyout server.key -days 36525 -out server.crt -config certificate.cnf

 3. run the application 
ng serve --ssl true --ssl-key "D:\Implement SSL\SSL-App\ssl\server.key" --ssl-cert "D:\Implement SSL\SSL-App\ssl\server.crt"

4. Change in package.json file

    "start-ssl": "ng serve --ssl true --ssl-key \"D:\\Implement SSL\\SSL-App\\localhost.key\" --ssl-cert \"D:\\Implement SSL\\SSL-App\\localhost.crt\"",
 
    "start-ssl": "ng serve --ssl true --ssl-key \"D:\\Implement SSL\\SSL-App\\ssl\\server.key\" --ssl-cert \"D:\\Implement SSL\\SSL-App\\ssl\\server.crt\"",


