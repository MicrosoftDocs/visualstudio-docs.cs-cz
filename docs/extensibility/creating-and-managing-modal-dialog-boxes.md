---
title: Vytváření a správa modálních dialogových oken | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739493"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Vytvoření a správa modálních dialogových oken
Při vytváření modálního dialogového okna v sadě Visual Studio se musíte ujistit, že nadřazené okno dialogového okna je při zobrazení dialogového okna zakázáno, a poté znovu povolit nadřazené okno po zavření dialogového okna. Pokud tak neučiníte, může se zobrazit chyba: *Aplikace Microsoft Visual Studio nelze vypnout, protože je aktivní modální dialog. Zavřete aktivní dialog a akci opakujte.*

Existují dva způsoby, jak toho dosáhnout. Doporučenýzpůsob, pokud máte dialogové okno WPF, je <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>odvodit <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> z aplikace a potom volat k zobrazení dialogového okna. Pokud tak učiníte, není nutné spravovat modální stav nadřazeného okna.

Pokud dialogové okno není WPF nebo z nějakého jiného důvodu <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>nelze odvodit třídu dialogového <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> okna z aplikace , potom <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> je nutné získat nadřazenou položku dialogového okna voláním a správou modálního stavu sami voláním metody s parametrem 0 (false) před zobrazením dialogového okna a znovu voláním metody s parametrem 1 (true) po zavření dialogového okna.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Vytvoření dialogového okna odvozeného z dialogového okna

1. Vytvořte projekt VSIX s názvem **OpenDialogTest** a přidejte příkaz nabídky s názvem **OpenDialog**. Další informace o tom, jak to provést, naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Chcete-li <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> třídu použít, musíte přidat odkazy na následující sestavení (na kartě Framework v dialogovém okně **Přidat odkaz):**

    - *Presentationcore*

    - *Presentationframework*

    - *Windowsbase*

    - *System.xaml*

3. V *OpenDialog.cs*přidejte `using` následující příkaz:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Deklarujte `TestDialogWindow` třídu <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>s názvem, která je odvozena od :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Chcete-li dialogové okno minimalizovat a <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> maximalizovat, nastavte a na hodnotu true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. V `OpenDialog.ShowMessageBox` metodě nahraďte existující kód následujícím:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Sestavte a spusťte aplikaci. Experimentální instance sady Visual Studio by se měla zobrazit. V nabídce **Nástroje** experimentální instance byste měli vidět příkaz s názvem **Invoke OpenDialog**. Po klepnutí na tento příkaz by se mělo zobrazit dialogové okno. Měli byste být schopni minimalizovat a maximalizovat okno.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Vytvoření a správa dialogového okna, které není odvozeno z dialogového okna

1. Pro tento postup můžete použít řešení **OpenDialogTest,** které jste vytvořili v předchozím postupu, se stejnými odkazy na sestavení.

2. Přidejte `using` následující prohlášení:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Vytvořte třídu s `TestDialogWindow2` <xref:System.Windows.Window>názvem, která je odvozena z :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Přidat soukromý odkaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>na :

    ```
    private IVsUIShell shell;
    ```

5. Přidejte konstruktor, který <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>nastaví odkaz na :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. V `OpenDialog.ShowMessageBox` metodě nahraďte existující kód následujícím:

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

7. Sestavte a spusťte aplikaci. V nabídce **Nástroje** byste měli vidět příkaz s názvem **Invoke OpenDialog**. Po klepnutí na tento příkaz by se mělo zobrazit dialogové okno.
