# <a name="installing-powershell-core-on-macos"></a>Instalación de PowerShell Core en macOS

PowerShell Core admite macOS 10.12 y superior.
Todos los paquetes están disponibles en nuestra página de [versiones][] de GitHub.
Una vez que se haya instalado el paquete, ejecute `pwsh` desde un terminal.

### <a name="installation-via-homebrew-on-macos-1012"></a>Instalación mediante Homebrew en macOS 10.12

[Homebrew][brew] es el administrador de paquetes preferido de macOS.
Si no se encuentra el comando `brew`, debe instalar Homebrew según [sus instrucciones][brew].

Una vez que haya instalado Homebrew, le resultará muy fácil instalar PowerShell.
En primer lugar, instale [Homebrew-Cask][cask] para poder instalar más paquetes:

```sh
brew tap caskroom/cask
```

Ahora puede instalar PowerShell:

```sh
brew cask install powershell
```

Por último, compruebe que la instalación funciona correctamente:

```sh
pwsh
```

Cuando se publiquen nuevas versiones de PowerShell, bastará con actualizar las fórmulas de Homebrew y PowerShell:

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> Los comandos anteriores pueden llamarse desde un host de PowerShell (pwsh), pero, acto seguido, el shell de PowerShell se debe cerrar y volver a iniciar para finalizar la actualización y actualizar los valores que aparecen en $PSVersionTable.

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download"></a>Instalación mediante descarga directa

Descargue el paquete PKG `powershell-6.0.2-osx.10.12-x64.pkg` de la página de [versiones][] en la máquina macOS.

Puede hacer doble clic en el archivo y seguir las indicaciones, o bien instalarlo desde el terminal:

```sh
sudo installer -pkg powershell-6.0.2-osx.10.12-x64.pkg -target /
```

## <a name="binary-archives"></a>Archivos binarios

Se proporcionan archivos binarios `tar.gz` de PowerShell para que las plataformas macOS y Linux permitan escenarios de implementación avanzada.

### <a name="installing-binary-archives-on-macos"></a>Instalación de archivos binarios en macOS

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.2/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a>Desinstalación de PowerShell Core

Si ha instalado PowerShell con Homebrew, la desinstalación es fácil:

```sh
brew cask uninstall powershell
```

Si ha instalado PowerShell mediante descarga directa, deberá quitar PowerShell manualmente:

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

Para quitar las rutas de acceso de PowerShell adicionales, consulte la sección [Rutas de acceso][] de este documento y elimine las rutas de acceso deseadas mediante `sudo rm`.

> [!NOTE]
> Este paso no es necesario si ha realizado la instalación con Homebrew.

[Rutas de acceso]:#paths

## <a name="paths"></a>Rutas de acceso

* `$PSHOME` es `/usr/local/microsoft/powershell/6.0.2/`.
* Los perfiles de usuario se leerán de `~/.config/powershell/profile.ps1`.
* Los perfiles predeterminados se leerán de `$PSHOME/profile.ps1`.
* Los módulos de usuario se leerán de `~/.local/share/powershell/Modules`.
* Los módulos compartidos se leerán de `/usr/local/share/powershell/Modules`.
* Los módulos predeterminados se leerán de `$PSHOME/Modules`.
* El historial de PSReadline se grabará en `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`.

Los perfiles respetan la configuración por host de PowerShell.
Así que los perfiles predeterminados específicos del host están en `Microsoft.PowerShell_profile.ps1` en las mismas ubicaciones.

PowerShell respeta la [especificación de directorio base de XDG][xdg-bds] en macOS.

Dado que macOS es una derivación de BSD, se usa el prefijo `/usr/local` en lugar de `/opt`.
Por lo tanto, `$PSHOME` es `/usr/local/microsoft/powershell/6.0.2/`, y el vínculo simbólico se coloca en `/usr/local/bin/pwsh`.

[versiones]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
