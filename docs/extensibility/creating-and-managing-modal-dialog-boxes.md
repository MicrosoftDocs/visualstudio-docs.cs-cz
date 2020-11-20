---
title: Vytváření a Správa modálních dialogových oken | Microsoft Docs
description: Naučte se, jak vytvořit modální dialogové okno v rámci sady Visual Studio, jak pomocí DialogWindow, tak bez použití DialogWindow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c95f03ee71a827380539404a90cd79d50232e488
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973627"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Vytváření a Správa modálních dialogových oken
Při vytváření modálního dialogového okna v aplikaci Visual Studio je nutné zajistit, aby nadřazené okno dialogového okna bylo při zobrazení dialogového okna zakázáno, a po zavření dialogového okna znovu povolit nadřazené okno. Pokud to neuděláte, může se zobrazit chyba: *Microsoft Visual Studio nelze vypnout, protože je aktivní modální dialogové okno. Zavřete aktivní dialogové okno a zkuste to znovu.*

Existují dva způsoby, jak to provést. Doporučený způsob, pokud máte dialogové okno WPF, je odvozovat z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> a pak zavolat <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> k zobrazení dialogového okna. Pokud to uděláte, nemusíte spravovat modální stav nadřazeného okna.

Pokud dialogové okno není WPF nebo z jiného důvodu nemůžete odvodit třídu dialogového okna z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , pak musíte získat nadřízený prvek dialogového okna voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> a správou modálního stavu sami, voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metody s parametrem 0 (NEPRAVDA) před zobrazením dialogového okna a voláním metody s parametrem 1 (true) po zavření dialogového okna.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Vytvoření dialogového okna odvozeného z DialogWindow

1. Vytvořte projekt VSIX s názvem **OpenDialogTest** a přidejte příkaz nabídky s názvem **OpenDialog**. Další informace o tom, jak to provést, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Chcete-li použít <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> třídu, je nutné přidat odkazy na následující sestavení (na kartě rozhraní dialogového okna **Přidat odkaz** ):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System. XAML*

3. Do *OpenDialog.cs* přidejte následující `using` příkaz:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Deklarovat třídu s názvem `TestDialogWindow` , která je odvozena z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Aby bylo možné minimalizovat a maximalizovat dialogové okno, nastavte <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> a <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> na hodnotu true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. V `OpenDialog.ShowMessageBox` metodě nahraďte existující kód následujícím kódem:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Sestavte a spusťte aplikaci. Měla by se zobrazit experimentální instance sady Visual Studio. V nabídce **nástroje** experimentální instance byste měli vidět příkaz s názvem **Invoke OpenDialog**. Po kliknutí na tento příkaz by se mělo zobrazit dialogové okno. Měli byste být schopni minimalizovat a maximalizovat okno.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Vytvoření a Správa dialogového okna, které není odvozeno z DialogWindow

1. Pro tento postup můžete použít řešení **OpenDialogTest** , které jste vytvořili v předchozím postupu, se stejnými odkazy na sestavení.

2. Přidejte následující `using` deklarace:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Vytvořte třídu s názvem `TestDialogWindow2` , která je odvozena z <xref:System.Windows.Window> :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Přidat privátní odkaz na <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```
    private IVsUIShell shell;
    ```

5. Přidejte konstruktor, na který nastaví odkaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. V `OpenDialog.ShowMessageBox` metodě nahraďte existující kód následujícím kódem:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Sestavte a spusťte aplikaci. V nabídce **nástroje** byste měli vidět příkaz s názvem **Invoke OpenDialog**. Po kliknutí na tento příkaz by se mělo zobrazit dialogové okno.
