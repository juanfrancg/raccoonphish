![gophish logo](https://raw.github.com/gophish/gophish/master/static/images/gophish_purple.png)

Gophish
=======

En primer lugar, hay que instalar Go siguiendo los pasos descritos en la documentación oficial:

[Instalación Go en Linux](https://go.dev/doc/install)

En segundo lugar, si no está subido el binario compilado o da errores, hay que compilar el código con el siguiente comando desde la carpeta raiz del proyecto:

`go build`

Finalmente, para utilizar la aplicación, añadir en el archivo _config.json_ las rutas a los certificados de la landing page. Estos se generan utilizando el siguiente comando:

`sudo certbot --register-unsafely-without-email certonly --standalone -d <dominio> -d <subdominio1> -d <subdominio2> -d <subdominioX...>`

Modificaciones
=======

Este código tiene ciertas mejoras y modificaciones respecto al proyecto original que se describen a continuación:

- Se cambia el nombre del parámetro de tracking "rid" por "token".
- Se modifica la página de error 404 por defecto añadiéndole un mensaje nuevo y cabeceras nuevas aleatorias.
- Se aplican los mismos cambios de la página de error 404 al robots.txt, en cuanto a las cabeceras.
- Se elimina la cabecera X-Mailer en los envíos de correos.
- Se elimina la cabecera X-GoPhish-Contact.
- Se configura por defecto la aplicación para que la landing page funcione por HTTPS, aunque la aplicación no funcionará si no se añaden los certificados en el archivo _config.json_.
- Se configura la aplicación para guardar logs de todo lo que ocurra durante la ejecución en un archivo en la carpeta raíz del proyecto
- Se añaden cabeceras nuevas en las landing pages para ocultar aún más que se trata de un servidor de GoPhish

Todos los cambios en el código están etiquetados con el comentario _--GoPhishraccoon--_ junto a ellos.

Troubleshooting
=======

- Es posible que la aplicación de un error al compilar, en este caso hay que ejecutar el archivo _ejecutarAntesDeCompilar.sh_ incluido en la carpeta raíz del proyecto

Trabajo futuro
=======

- Es necesario que la aplicación haga backups automáticamente en otro servidor que no sea de OVH, por si se cae toda la infraestrucutra de la empresa.
