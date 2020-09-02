---
title: Vytváření a Správa modálních dialogových oken | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29b0066f201fbb791d471d5cfb433d9a335aa775
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431573"
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Vytváření a správa modálních dialogových oken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vytváření modálního dialogového okna v aplikaci Visual Studio je nutné zajistit, aby nadřazené okno dialogového okna bylo při zobrazení dialogového okna zakázáno, a po zavření dialogového okna znovu povolit nadřazené okno. Pokud to neuděláte, může se zobrazit chyba "Microsoft Visual Studio nejde vypnout, protože je aktivní modální dialogové okno. Zavřete aktivní dialogové okno a zkuste to znovu. "  
  
 Existují dva způsoby, jak to provést. Doporučený způsob, pokud máte dialogové okno WPF, je odvozovat z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> a pak zavolat <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> k zobrazení dialogového okna. Pokud to uděláte, nemusíte spravovat modální stav nadřazeného okna.  
  
 Pokud dialogové okno není WPF nebo z jiného důvodu nemůžete odvodit třídu dialogového okna z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , pak musíte získat nadřízený prvek dialogového okna voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> a správou modálního stavu sami, voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metody s parametrem 0 (NEPRAVDA) před zobrazením dialogového okna a voláním metody s parametrem 1 (true) po zavření dialogového okna.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Vytvoření dialogového okna odvozeného z DialogWindow  
  
1. Vytvořte projekt VSIX s názvem **OpenDialogTest** a přidejte příkaz nabídky s názvem **OpenDialog**. Další informace o tom, jak to provést, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Chcete-li použít <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> třídu, je nutné přidat odkazy na následující sestavení (na kartě rozhraní dialogového okna **Přidat odkaz** ):  
  
    - PresentationCore  
  
    - PresentationFramework  
  
    - WindowsBase  
  
    - System. XAML  
  
3. Do OpenDialog.cs přidejte následující `using` příkaz:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4. Deklarovat třídu s názvem **TestDialogWindow** , která je odvozena z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :  
  
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
  
6. V metodě **OpenDialog. ShowMessageBox** nahraďte existující kód následujícím kódem:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7. Sestavte a spusťte aplikaci. Měla by se zobrazit experimentální instance sady Visual Studio. V nabídce **nástroje** experimentální instance byste měli vidět příkaz s názvem **Invoke OpenDialog**. Po kliknutí na tento příkaz by se mělo zobrazit dialogové okno. Měli byste být schopni minimalizovat a maximalizovat okno.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Vytvoření a Správa dialogového okna, které není odvozeno z DialogWindow  
  
1. Pro tento postup můžete použít řešení **OpenDialogTest** , které jste vytvořili v předchozím postupu, se stejnými odkazy na sestavení.  
  
2. Přidejte následující `using` deklarace:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3. Vytvořte třídu s názvem **TestDialogWindow2** , která je odvozena z <xref:System.Windows.Window> :  
  
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
  
6. V metodě **OpenDialog. ShowMessageBox** nahraďte existující kód následujícím kódem:  
  
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
