---
title: Vytvoření panelu nástrojů s více instancemi | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 19a41e172fd68687cffeca91bdfb4bc418ecdf60
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499764"
---
# <a name="create-a-multi-instance-tool-window"></a>Vytvořit panel nástrojů s více instancemi
Panel nástrojů můžete naprogramovat tak, aby více instancí může být otevřeno současně. Ve výchozím nastavení nástroj windows může mít pouze jednu instanci otevřete.  
  
 Při použití panelu nástrojů s více instancemi můžete zobrazit několik souvisejících zdroje informací ve stejnou dobu. Můžete například umístit více řádky <xref:System.Windows.Forms.TextBox> ovládacího prvku panel nástrojů s více instancemi tak, že jsou během relace programovací současně k dispozici několik fragmentů kódu. Také například můžete umístit <xref:System.Windows.Forms.DataGrid> ovládacího prvku a rozevírací seznam pole v panelu nástrojů s více instancemi tak, aby několik zdrojů dat v reálném čase lze sledovat současně.  
  
## <a name="create-a-basic-single-instance-tool-window"></a>Vytvoření okna nástroje základní (single-instance)  
  
1.  Vytvoření projektu s názvem **MultiInstanceToolWindow** VSIX šablony a přidat šablonu vlastního nástroje okna položku s názvem **MIToolWindow**.  
  
    > [!NOTE]
    >  Další informace o vytváření rozšíření pomocí panelu nástrojů najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="make-a-tool-window-multi-instance"></a>Ujistěte se, s více instancemi okno nástroje  
  
1.  Otevřít *MIToolWindowPackage.cs* souborů a vyhledejte `ProvideToolWindow` atribut. a `MultiInstances=true` parametru, jak je znázorněno v následujícím příkladu:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackage.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  V *MIToolWindowCommand.cs* souboru, vyhledejte `ShowToolWindos()` metody. V této metodě volání <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metoda a nastavte jeho `create` příznak `false` tak, aby se iterovat přes existující instance okno nástrojů do dostupného `id` nenajde.  
  
3.  Chcete-li vytvořit instanci okna nástroje, zavolejte <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metoda a nastavte jeho `id` dostupné hodnotu a jeho `create` příznak `true`.  
  
     Ve výchozím nastavení mají hodnotu `id` parametr <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> je metoda `0`. Tato hodnota je okno nástroje jednou instancí. Pro více než jednu instanci zajistit také jejich hostování, každá instance musí mít svůj vlastní jedinečný `id`.  
  
4.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodu na <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekt, který je vrácený <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> vlastnost instance okno nástroje.  
  
5.  Ve výchozím nastavení `ShowToolWindow` metodu, která je vytvořen pomocí šablony položky okna nástroje vytvoří panel nástrojů s jednou instancí. Následující příklad ukazuje, jak změnit `ShowToolWindow` metodu pro vytvoření víc instancí.  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        for (int i = 0; i < 10; i++)  
        {  
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);  
            if (window == null)  
            {  
                // Create the window with the first free ID.   
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);  
                if ((null == window) || (null == window.Frame))  
                {  
                    throw new NotSupportedException("Cannot create tool window");  
                }  
  
            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
            break;  
            }  
        }  
    }  
    ```