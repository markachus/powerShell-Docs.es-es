---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: e1f8146b6113a82fd3d857c98550ec2e459715a4
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954932"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola

La finalización con tabulación proporciona ayuda automática al escribir en el panel de scripts o el panel de comandos. Para aprovechar esta característica, siga estos pasos:

## <a name="to-automatically-complete-a-command-entry"></a>Para completar automáticamente una entrada de comando

En el panel de comandos o el panel de scripts, escriba algunos caracteres de un comando y, después, presione la tecla TAB para seleccionar el texto de finalización deseado. Si varios elementos empiezan por el texto que ha escrito inicialmente, siga presionando la tecla Tab hasta que aparezca el elemento deseado. La finalización con tabulación puede ayudarle a escribir un nombre de cmdlet, de parámetro, de variable o de propiedad de objeto, o bien una ruta de acceso de archivo.

> [!NOTE]
> En el panel de scripts, al presionar TAB, se completa automáticamente un comando solo cuando se editan archivos .ps1, .psd1 o .psm1. La finalización con tabulación funciona siempre al escribir en el panel de comandos.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Para completar automáticamente la entrada de un parámetro de cmdlet

En el panel de comandos o el panel de scripts, escriba un cmdlet seguido por un guion y, después, presione la tecla TAB.

Por ejemplo, escriba `Get-Process -` y, a continuación, presione TAB varias veces para mostrar cada uno de los parámetros del cmdlet de uno en uno.

## <a name="see-also"></a>Véase también

- [Presentación de Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Cómo crear una pestaña de PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)