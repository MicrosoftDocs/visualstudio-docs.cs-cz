---
title: Vytvoření okna nástroje s více instancemi | Microsoft Docs
description: Naučte se, jak upravit okno nástroje tak, aby bylo možné současně otevřít více instancí. Ve výchozím nastavení může být v oknech nástrojů otevřená jenom jedna instance.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10de60620bcd0b56f251955f478d4d06c984d021
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973998"
---
# <a name="create-a-multi-instance-tool-window"></a>Vytvoření okna nástroje s více instancemi
Můžete programovat okno nástroje, aby bylo možné současně otevřít více instancí. Ve výchozím nastavení může být v oknech nástrojů otevřená jenom jedna instance.

Když použijete okno s více instancemi, můžete zobrazit několik souvisejících zdrojů informací současně. Můžete například umístit víceřádkové <xref:System.Windows.Forms.TextBox> řízení v okně nástroje s více instancemi tak, aby byly během relace programování současně k dispozici několik fragmentů kódu. Můžete také umístit <xref:System.Windows.Forms.DataGrid> ovládací prvek a rozevírací seznam do okna nástroje s více instancemi tak, aby bylo možné současně sledovat několik datových zdrojů v reálném čase.

## <a name="create-a-basic-single-instance-tool-window"></a>Vytvoření základního okna nástroje (s jednou instancí)

1. Vytvořte projekt s názvem **MultiInstanceToolWindow** pomocí šablony VSIX a přidejte šablonu položky vlastního okna nástroje s názvem **MIToolWindow**.

    > [!NOTE]
    > Další informace o vytváření rozšíření pomocí okna nástroje naleznete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Vytvoření více instancí okna nástrojů

1. Otevřete soubor *MIToolWindowPackage.cs* a vyhledejte `ProvideToolWindow` atribut. a `MultiInstances=true` parametr, jak je znázorněno v následujícím příkladu:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. V souboru *MIToolWindowCommand.cs* vyhledejte `ShowToolWindos()` metodu. V této metodě zavolejte <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodu a nastavte její `create` příznak na `false` tak, aby se opakovala prostřednictvím existujících instancí okna nástrojů, dokud `id` není nalezen.

3. Chcete-li vytvořit instanci okna nástroje, zavolejte <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodu a nastavte `id` ji na dostupnou hodnotu a její `create` příznak na `true` .

    Ve výchozím nastavení `id` je hodnota parametru <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metody `0` . Tato hodnota vytvoří podokno nástrojů s jednou instancí. Pro více než jednu instanci, která má být hostována, musí mít každá instance vlastní jedinečný identifikátor `id` .

4. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodu pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekt, který je vrácen <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> vlastností instance okna nástroje.

5. Ve výchozím nastavení `ShowToolWindow` metoda, která je vytvořena šablonou položky okna nástroje, vytvoří okno nástroje s jednou instancí. Následující příklad ukazuje, jak upravit `ShowToolWindow` metodu pro vytvoření více instancí.

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
