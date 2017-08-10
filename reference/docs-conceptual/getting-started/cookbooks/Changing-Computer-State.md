---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Cambiar el estado del equipo
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: 636690c72b16bf19826b0a7e54ce00114ce30fb6
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="changing-computer-state"></a><span data-ttu-id="344a8-103">Cambiar el estado del equipo</span><span class="sxs-lookup"><span data-stu-id="344a8-103">Changing Computer State</span></span>
<span data-ttu-id="344a8-104">Para restablecer un equipo en Windows PowerShell, use una herramienta de línea de comandos estándar o una clase WMI.</span><span class="sxs-lookup"><span data-stu-id="344a8-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="344a8-105">Aunque use Windows PowerShell solo para ejecutar la herramienta, aprender a cambiar el estado de energía de un equipo en Windows PowerShell le mostrará algunos de los detalles importantes sobre el uso de herramientas externas en Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="344a8-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="344a8-106">Bloquear un equipo</span><span class="sxs-lookup"><span data-stu-id="344a8-106">Locking a Computer</span></span>
<span data-ttu-id="344a8-107">La única manera de bloquear un equipo directamente con las herramientas estándar disponibles es llamar a la función **LockWorkstation()** en **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="344a8-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="344a8-108">Este comando bloquea inmediatamente la estación de trabajo.</span><span class="sxs-lookup"><span data-stu-id="344a8-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="344a8-109">Usa *rundll32.exe*, que ejecuta archivos DLL de Windows (y guarda sus bibliotecas para usarlas repetidamente), para ejecutar el archivo user32.dll, una biblioteca de funciones de administración de Windows.</span><span class="sxs-lookup"><span data-stu-id="344a8-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="344a8-110">Si se bloquea una estación de trabajo mientras Cambio rápido de usuario está habilitado, como en Windows XP, el equipo muestra la pantalla de inicio de sesión de usuario, en lugar de iniciar el protector de pantalla del usuario actual.</span><span class="sxs-lookup"><span data-stu-id="344a8-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="344a8-111">Para cerrar sesiones determinadas en un servidor de Terminal Server, use la herramienta de línea de comandos **tsshutdn.exe**.</span><span class="sxs-lookup"><span data-stu-id="344a8-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="344a8-112">Cerrar la sesión actual</span><span class="sxs-lookup"><span data-stu-id="344a8-112">Logging Off the Current Session</span></span>
<span data-ttu-id="344a8-113">Puede usar varias técnicas diferentes para cerrar una sesión en el sistema local.</span><span class="sxs-lookup"><span data-stu-id="344a8-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="344a8-114">La manera más sencilla es usar la herramienta de línea de comandos **logoff.exe** de Escritorio remoto/Terminal Services (para obtener más información, en el símbolo del sistema de Windows PowerShell, escriba **logoff /?**).</span><span class="sxs-lookup"><span data-stu-id="344a8-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="344a8-115">Para cerrar la sesión activa actualmente, escriba **logoff** sin argumentos.</span><span class="sxs-lookup"><span data-stu-id="344a8-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="344a8-116">También puede usar la herramienta **shutdown.exe** con su opción de cierre de sesión:</span><span class="sxs-lookup"><span data-stu-id="344a8-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="344a8-117">Una tercera opción es usar WMI.</span><span class="sxs-lookup"><span data-stu-id="344a8-117">A third option is to use WMI.</span></span> <span data-ttu-id="344a8-118">La clase Win32_OperatingSystem tiene un método Win32Shutdown.</span><span class="sxs-lookup"><span data-stu-id="344a8-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="344a8-119">Al invocar el método con la marca 0 se inicia el cierre de sesión:</span><span class="sxs-lookup"><span data-stu-id="344a8-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="344a8-120">Para obtener más información y otras características del método Win32Shutdown, vea "Win32Shutdown Method of the Win32_OperatingSystem Class" (Método Win32Shutdown de la clase Win32_OperatingSystem) en MSDN.</span><span class="sxs-lookup"><span data-stu-id="344a8-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="344a8-121">Apagar o reiniciar un equipo</span><span class="sxs-lookup"><span data-stu-id="344a8-121">Shutting Down or Restarting a Computer</span></span>
<span data-ttu-id="344a8-122">Apagar y reiniciar equipos suelen ser los mismos tipos de tarea.</span><span class="sxs-lookup"><span data-stu-id="344a8-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="344a8-123">Las herramientas que apagan un equipo generalmente también lo reinician, y viceversa.</span><span class="sxs-lookup"><span data-stu-id="344a8-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="344a8-124">Hay dos opciones sencillas para reiniciar un equipo desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="344a8-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="344a8-125">Use Tsshutdn.exe o Shutdown.exe con los argumentos apropiados.</span><span class="sxs-lookup"><span data-stu-id="344a8-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="344a8-126">Puede obtener información de uso detallada en **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="344a8-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="344a8-127">o **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="344a8-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="344a8-128">También puede realizar las operaciones de apagar y reiniciar mediante **Win32_OperatingSystem** directamente desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="344a8-128">You can also perform shutdown and restart operations by using **Win32_OperatingSystem** directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="344a8-129">Para apagar el equipo, use el método Win32Shutdown con la marca **1**.</span><span class="sxs-lookup"><span data-stu-id="344a8-129">To shut down the computer, use the Win32Shutdown method with the **1** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

<span data-ttu-id="344a8-130">Para reiniciar el sistema operativo, use el método Win32Shutdown con la marca **2**.</span><span class="sxs-lookup"><span data-stu-id="344a8-130">To restart the operating system, use the Win32Shutdown method with the **2** flag.</span></span>

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```
