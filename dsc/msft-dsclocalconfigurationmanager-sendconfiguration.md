---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892450"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Método SendConfiguration de la clase MSFT_DSCLocalConfigurationManager

Envía el documento de configuración al nodo administrado y lo guarda como cambio pendiente.

## <a name="syntax"></a>Sintaxis

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parámetros

*ConfigurationData* \[in\] Datos del entorno para la configuración.

*force* \[in\] **true** para forzar la configuración a detenerse.

## <a name="return-value"></a>Valor devuelto

Devuelve cero si se ejecuta correctamente; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones

Se trata de un método estático.

## <a name="requirements"></a>Requisitos

**MOF:** DscCore.mof

**Espacio de nombres**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vea también

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)