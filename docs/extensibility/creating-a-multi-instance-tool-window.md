---
title: Vytvoření okna nástroje s více instancemi | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739621"
---
# <a name="create-a-multi-instance-tool-window"></a>Vytvoření okna nástroje pro více instancí
Okno nástroje můžete naprogramovat tak, aby bylo možné současně otevřít více instancí. Ve výchozím nastavení může mít okna nástrojů otevřenou pouze jednu instanci.

Při použití okna nástroje pro více instancí můžete zobrazit několik souvisejících zdrojů informací současně. Můžete například umístit víceřádkový <xref:System.Windows.Forms.TextBox> ovládací prvek do okna nástroje s více instancemi, aby bylo během programovací relace současně k dispozici několik fragmentů kódu. Můžete také například umístit <xref:System.Windows.Forms.DataGrid> ovládací prvek a rozevírací seznam do okna nástroje pro více instancí, aby bylo možné sledovat několik zdrojů dat v reálném čase současně.

## <a name="create-a-basic-single-instance-tool-window"></a>Vytvoření základního okna nástroje (s jednou instancí)

1. Vytvořte projekt s názvem **MultiInstanceToolWindow** pomocí šablony VSIX a přidejte vlastní šablonu položky okna nástroje s názvem **MIToolWindow**.

    > [!NOTE]
    > Další informace o vytvoření rozšíření pomocí okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Vytvoření víceindicí okna nástroje

1. Otevřete soubor *MIToolWindowPackage.cs* `ProvideToolWindow` a vyhledejte atribut. a `MultiInstances=true` parametr, jak je znázorněno v následujícím příkladu:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. V *souboru MIToolWindowCommand.cs* `ShowToolWindos()` najděte metodu. V této metodě <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> volání metody `create` a `false` nastavte její příznak tak, aby bude iterovat prostřednictvím existující instance okna nástroje, dokud je nalezen k dispozici. `id`

3. Chcete-li vytvořit instanci <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> okna nástroje, zavolejte metodu a nastavte její `id` hodnotu na dostupnou hodnotu a její `create` příznak na `true`.

    Ve výchozím nastavení je `id` `0`hodnota <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> parametru metody . Tato hodnota vytvoří okno nástroje jedné instance. Pro více než jednu instanci, která má `id`být hostována, musí mít každá instance své vlastní jedinečné .

4. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody na <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objekt, který <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> je vrácen vlastností instance okna nástroje.

5. Ve výchozím `ShowToolWindow` nastavení metoda vytvořená šablonou položky okna nástroje vytvoří okno nástroje pro jednu instanci. Následující příklad ukazuje, jak `ShowToolWindow` upravit metodu pro vytvoření více instancí.

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
