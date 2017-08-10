---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Ejecutar comandos remotos
ms.assetid: d6938b56-7dc8-44ba-b4d4-cd7b169fd74d
ms.openlocfilehash: a8645a348ebc25533f60cd049ed5872e49565b96
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="running-remote-commands"></a><span data-ttu-id="aa984-103">Ejecutar comandos remotos</span><span class="sxs-lookup"><span data-stu-id="aa984-103">Running Remote Commands</span></span>
<span data-ttu-id="aa984-104">Puede ejecutar comandos en un equipo o en cientos de ellos usando un solo comando de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa984-104">You can run commands on one or hundreds of computers with a single Windows PowerShell command.</span></span> <span data-ttu-id="aa984-105">Windows PowerShell admite la informática remota a través de varias tecnologías, como WS-Management, RPC y WMI.</span><span class="sxs-lookup"><span data-stu-id="aa984-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

## <a name="remoting-without-configuration"></a><span data-ttu-id="aa984-106">Comunicación remota sin configuración</span><span class="sxs-lookup"><span data-stu-id="aa984-106">Remoting Without Configuration</span></span>
<span data-ttu-id="aa984-107">Muchos de los cmdlets de Windows PowerShell tienen un parámetro ComputerName que les permite recopilar datos y cambiar la configuración de uno o más equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="aa984-107">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="aa984-108">Usan distintas tecnologías de comunicación y muchos de ellos funcionan con todos los sistemas operativos de Windows que Windows PowerShell admite sin necesidad de ninguna configuración especial.</span><span class="sxs-lookup"><span data-stu-id="aa984-108">They use a variety of communication technologies and many work on all Windows operating systems that Windows PowerShell supports without any special configuration.</span></span>

<span data-ttu-id="aa984-109">Estos cmdlets son:</span><span class="sxs-lookup"><span data-stu-id="aa984-109">These cmdlets include:</span></span>

-   [<span data-ttu-id="aa984-110">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="aa984-110">Restart-Computer</span></span>](https://technet.microsoft.com/en-us/library/dd315301.aspx)

-   [<span data-ttu-id="aa984-111">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="aa984-111">Test-Connection</span></span>](https://technet.microsoft.com/en-us/library/dd315259.aspx)

-   [<span data-ttu-id="aa984-112">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="aa984-112">Clear-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd347552.aspx)

-   [<span data-ttu-id="aa984-113">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="aa984-113">Get-EventLog</span></span>](https://technet.microsoft.com/en-us/library/dd315250.aspx)

-   [<span data-ttu-id="aa984-114">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="aa984-114">Get-HotFix</span></span>](https://technet.microsoft.com/en-us/library/e1ef636f-5170-4675-b564-199d9ef6f101)

-   [<span data-ttu-id="aa984-115">Get-Process</span><span class="sxs-lookup"><span data-stu-id="aa984-115">Get-Process</span></span>](https://technet.microsoft.com/en-us/library/dd347630.aspx)

-   [<span data-ttu-id="aa984-116">Get-Service</span><span class="sxs-lookup"><span data-stu-id="aa984-116">Get-Service</span></span>](https://technet.microsoft.com/en-us/library/dd347591.aspx)

-   [<span data-ttu-id="aa984-117">Set-Service</span><span class="sxs-lookup"><span data-stu-id="aa984-117">Set-Service</span></span>](https://technet.microsoft.com/en-us/library/dd315324.aspx)

-   [<span data-ttu-id="aa984-118">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="aa984-118">Get-WinEvent</span></span>](https://technet.microsoft.com/en-us/library/dd315358.aspx)

-   [<span data-ttu-id="aa984-119">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="aa984-119">Get-WmiObject</span></span>](https://technet.microsoft.com/en-us/library/dd315295.aspx)

<span data-ttu-id="aa984-120">Normalmente, los cmdlets que admiten la comunicación remota sin una configuración especial tienen un parámetro ComputerName y carecen de un parámetro Session.</span><span class="sxs-lookup"><span data-stu-id="aa984-120">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and do not have the Session parameter.</span></span> <span data-ttu-id="aa984-121">Para encontrar estos cmdlets en la sesión, escriba:</span><span class="sxs-lookup"><span data-stu-id="aa984-121">To find these cmdlets in your session, type:</span></span>

```
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="aa984-122">Comunicación remota de Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="aa984-122">Windows PowerShell Remoting</span></span>
<span data-ttu-id="aa984-123">La comunicación remota de Windows PowerShell, que usa el protocolo WS-Management, permite ejecutar cualquier comando de Windows PowerShell en uno o varios equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="aa984-123">Windows PowerShell remoting, which uses the WS-Management protocol, lets you run any Windows PowerShell command on one or many remote computers.</span></span> <span data-ttu-id="aa984-124">Así, permite establecer conexiones persistentes, iniciar sesiones interactivas de 1:1 y ejecutar scripts en varios equipos.</span><span class="sxs-lookup"><span data-stu-id="aa984-124">It lets you establish persistent connections, start 1:1 interactive sessions, and run scripts on multiple computers.</span></span>

<span data-ttu-id="aa984-125">Para usar la comunicación remota de Windows PowerShell, el equipo remoto debe estar configurado para la administración remota.</span><span class="sxs-lookup"><span data-stu-id="aa984-125">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span> <span data-ttu-id="aa984-126">Para más información y ver instrucciones, consulte [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx) (Acerca de los requisitos remotos).</span><span class="sxs-lookup"><span data-stu-id="aa984-126">For more information, including instructions, see [About Remote Requirements](https://technet.microsoft.com/en-us/library/dd315349.aspx).</span></span>

<span data-ttu-id="aa984-127">Después de configurar la comunicación remota de Windows PowerShell, tendrá a su disposición un gran número de estrategias de comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="aa984-127">After you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span> <span data-ttu-id="aa984-128">En lo que resta de este documento se mencionan solo algunas de ellas.</span><span class="sxs-lookup"><span data-stu-id="aa984-128">The remainder of this document lists just a few of them.</span></span> <span data-ttu-id="aa984-129">Para más información, vea [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) (Acerca del acceso remoto) y [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx) (Preguntas más frecuentes sobre el acceso remoto).</span><span class="sxs-lookup"><span data-stu-id="aa984-129">For more information, see [About Remote](https://technet.microsoft.com/en-us/library/dd347744.aspx) and [About Remote FAQ](https://technet.microsoft.com/en-us/library/dd347744.aspx).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="aa984-130">Iniciar una sesión interactiva</span><span class="sxs-lookup"><span data-stu-id="aa984-130">Start an Interactive Session</span></span>
<span data-ttu-id="aa984-131">Para iniciar una sesión interactiva con un único equipo remoto, use el cmdlet [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-131">To start an interactive session with a single remote computer, use the [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) cmdlet.</span></span> <span data-ttu-id="aa984-132">Por ejemplo, para iniciar una sesión interactiva con el equipo remoto Server01, escriba:</span><span class="sxs-lookup"><span data-stu-id="aa984-132">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```
Enter-PSSession Server01
```

<span data-ttu-id="aa984-133">El símbolo del sistema cambia para mostrar el nombre del equipo al que está conectado.</span><span class="sxs-lookup"><span data-stu-id="aa984-133">The command prompt changes to display the name of the computer to which you are connected.</span></span> <span data-ttu-id="aa984-134">Desde ese momento, cualquier comando que escriba en el símbolo del sistema se ejecutará en el equipo remoto y los resultados se mostrarán en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="aa984-134">From then on, any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="aa984-135">Para finalizar la sesión interactiva, escriba:</span><span class="sxs-lookup"><span data-stu-id="aa984-135">To end the interactive session, type:</span></span>

```
Exit-PSSession
```

<span data-ttu-id="aa984-136">Para más información sobre los cmdlets Enter-PSSession y Exit-PSSession, vea [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) y [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-136">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see [Enter-PSSession](https://technet.microsoft.com/en-us/library/dd315384.aspx) and [Exit-PSSession](https://technet.microsoft.com/en-us/library/dd315322.aspx).</span></span>

### <a name="run-a-remote-command"></a><span data-ttu-id="aa984-137">Ejecutar un comando remoto</span><span class="sxs-lookup"><span data-stu-id="aa984-137">Run a Remote Command</span></span>
<span data-ttu-id="aa984-138">Para ejecutar cualquier comando en uno o varios equipos remotos, use el cmdlet [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-138">To run any command on one or many remote computers, use the [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx) cmdlet.</span></span>
<span data-ttu-id="aa984-139">Por ejemplo, para ejecutar un comando [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) en los equipos remotos Server01 y Server02, escriba:</span><span class="sxs-lookup"><span data-stu-id="aa984-139">For example, to run a [Get-UICulture](https://technet.microsoft.com/en-us/library/dd347742.aspx) command on the Server01 and Server02 remote computers, type:</span></span>

```
Invoke-Command -ComputerName Server01, Server02 {Get-UICulture}
```

<span data-ttu-id="aa984-140">El resultado se muestra en su equipo.</span><span class="sxs-lookup"><span data-stu-id="aa984-140">The output is returned to your computer.</span></span>

```
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

<span data-ttu-id="aa984-141">Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span><span class="sxs-lookup"><span data-stu-id="aa984-141">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462).</span></span>

### <a name="run-a-script"></a><span data-ttu-id="aa984-142">Ejecutar un script</span><span class="sxs-lookup"><span data-stu-id="aa984-142">Run a Script</span></span>
<span data-ttu-id="aa984-143">Para ejecutar un script en uno o varios equipos remotos, use el parámetro FilePath del cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="aa984-143">To run a script on one or many remote computers, use the FilePath parameter of the Invoke-Command cmdlet.</span></span> <span data-ttu-id="aa984-144">El script debe estar en el equipo local o accesible desde este.</span><span class="sxs-lookup"><span data-stu-id="aa984-144">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="aa984-145">Los resultados se devuelven en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="aa984-145">The results are returned to your local computer.</span></span>

<span data-ttu-id="aa984-146">Por ejemplo, el siguiente comando ejecuta el script DiskCollect.ps1 en los equipos remotos Server01 y Server02.</span><span class="sxs-lookup"><span data-stu-id="aa984-146">For example, the following command runs the DiskCollect.ps1 script on the Server01 and Server02 remote computers.</span></span>

```
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

<span data-ttu-id="aa984-147">Para más información sobre el cmdlet Invoke-Command, vea [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-147">For more information about the Invoke-Command cmdlet, see [Invoke-Command](https://technet.microsoft.com/en-us/library/dd347578.aspx).</span></span>

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="aa984-148">Establecer una conexión persistente</span><span class="sxs-lookup"><span data-stu-id="aa984-148">Establish a Persistent Connection</span></span>
<span data-ttu-id="aa984-149">Para ejecutar una serie de comandos relacionados que comparten datos, crear una sesión en el equipo remoto y, a continuación, use el cmdlet Invoke-Command para ejecutar comandos en la sesión que cree.</span><span class="sxs-lookup"><span data-stu-id="aa984-149">To run a series of related commands that share data, create a session on the remote computer and then use the Invoke-Command cmdlet to run commands in the session that you create.</span></span> <span data-ttu-id="aa984-150">Para crear una sesión remota, use el cmdlet New-PSSession.</span><span class="sxs-lookup"><span data-stu-id="aa984-150">To create a remote session, use the New-PSSession cmdlet.</span></span>

<span data-ttu-id="aa984-151">Por ejemplo, el comando siguiente crea una sesión remota en el equipo Server01 y otra sesión remota en el equipo Server02.</span><span class="sxs-lookup"><span data-stu-id="aa984-151">For example, the following command creates a remote session on the Server01 computer and another remote session on the Server02 computer.</span></span> <span data-ttu-id="aa984-152">Guarda los objetos de la sesión en la variable $s.</span><span class="sxs-lookup"><span data-stu-id="aa984-152">It saves the session objects in the $s variable.</span></span>

```
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="aa984-153">Ahora que las sesiones se han establecido, puede ejecutar cualquier comando en ellas.</span><span class="sxs-lookup"><span data-stu-id="aa984-153">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="aa984-154">Y, como las sesiones son persistentes, puede recopilar datos en un solo comando y usarlos en un comando posterior.</span><span class="sxs-lookup"><span data-stu-id="aa984-154">And because the sessions are persistent, you can collect data in one command and use it in a subsequent command.</span></span>

<span data-ttu-id="aa984-155">Por ejemplo, el siguiente comando ejecuta un comando Get-Hotfix en las sesiones de la variable $s y guarda los resultados en la variable $h.</span><span class="sxs-lookup"><span data-stu-id="aa984-155">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="aa984-156">La variable $h se crea en cada una de las sesiones en $s, pero no existe en la sesión local.</span><span class="sxs-lookup"><span data-stu-id="aa984-156">The $h variable is created in each of the sessions in $s, but it does not exist in the local session.</span></span>

```
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="aa984-157">Ahora puede usar los datos de la variable $h en los siguientes comandos, como en el siguiente.</span><span class="sxs-lookup"><span data-stu-id="aa984-157">Now you can use the data in the $h variable in subsequent commands, such as the following one.</span></span> <span data-ttu-id="aa984-158">Los resultados se muestran en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="aa984-158">The results are displayed on the local computer.</span></span>

```
Invoke-Command -Session $s {$h | where {$_.installedby -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="aa984-159">Comunicación remota avanzada</span><span class="sxs-lookup"><span data-stu-id="aa984-159">Advanced Remoting</span></span>
<span data-ttu-id="aa984-160">La administración remota de Windows PowerShell empieza aquí.</span><span class="sxs-lookup"><span data-stu-id="aa984-160">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="aa984-161">Con los cmdlets que se instalan con Windows PowerShell puede, entre otras muchas cosas, establecer y configurar sesiones remotas desde extremos tanto locales como remotos, crear sesiones personalizadas y restringidas, dejar que los usuarios importen comandos desde una sesión remota que se ejecutan implícitamente en la sesión remota o configurar la seguridad de una sesión remota.</span><span class="sxs-lookup"><span data-stu-id="aa984-161">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="aa984-162">Para facilitar la configuración remota, Windows PowerShell incluye un proveedor WSMan.</span><span class="sxs-lookup"><span data-stu-id="aa984-162">To facilitate remote configuration, Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="aa984-163">La unidad WSMAN: que este proveedor crea permite desplazarse por una jerarquía de valores de configuración en el equipo local y en los equipos remotos.</span><span class="sxs-lookup"><span data-stu-id="aa984-163">The WSMAN: drive that the provider creates lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>
<span data-ttu-id="aa984-164">Para obtener más información sobre el proveedor WSMan, vea el tema sobre el [proveedor WSMan](https://technet.microsoft.com/en-us/library/dd819476.aspx) y el tema   [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx) (Acerca de los cmdlets de WS-Management). También puede escribir "Get-Help wsman" en la consola de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="aa984-164">For more information about the WSMan provider, see  [WSMan Provider](https://technet.microsoft.com/en-us/library/dd819476.aspx) and   [About WS-Management Cmdlets](https://technet.microsoft.com/en-us/library/dd819481.aspx), or in the Windows PowerShell console, type "Get-Help wsman".</span></span>

<span data-ttu-id="aa984-165">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="aa984-165">For more information, see:</span></span>
- [<span data-ttu-id="aa984-166">Acerca de las Preguntas más frecuentes sobre el acceso remoto</span><span class="sxs-lookup"><span data-stu-id="aa984-166">About Remote FAQ</span></span>](https://technet.microsoft.com/en-us/library/dd315359.aspx)
- [<span data-ttu-id="aa984-167">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aa984-167">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/dd819496.aspx)
- <span data-ttu-id="aa984-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-168">[Import-PSSession](https://technet.microsoft.com/en-us/library/dd347575.aspx).</span></span> 

<span data-ttu-id="aa984-169">Para obtener ayuda con los errores de comunicación remota, consulte [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa984-169">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/en-us/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa984-170">Véase también</span><span class="sxs-lookup"><span data-stu-id="aa984-170">See Also</span></span>
- [<span data-ttu-id="aa984-171">about_Remote</span><span class="sxs-lookup"><span data-stu-id="aa984-171">about_Remote</span></span>](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="aa984-172">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="aa984-172">about_Remote_FAQ</span></span>](https://technet.microsoft.com/en-us/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="aa984-173">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="aa984-173">about_Remote_Requirements</span></span>](https://technet.microsoft.com/en-us/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="aa984-174">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="aa984-174">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/en-us/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="aa984-175">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="aa984-175">about_PSSessions</span></span>](https://technet.microsoft.com/en-us/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="aa984-176">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aa984-176">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/en-us/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="aa984-177">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="aa984-177">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
- [<span data-ttu-id="aa984-178">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="aa984-178">Import-PSSession</span></span>](https://technet.microsoft.com/en-us/library/048c115e-a6fb-4e0d-8cea-c5ca24630c9d)
- [<span data-ttu-id="aa984-179">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="aa984-179">New-PSSession</span></span>](https://technet.microsoft.com/en-us/library/59452f12-a11d-4558-99ea-e6ca6ad5ffd3)
- [<span data-ttu-id="aa984-180">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="aa984-180">Register-PSSessionConfiguration</span></span>](https://technet.microsoft.com/en-us/library/af68867a-d201-4b19-a1de-594015ed8a25)
- [<span data-ttu-id="aa984-181">Proveedor de WSMan</span><span class="sxs-lookup"><span data-stu-id="aa984-181">WSMan Provider</span></span>](https://technet.microsoft.com/en-us/library/66fe1241-e08f-49ca-832f-a84c33ca8735)
