# Acceso

Los usuarios con acceso a los laboratorios son aquellos que se encuentran:
- Cursando materias de la _Escuela de Ingenieria_
- Realizando la tesis de grado

Tanto para el acceso presencial como para el remoto, las credenciales son el usuario y la contraseña del mail "@udesa.edu.ar".


```{warning}
La primera vez que uno se loguea a una maquina puede tardar mas de lo esperado.
```

Para poder acceder a la red de la universidad, es necesario que descarguen un cliente para conectarse a la VPN (Virtual Private Network) de la universidad.

## 1. VPN

### Clientes soportados

- Forticlient 7.4 https://www.fortinet.com/lat/support/product-downloads
- Openfortivpn +1.23

Con ambas formas van a tener que utilizar sus credenciales institucionales.

### 1.1. openfortivpn

1. Descargar openfortivpn (versión 1.23 o superior).

   `<PLACEHOLDER: comando de instalación (apt install openfortivpn) y cómo verificar la versión instalada (openfortivpn --version)>`

2. Conectarse corriendo:

   ```
   sudo openfortivpn gateway.udesa.edu.ar:10443 -u <usuario> --saml-login
   ```

   Al correr el comando, se deberia abrir el navegador con una interfaz para loguearse.





### 1.2. FortiClient VPN

1. Descargar FortiClient VPN 7.4 desde https://www.fortinet.com/lat/support/product-downloads e instalarlo.


2. Abrir FortiClient VPN.

```{figure} _static/img/vpn/forticlient_1.png
:alt: Pantalla principal de FortiClient VPN

Pantalla principal de FortiClient VPN.
```

3. Hacer click en el menú (☰) al lado de **VPN Name** y elegir **Add a new connection**.

```{figure} _static/img/vpn/forticlient_2.png
:alt: Menú de FortiClient VPN con la opción Add a new connection

Menú para agregar una nueva conexión.
```

4. Completar los datos de la conexión y hacer click en **Save**:
   - **VPN**: SSL-VPN
   - **Connection Name**: UdeSA VPN
   - **Remote Gateway**: `gateway.udesa.edu.ar:443` y `gateway-2.udesa.edu.ar:443`
   - Marcar **Enable Single Sign On (SSO) for VPN Tunnel**
   - **Client Certificate**: None

```{figure} _static/img/vpn/forticlient_3.png
:alt: Formulario de configuración de la conexión UdeSA VPN

Configuración de la conexión.
```


## 2. Acceso remoto por SSH

### Conexión

Una vez conectados a la VPN, desde una terminal con `ssh` instalado, correr

```
ssh sruberto@labs004.udesa.edu.ar
```

Una vez ejecutado el comando, van a ser conectados directamente a una maquina del laboratorio. 

Por cada conexion sucesiva, se los va a pinnear a la misma maquina para que puedan reutilizar los datos que usen en el disco local.



### Interfaz gráfica (X11 forwarding)
Una de las capacidades de la conexion por SSH es renderizar una interfaz grafica dentro de la maquina y visualizar en la maquina local. Para ello, deben conectarse como:

```
ssh -XYC <usuario>@labs004.udesa.edu.ar
```

### SSH keys

`<PLACEHOLDER: cómo generar un par de claves (ssh-keygen), cómo copiar la clave pública al laboratorio (ssh-copy-id) y cómo usarla para no ingresar la contraseña en cada conexión>`
