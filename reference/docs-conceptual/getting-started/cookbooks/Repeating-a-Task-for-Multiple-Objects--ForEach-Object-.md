---
ms.date: 06/05/2017
keywords: powershell, cmdlet
title: Repetir una tarea para varios objetos ForEach Object
ms.assetid: 6697a12d-2470-4ed6-b5bb-c35e5d525eb6
ms.openlocfilehash: 8b8002af3ade0905421760ce29cdc84b084236e9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954286"
---
# <a name="repeating-a-task-for-multiple-objects-foreach-object"></a>Repetir una tarea para varios objetos (ForEach-Object)

El cmdlet **ForEach-Object** usa bloques de script y el descriptor $_ del objeto de canalización actual para permitir ejecutar un comando en cada objeto de la canalización. Se puede usar para realizar algunas tareas complejas.

Una situación en la que puede resultar útil es la manipulación de datos para mejorar su utilidad. Por ejemplo, la clase Win32_LogicalDisk de WMI puede usarse para devolver información del espacio libre de cada disco local. Los datos se devuelven en bytes, lo que dificulta su lectura:

```
PS> Get-WmiObject -Class Win32_LogicalDisk

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 50665070592
Size         : 203912880128
VolumeName   : Local Disk
```

Podemos convertir el valor FreeSpace a megabytes dividiendo cada valor por 1024 dos veces; después de la primera división, los datos están en kilobytes y tras la segunda, en megabytes. Para realizar este paso en un bloque de script ForEach-Object, escriba lo siguiente:

```
PS> Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {($_.FreeSpace)/1024.0/1024.0}
48318.01171875
```

Desafortunadamente, la salida actual consta de datos sin una etiqueta asociada. Dado que las propiedades de WMI como esta son de solo lectura, no se puede convertir directamente el valor de FreeSpace. Si escribe esto:

```powershell
Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.FreeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Obtiene un mensaje de error:

```output
"FreeSpace" is a ReadOnly property.
At line:1 char:70
+ Get-WmiObject -Class Win32_LogicalDisk | ForEach-Object -Process {$_.F <<<< r
eeSpace = ($_.FreeSpace)/1024.0/1024.0}
```

Puede reorganizar los datos mediante algunas técnicas avanzadas, pero un enfoque más sencillo es crear un nuevo objeto con **Select-Object**.