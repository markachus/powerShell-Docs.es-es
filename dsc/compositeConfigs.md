---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: Anidamiento de configuraciones
ms.openlocfilehash: 4de53b94056df46d74923dda56e02841cfac2cd1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2017
---
# <a name="nesting-dsc-configurations"></a><span data-ttu-id="30cba-103">Anidamiento de configuraciones DSC</span><span class="sxs-lookup"><span data-stu-id="30cba-103">Nesting DSC configurations</span></span>

<span data-ttu-id="30cba-104">Una configuración anidada (también denominada configuración compuesta) es una configuración que se llama dentro de otra configuración, como si se tratara de un recurso.</span><span class="sxs-lookup"><span data-stu-id="30cba-104">A nested configuration (also called composite configuration) is a configuration that is called within another configuration as if it were a resource.</span></span>
<span data-ttu-id="30cba-105">Ambas configuraciones deben definirse en el mismo archivo.</span><span class="sxs-lookup"><span data-stu-id="30cba-105">Both configurations must be defined in the same file.</span></span>

<span data-ttu-id="30cba-106">Veamos un ejemplo sencillo:</span><span class="sxs-lookup"><span data-stu-id="30cba-106">Let's look at a simple example:</span></span>

```powershell
Configuration FileConfig 
{
    param (
        [Parameter(Mandatory = $true)]
        [String] $CopyFrom,

        [Parameter(Mandatory = $true)]
        [String] $CopyTo
    )

    Import-DscResource -ModuleName PSDesiredStateConfiguration

    File FileTest
       {
           SourcePath = $CopyFrom
           DestinationPath = $CopyTo
           Ensure = 'Present'
       }
    
}

Configuration NestedFileConfig
{
    Node localhost
    {
        FileConfig NestedConfig
        {
            CopyFrom = 'C:\Test\TestFile.txt'
            CopyTo = 'C:\Test2'
        }
    }
}
```

<span data-ttu-id="30cba-107">En este ejemplo, `FileConfig` toma dos parámetros obligatorios, **CopyFrom** y **CopyTo**, que se utilizan como los valores para las propiedades **SourcePath** y **DestinationPath** en el bloque de recursos `File`.</span><span class="sxs-lookup"><span data-stu-id="30cba-107">In this example, `FileConfig` takes two mandatory parameters,  **CopyFrom** and **CopyTo**, which are used as the values for the **SourcePath** and **DestinationPath** properties in the `File` resource block.</span></span> <span data-ttu-id="30cba-108">La configuración `NestedConfig` llamada a `FileConfig` como si fuera un recurso.</span><span class="sxs-lookup"><span data-stu-id="30cba-108">The `NestedConfig` configuration calls `FileConfig` as if it were a resource.</span></span>
<span data-ttu-id="30cba-109">Las propiedades del bloque de recursos `NestedConfig` (**CopyFrom** y **CopyTo**) son los parámetros de la configuración `FileConfig`.</span><span class="sxs-lookup"><span data-stu-id="30cba-109">The properties in the `NestedConfig` resource block (**CopyFrom** and **CopyTo**) are the parameters of the `FileConfig` configuration.</span></span>

## <a name="see-also"></a><span data-ttu-id="30cba-110">Véase también</span><span class="sxs-lookup"><span data-stu-id="30cba-110">See Also</span></span>

- [<span data-ttu-id="30cba-111">Recursos compuestos: uso de una configuración DSC como un recurso</span><span class="sxs-lookup"><span data-stu-id="30cba-111">Composite resources--Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
