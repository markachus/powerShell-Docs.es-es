# <a name="installing-powershell-core-on-linux"></a>Instalación de PowerShell Core en Linux

Admite [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] y [Arch Linux][arch].

Para distribuciones de Linux que no sean compatibles oficialmente, puede usar el archivo [AppImage de PowerShell][lai].
También puede intentar implementar los archivos binarios de PowerShell directamente mediante el [archivo `tar.gz`][tar] de Linux, pero deberá configurar las dependencias necesarias según el sistema operativo en pasos independientes.

Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.
Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a>Instalación de versiones preliminares

Al instalar una versión preliminar de PowerShell Core para Linux mediante un repositorio de paquetes, el nombre del paquete cambia de `powershell` a `powershell-preview`.

La instalación mediante la descarga directa solo cambia el nombre de archivo.

A continuación se muestra una tabla con los comandos para instalar los paquetes estables y de versión preliminar mediante los diversos administradores de paquetes:

|Distribuciones|Comando estable | Comando de versión preliminar |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Instalación mediante un repositorio de paquetes, Ubuntu 14.04

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Como superusuario, registre el repositorio de Microsoft.
Desde ese momento, solo debe usar `sudo apt-get upgrade powershell` para actualizar la instalación.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Instalación mediante descarga directa, Ubuntu 14.04

Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet.
> El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Desinstalación, Ubuntu 14.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Instalación mediante un repositorio de paquetes, Ubuntu 16.04

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Instalación mediante descarga directa, Ubuntu 16.04

Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet.
> El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Desinstalación, Ubuntu 16.04

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a>Ubuntu 17.10

> [!NOTE]
> Se ha agregado compatibilidad con Ubuntu 17.04 después de `6.1.0-preview.2`.

### <a name="installation-via-package-repository---ubuntu-1710"></a>Instalación mediante un repositorio de paquetes, Ubuntu 17.10

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.

### <a name="installation-via-direct-download---ubuntu-1710"></a>Instalación mediante descarga directa, Ubuntu 17.10

Descargue el paquete de Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet.
> El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Desinstalación, Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Se ha agregado compatibilidad con Ubuntu 18.04 después de `6.1.0-preview.2`.

### <a name="installation-via-package-repository---ubuntu-1804"></a>Instalación mediante un repositorio de paquetes, Ubuntu 18.04

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Instalación mediante descarga directa, Ubuntu 18.04

Descargue el paquete de Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` desde la página de [versiones][] en la máquina Ubuntu.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet.
> El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---ubuntu-1710"></a>Desinstalación, Ubuntu 17.10

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Instalación mediante un repositorio de paquetes, Debian 8

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.

### <a name="installation-via-direct-download---debian-8"></a>Instalación mediante descarga directa, Debian 8

Descargue el paquete de Debian `powershell_6.0.2-1.debian.8_amd64.deb` desde la página de [versiones][] en la máquina Debian.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> El comando `dpkg -i` produce un error con las dependencias unmet.
> El comando siguiente, `apt-get install -f`, resuelve estos problemas y, luego, termina de configurar el paquete de PowerShell.

### <a name="uninstallation---debian-8"></a>Desinstalación, Debian 8

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Instalación mediante un repositorio de paquetes, Debian 9

PowerShell Core para Linux se publica en repositorios de paquetes para facilitar la instalación (y las actualizaciones).
Este es el método preferido.

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo apt-get upgrade powershell` para actualizarlo.

### <a name="installation-via-direct-download---debian-9"></a>Instalación mediante descarga directa, Debian 9

Descargue el paquete de Debian `powershell_6.0.2-1.debian.9_amd64.deb` desde la página de [versiones][] en la máquina Debian.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Desinstalación, Debian 9

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Este paquete también funciona en Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>Instalación mediante un repositorio de paquetes (opción preferida), CentOS 7

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>Instalación mediante descarga directa, CentOS 7

Cuando use [CentOS 7][], descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina CentOS.

Después, ejecute lo siguiente en el terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

También puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>Desinstalación, CentOS 7

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Instalación a través de un repositorio de paquetes (opción preferida), Red Hat Enterprise Linux (RHEL) 7

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Una vez que haya registrado el repositorio de Microsoft como superusuario, solo deberá debe usar `sudo yum update powershell` para actualizar PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Instalación mediante descarga directa, Red Hat Enterprise Linux (RHEL) 7

Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Red Hat Enterprise Linux.

Después, ejecute lo siguiente en el terminal:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

También puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Desinstalación, Red Hat Enterprise Linux (RHEL) 7

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a>OpenSUSE 42.2

Al instalar PowerShell Core, `zypper` puede notificar el siguiente error:

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

En este caso, verifique que haya una biblioteca `libcurl` compatible. Para ello, compruebe que mediante el siguiente comando se muestre que el paquete `libcurl4` está instalado:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

A continuación, elija la solución `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` al instalar el paquete de PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-422"></a>Instalación mediante un repositorio de paquetes (opción preferida), OpenSUSE 42.2

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a>Instalación mediante descarga directa, OpenSUSE 42.2

Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

También puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a>Desinstalación, OpenSUSE 42.2

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 solo se admite en PowerShell Core 6.1 y versiones más recientes.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Instalación mediante un repositorio de paquetes (opción preferida), Fedora 27, Fedora 28

PowerShell Core para Linux se publica en repositorios oficiales de Microsoft para facilitar la instalación (y las actualizaciones).

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Instalación mediante descarga directa, Fedora 27, Fedora 28

Descargue el paquete RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` desde la página de [versiones][] en la máquina Fedora.

Después, ejecute lo siguiente en el terminal:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

También puede instalar el paquete RPM sin el paso intermedio de descargarlo:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Desinstalación, Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> La compatibilidad con Arch es experimental.

PowerShell está disponible en el repositorio de usuario [Arch Linux][] (AUR).

* Se puede compilar con la [versión etiquetada más reciente][arch-release].
* Se puede compilar desde la [última confirmación en maestro][arch-git].
* Se puede instalar mediante el [binario de la versión más reciente][arch-bin].

Los paquetes del AUR se mantienen gracias a la comunidad, ya que no hay asistencia oficial.

Para más información sobre cómo instalar paquetes desde el AUR, vea la [wiki de Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile) de la comunidad.

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a>AppImage de Linux

> [!NOTE]
> La compatibilidad con AppImage es experimental.

Si usa una distribución de Linux reciente, descargue el archivo AppImage `powershell-6.0.1-x86_64.AppImage` desde la página de [versiones][] en el equipo Linux.

Después, ejecute lo siguiente en el terminal:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

El archivo [AppImage][] permite ejecutar PowerShell sin instalarlo.
Se trata de una aplicación portátil que empaqueta PowerShell y sus dependencias (incluidas las dependencias del sistema de .NET Core) en un paquete coherente.
Este paquete es un archivo binario único que funciona con independencia de la distribución de Linux del usuario.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> La compatibilidad con Kali es experimental.

### <a name="installation"></a>Instalación

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Ejecución de PowerShell en la versión más reciente de Kali (Kali GNU/Linux Rolling) sin instalarlo

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Desinstalación, Kali

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> La compatibilidad con Raspbian es experimental.

Actualmente, PowerShell solo se admite en Raspbian Stretch.

Asimismo, CoreCLR (y, por tanto, PowerShell Core) solo funcionará en dispositivos Pi 2 y Pi 3 dado que otros dispositivos, como [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), tienen un procesador no admitido.

Descargue [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) y siga las [instrucciones de instalación](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) para tenerlo en su Pi.

### <a name="installation"></a>Instalación

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

Opcionalmente, puede crear un vínculo simbólico para poder iniciar PowerShell sin especificar la ruta de acceso al archivo binario "pwsh".

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Desinstalación, Raspbian

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archivos binarios

Se proporcionan archivos binarios `tar.gz` de PowerShell para plataformas Linux, a fin de permitir escenarios de implementación avanzados.

### <a name="dependencies"></a>Dependencias

PowerShell compila archivos binarios portátiles para todas las distribuciones de Linux.
Aun así, el entorno de ejecución de .NET Core requiere dependencias diferentes en otras distribuciones, y por eso PowerShell hace lo mismo.

En la tabla siguiente se muestran las dependencias de .NET Core 2.0 que se admiten oficialmente en diferentes distribuciones de Linux.

| Sistema operativo                 | Dependencias |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE 42.2 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Para implementar archivos binarios de PowerShell en distribuciones de Linux que no se admiten oficialmente, debe instalar las dependencias necesarias para el sistema operativo de destino en varios pasos.
Por ejemplo, nuestro [dockerfile de Amazon Linux][amazon-dockerfile] instala primero las dependencias y, después, extrae el archivo `tar.gz` de Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Instalación, archivos binarios

#### <a name="linux"></a>Linux

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a>Desinstalación de archivos binarios

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Rutas de acceso

* `$PSHOME` es `/opt/microsoft/powershell/6.0.2/`.
* Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.
* Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.
* Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.
* Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.
* Los módulos predeterminados se leerán de `$PSHOME/Modules`.
* El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.

Los perfiles respetan la configuración de cada host de PowerShell, por lo que hay perfiles predeterminados específicos del host en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.

PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en Linux.

[Versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
