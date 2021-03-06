---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Recurso de DSC Log
ms.openlocfilehash: fade94efd8133ae0172737e4bb1aed89fc0f97d9
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093483"
---
# <a name="dsc-log-resource"></a>Recurso de DSC Log

> Se aplica a: Windows PowerShell 4.0, Windows PowerShell 5.0

El recurso __Log__ de la configuración de estado deseado (DSC) de Windows PowerShell ofrece un mecanismo para escribir mensajes en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.

```
Syntax

Log [string] #ResourceName
{
    Message = [string]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> De forma predeterminada, solo están habilitados los registros operativos para DSC. Para que el registro analítico esté disponible o visible, es necesario habilitarlo. Para más información, consulte [¿Dónde se encuentran los registros de eventos de DSC?](https://msdn.microsoft.com/en-us/powershell/dsc/troubleshooting#where-are-dsc-event-logs)

## <a name="properties"></a>Propiedades

|  Propiedad  |  Descripción   |
|---|---|
| Mensaje| Indica el mensaje que quiere escribir en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.|
| DependsOn | Indica que la configuración de otro recurso debe ejecutarse antes de que se escriba este mensaje de registro. Por ejemplo, si el elemento ID del bloque del script de configuración del recurso que quiere ejecutar primero es __ResourceName__ y su tipo es __ResourceType__, la sintaxis para usar esta propiedad es `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo incluir un mensaje en el registro de eventos de análisis o de la configuración de estado deseado de Microsoft Windows.

> [!NOTE]
> Si ejecuta [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) con este recurso configurado, siempre devolverá **$false**.

```powershell
Configuration logResourceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node localhost
    {
        Log LogExample
        {
            Message = 'This message will appear in the Microsoft-Windows-Desired State Configuration/Analytic event log.'
        }
    }
}
```