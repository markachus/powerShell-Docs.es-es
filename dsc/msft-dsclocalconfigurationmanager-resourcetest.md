---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893083"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método ResourceTest de la clase MSFT_DSCLocalConfigurationManager

Llama directamente al método **Test** de un recurso de DSC.

## <a name="syntax"></a>Sintaxis

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parámetros

*ResourceType* \[in\] Nombre del recurso al que se va a llamar.

*ModuleName* \[in\] Nombre del módulo que contiene el recurso al que se va a llamar.

*resourceProperty* \[in\] Especifica el nombre de la propiedad del recurso y su valor en una tabla hash como clave y valor, respectivamente. Use el cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) para descubrir las propiedades del recurso y sus tipos.

*InDesiredState* \[out\] En la devolución, esta propiedad se establece en **true** si el nodo de destino está en el estado deseado.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)