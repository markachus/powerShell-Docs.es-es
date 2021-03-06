---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Elementos con las ediciones compatibles de PowerShell
ms.openlocfilehash: f661c2cd076acb9c11394ba0b752ebd154965ff4
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189506"
---
# <a name="items-with-compatible-powershell-editions"></a>Elementos con las ediciones compatibles de PowerShell

A partir de la versión 5.1, PowerShell está disponible en diferentes ediciones que denotan distintos conjuntos de características y compatibilidad con varias plataformas.

- **Desktop Edition:** basado en .NET Framework y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Server Core y Windows Desktop.
- **Core Edition:** basado en .NET Core y proporciona compatibilidad con scripts y módulos destinados a las versiones de PowerShell que se ejecutan en las ediciones de superficie completa de Windows como Nano Server y Windows IoT.

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-items-compatible-for-specific-powershell-editions"></a>La Galería de PowerShell extrae metadatos de PSEditions compatibles y permite filtrar los elementos compatibles con ediciones específicas de PowerShell

Si en un elemento se han especificado PSEditions compatibles, se enumerarán como parte de "Ediciones de PowerShell" en la página de visualización del elemento y en los resultados de los elementos.

![Página de visualización del elemento con PSEditions](../../Images/ItemDisplayPageWithPSEditions.PNG)

## <a name="search-for-items-in-the-gallery-ui-which-works-on-powershellcore"></a>Buscar elementos en la interfaz de usuario de la Galería que funciona en PowerShellCore

Use Tags:"PSEdition_Desktop" y Tags:"PSEdition_Core" para filtrar los elementos de la Galería de PowerShell.

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a>Use Tags:"PSEdition_Core" para buscar elementos compatibles con la edición PowerShell Core.

![Resultados de la búsqueda de elementos compatibles con Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a>Use Tags:"PSEdition_Desktop" para buscar elementos compatibles con la edición PowerShell Desktop.

![Resultados de la búsqueda de elementos compatibles con Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-items-with-compatible-powershell-editions"></a>Obtener más detalles sobre la creación y la búsqueda de elementos con ediciones compatibles de PowerShell

- [Módulos con PSEditions](../../concepts/module-psedition-support.md)
- [Scripts con PSEditions](../../concepts/script-psedition-support.md)