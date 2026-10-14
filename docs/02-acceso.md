# Acceso

Los usuarios con acceso a los laboratorios son aquellos que se encuentran:
- Cursando materias de la _Escuela de Ingeniería_
- Realizando la tesis de grado

Tanto para el acceso presencial como para el remoto, las credenciales son el usuario y la contraseña del mail "@udesa.edu.ar".


```{warning}
La primera vez que uno se loguea a una máquina puede tardar más de lo esperado.
```

## VPN

Para poder acceder a la red de la universidad, es necesario que descarguen un cliente para conectarse a la VPN (Virtual Private Network) de la universidad.

### Clientes soportados

- openfortivpn (Linux)
- FortiClient VPN (Linux y Windows)

### openfortivpn

1. Descargar openfortivpn (versión 1.23 o superior).

2. Conectarse corriendo:

   ```
   sudo openfortivpn gateway.udesa.edu.ar:443 -u <usuario> --saml-login
   ```

   Al correr el comando, se debería abrir el navegador con una interfaz para loguearse.


### FortiClient VPN

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

5. Elegir **UdeSA VPN** en **VPN Name** y hacer click en **SAML Login**. Se abre una ventana para loguearse con las credenciales institucionales.

```{figure} _static/img/vpn/forticlient_4.png
:alt: Pantalla principal de FortiClient VPN con el botón SAML Login

Conexión con SAML Login.
```


## Acceso remoto por SSH

Una vez conectados a la VPN, desde una terminal con `ssh` instalado, correr

```
ssh <usuario>@labs004.udesa.edu.ar
```

Una vez ejecutado el comando, van a ser conectados directamente a una máquina del laboratorio. Luego, cada conexión sucesiva los va a asignar a la misma máquina, para que puedan reutilizar los datos que usen en el disco local.

Cada usuario puede tener hasta 2 conexiones simultáneas al laboratorio. `ssh`, `scp`, `sftp` y `rsync` cuentan cada uno como una conexión.

Para copiar archivos y usar aplicaciones gráficas por SSH, ver [Tips de SSH](03-tips-ssh.md).
