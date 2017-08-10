---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Crear un selector de fecha gráfico"
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 5cb952264092d345945318968cf0b3028b11f3e9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2017
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="ab147-103">Crear un selector de fecha gráfico</span><span class="sxs-lookup"><span data-stu-id="ab147-103">Creating a Graphical Date Picker</span></span>
<span data-ttu-id="ab147-104">Use Windows PowerShell 3.0 (y versiones posteriores) para crear un formulario con un control gráfico de estilo de calendario que permita a los usuarios seleccionar un día del mes.</span><span class="sxs-lookup"><span data-stu-id="ab147-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="ab147-105">Crear un control gráfico de selector de fecha</span><span class="sxs-lookup"><span data-stu-id="ab147-105">Create a graphical date-picker control</span></span>
<span data-ttu-id="ab147-106">Copie y pegue lo siguiente en Windows PowerShell ISE y, después, guárdelo como un script de Windows PowerShell (.ps1).</span><span class="sxs-lookup"><span data-stu-id="ab147-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="ab147-107">El script comienza con la carga de dos clases de .NET Framework: **System.Drawing** y **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="ab147-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="ab147-108">A continuación, inicie una nueva instancia de la clase de .NET Framework **Windows.Forms.Form**, que proporciona un formulario o una ventana en blanco en la que puede empezar a agregar controles.</span><span class="sxs-lookup"><span data-stu-id="ab147-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="ab147-109">Tras crear una instancia de la clase Form, asigne valores a las tres propiedades de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ab147-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

-   <span data-ttu-id="ab147-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="ab147-110">**Text.**</span></span> <span data-ttu-id="ab147-111">Es el título de la ventana.</span><span class="sxs-lookup"><span data-stu-id="ab147-111">This becomes the title of the window.</span></span>

-   <span data-ttu-id="ab147-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="ab147-112">**Size.**</span></span> <span data-ttu-id="ab147-113">Es el tamaño del formulario en píxeles.</span><span class="sxs-lookup"><span data-stu-id="ab147-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="ab147-114">El script anterior crea un formulario de 243 píxeles de ancho y 230 píxeles de alto.</span><span class="sxs-lookup"><span data-stu-id="ab147-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

-   <span data-ttu-id="ab147-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="ab147-115">**StartingPosition.**</span></span> <span data-ttu-id="ab147-116">Esta propiedad opcional está establecida en **CenterScreen** en el script anterior.</span><span class="sxs-lookup"><span data-stu-id="ab147-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="ab147-117">Si no agrega esta propiedad, Windows selecciona una ubicación cuando el formulario se abre.</span><span class="sxs-lookup"><span data-stu-id="ab147-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="ab147-118">Cuando **StartingPosition** se establece en **CenterScreen**, el formulario aparece automáticamente en el centro de la pantalla cada vez que se carga.</span><span class="sxs-lookup"><span data-stu-id="ab147-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="ab147-119">A continuación, cree un control de calendario y agréguelo al formulario.</span><span class="sxs-lookup"><span data-stu-id="ab147-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="ab147-120">En este ejemplo, el día actual no está resaltado o dentro de un círculo.</span><span class="sxs-lookup"><span data-stu-id="ab147-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="ab147-121">Los usuarios pueden seleccionar un solo día en el calendario cada vez.</span><span class="sxs-lookup"><span data-stu-id="ab147-121">Users can select only one day on the calendar at one time.</span></span>

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="ab147-122">A continuación, cree un botón **Aceptar** para el formulario.</span><span class="sxs-lookup"><span data-stu-id="ab147-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="ab147-123">Indique un tamaño y el comportamiento del botón **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ab147-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="ab147-124">En este ejemplo, la posición del botón es de 165 píxeles desde el borde superior del formulario y de 38 píxeles desde el borde izquierdo.</span><span class="sxs-lookup"><span data-stu-id="ab147-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="ab147-125">La altura del botón es 23 píxeles y la longitud, 75 píxeles.</span><span class="sxs-lookup"><span data-stu-id="ab147-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="ab147-126">El script usa tipos predefinidos de Windows Forms para definir el comportamiento del botón.</span><span class="sxs-lookup"><span data-stu-id="ab147-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="ab147-127">De manera similar, cree un botón **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="ab147-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="ab147-128">El botón **Cancelar** está a 165 píxeles de la parte superior, pero a 113 píxeles del borde izquierdo de la ventana.</span><span class="sxs-lookup"><span data-stu-id="ab147-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="ab147-129">Establezca la propiedad **Topmost** en **$True** para forzar que la ventana se abra encima del resto de ventanas y cuadros de diálogo abiertos.</span><span class="sxs-lookup"><span data-stu-id="ab147-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="ab147-130">Agregue la siguiente línea de código para mostrar el formulario en Windows.</span><span class="sxs-lookup"><span data-stu-id="ab147-130">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="ab147-131">Por último, el código del bloque **If** indica a Windows qué hacer con el formulario después de que los usuarios seleccionen un día en el calendario y hagan clic en **Aceptar** o presionen la tecla **Entrar**.</span><span class="sxs-lookup"><span data-stu-id="ab147-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="ab147-132">Windows PowerShell muestra la fecha seleccionada a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="ab147-132">Windows PowerShell displays the selected date to users.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="ab147-133">Véase también</span><span class="sxs-lookup"><span data-stu-id="ab147-133">See Also</span></span>
- [<span data-ttu-id="ab147-134">Hey Scripting Guy: Why don’t these PowerShell GUI examples work?</span><span class="sxs-lookup"><span data-stu-id="ab147-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644) (Hey Scripting Guy: ¿Por qué estos ejemplos de GUI de PowerShell no funcionan?)
- [<span data-ttu-id="ab147-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="ab147-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates) (GitHub: WinFormsExampleUpdates de Dave Wyatt)
- [<span data-ttu-id="ab147-136">Windows PowerShell Tip of the Week: Creating a Graphical Date Picker (Sugerencia de la semana de Windows PowerShell: Crear un selector de fecha gráfico)</span><span class="sxs-lookup"><span data-stu-id="ab147-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)
