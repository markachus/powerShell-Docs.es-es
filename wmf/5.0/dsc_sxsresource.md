---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218440"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Compatibilidad del control de versiones de módulos en paralelo para recursos de DSC

Los módulos que contienen recursos de DSC pueden instalarse en paralelo y las configuraciones de DSC pueden usar una versión específica del recurso que está instalado en el sistema.

Para más información, consulte [Uso de recursos con varias versiones](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Problemas conocidos

En esta versión, se conocen los siguientes problemas de instalación en paralelo:

-   No se admite el uso de dos versiones diferentes del recurso de DSC en la misma configuración.
