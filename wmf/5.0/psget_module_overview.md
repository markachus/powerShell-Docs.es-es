---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222180"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Detección, instalación e inventario del módulo de PowerShell con PowerShellGet

PowerShellGet se incluye en esta versión de WMF:
-   Find-Module puede filtrar por los metadatos del módulo con el parámetro -Tag.
-   Find-Module puede filtrar por el idioma de búsqueda específico del repositorio con el parámetro -Filter.
-   Find-Module puede filtrar por el contenido del módulo con los parámetros -Command, -DscResource e -Includes.
-   Find-DscResource permite la detección de recursos de DSC individuales en repositorios.
-   Soporte para la instalación y la publicación en recursos compartidos de archivos con NuGet.

## <a name="example-commands"></a>Comandos de ejemplo
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Nuevas características de PowerShell
-   Compatibilidad de versiones en paralelo en Windows PowerShell 5.0 o más reciente
-   Compatibilidad con la instalación de dependencias de módulo
-   Tres cmdlets nuevos
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
