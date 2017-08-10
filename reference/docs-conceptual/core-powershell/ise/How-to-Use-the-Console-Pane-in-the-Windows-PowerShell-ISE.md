---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Cómo usar el panel de consola en Windows PowerShell ISE"
ms.assetid: 44d67705-87c7-4a69-a53e-6471fdebb757
ms.openlocfilehash: 1bb7a18c64fc12130b5af78ef55e68047d54da65
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="how-to-use-the-console-pane-in-the-windows-powershell-ise"></a><span data-ttu-id="ab3d2-103">Cómo usar el panel de consola en Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ab3d2-103">How to Use the Console Pane in the Windows PowerShell ISE</span></span>
<span data-ttu-id="ab3d2-104">El panel de consola del Entorno de scripting integrado (ISE) de Windows PowerShell® funciona exactamente igual que la ventana de consola independiente de Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-104">The Console pane in the Windows PowerShell® Integrated Scripting Environment (ISE) operates exactly like the stand-alone Windows PowerShell ISE console window.</span></span>

<span data-ttu-id="ab3d2-105">Para ejecutar un comando en el panel de consola, escriba un comando y, a continuación, presione ENTRAR.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-105">To run a command in the Console Pane, type a command, and then press ENTER.</span></span> <span data-ttu-id="ab3d2-106">Para escribir varios comandos que quiera ejecutar en secuencia, escriba MAYÚS+ENTRAR entre comandos.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-106">To enter multiple commands that you want to execute in sequence, type SHIFT+ENTER between commands.</span></span> <span data-ttu-id="ab3d2-107">Consulte [Cómo usar la finalización con tabulación en el panel de scripts y en el panel de consola](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) para obtener ayuda sobre la escritura de los comandos.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-107">See [How to Use Tab Completion in the Script Pane and Console Pane](How-to-Use-Tab-Completion-in-the-Script-Pane-and-Console-Pane.md) for help in typing commands.</span></span>

<span data-ttu-id="ab3d2-108">Para detener un comando, en la barra de herramientas, haga clic en **Detener la operación**, o presione CTRL+Interrumpir.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-108">To stop a command, on the toolbar, click **Stop Operation**, or press CTRL+BREAK.</span></span> <span data-ttu-id="ab3d2-109">También puede usar CTRL+C para detener un comando si el contexto no es ambiguo.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-109">You can also use CTRL+C to stop a command if the context is unambiguous.</span></span> <span data-ttu-id="ab3d2-110">Por ejemplo, si se ha seleccionado texto en el panel actual, CTRL+C se asigna a la operación de copia.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-110">For example, if some text has been selected in the current Pane, then CTRL+C maps to the copy operation.</span></span>

<span data-ttu-id="ab3d2-111">A partir de Windows PowerShell v3, el panel de salida se combinó con el panel de consola.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-111">Beginning in Windows PowerShell v3, the Output pane was combined with the Console pane.</span></span> <span data-ttu-id="ab3d2-112">La ventaja de esta combinación es que se comporta como la consola independiente de Windows PowerShell y se eliminan las diferencias en los procedimientos que eran necesarios cuando eran independientes.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-112">This has the benefit of behaving like the stand-alone Windows PowerShell console and eliminates the differences in procedures that were needed when they were separate.</span></span> <span data-ttu-id="ab3d2-113">Se puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ab3d2-113">You can:</span></span>

-   <span data-ttu-id="ab3d2-114">Seleccionar y copiar texto del panel de consola en el Portapapeles para pegarlo en cualquier otra ventana.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-114">Select and copy text from the Console pane to the Clipboard for pasting in any other window.</span></span> <span data-ttu-id="ab3d2-115">Para seleccionar texto, mantenga presionado el botón del ratón en el panel de salida mientras arrastra el mouse sobre el texto que quiere capturar.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-115">To select text, click and hold the mouse in the output pane while dragging the mouse over the text you want to capture.</span></span> <span data-ttu-id="ab3d2-116">También puede usar las teclas de dirección mientras mantiene presionada la tecla **MAYÚS** para seleccionar texto.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-116">You can also use the cursor arrow keys while holding **SHIFT** to select text.</span></span> <span data-ttu-id="ab3d2-117">A continuación, presione CTRL+C o haga clic en el icono **Copiar** en la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-117">Then press CTRL+C or click the **Copy** icon in the toolbar.</span></span>

-   <span data-ttu-id="ab3d2-118">Pegar el texto seleccionado en la posición actual del cursor.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-118">Paste the selected text at a current cursor position.</span></span> <span data-ttu-id="ab3d2-119">Haga clic en el icono **Pegar** de la barra de herramientas.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-119">Click the **Paste** icon on the toolbar.</span></span>

-   <span data-ttu-id="ab3d2-120">Borrar todo el texto del panel de consola.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-120">Clear all the text in the Console pane.</span></span> <span data-ttu-id="ab3d2-121">Para borrar el panel de consola, puede hacer clic en el icono **Borrar panel de consola** de la barra de herramientas, o ejecutar el comando **Clear-Host** o su alias, **cls**.</span><span class="sxs-lookup"><span data-stu-id="ab3d2-121">To clear the Console pane, you can click the **Clear Console Pane** icon on the toolbar, or run the command **Clear-Host** or its alias, **cls**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ab3d2-122">Véase también</span><span class="sxs-lookup"><span data-stu-id="ab3d2-122">See Also</span></span>
- [<span data-ttu-id="ab3d2-123">Usar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ab3d2-123">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
