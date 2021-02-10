---
title: Otevření dynamického okna nástroje | Microsoft Docs
description: Přečtěte si o dynamických nástrojích nástrojů, které se otevře při každém použití a zavření konkrétního kontextu uživatelského rozhraní, když se kontext uživatelského rozhraní už nepoužívá.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1998091559f78ed7c7eb8d9585206cf0217d8b2d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946589"
---
# <a name="open-a-dynamic-tool-window"></a>Otevřít dynamické okno nástrojů
Okna nástrojů se obvykle otevírají z příkazu v nabídce nebo ekvivalentní klávesové zkratky. V některých případech však můžete potřebovat okno nástroje, které se otevře vždy, když se použije konkrétní kontext uživatelského rozhraní, a ukončí se, když se kontext uživatelského rozhraní již nepoužívá. Tyto typy oken nástrojů se nazývají *dynamické* nebo *automaticky viditelné*.

> [!NOTE]
> Seznam předdefinovaných kontextů uživatelského rozhraní naleznete v tématu <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .

 Chcete-li otevřít dynamické okno nástroje při spuštění a je možné, že vytvoření selže, je nutné implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> rozhraní a otestovat podmínky selhání v <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodě. Aby prostředí věděli, že máte dynamické okno nástrojů, které by se mělo otevřít při spuštění, musíte `SupportsDynamicToolOwner` do registrace balíčku přidat hodnotu (nastavenou na 1). Tato hodnota není součástí standardu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , takže musíte vytvořit vlastní atribut pro jeho přidání. Další informace o vlastních atributech naleznete v tématu [použití vlastního registračního atributu k registraci rozšíření](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Použijte <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> k otevření okna nástroje. V případě potřeby se vytvoří okno nástroje.

> [!NOTE]
> Dynamické okno nástroje může být zavřeno uživatelem. Pokud chcete vytvořit příkaz nabídky, aby uživatel mohl znovu otevřít okno nástroje, měl by být příkaz nabídky povolen ve stejném kontextu uživatelského rozhraní, který otevírá okno nástroje, a v opačném případě zakázaný.

## <a name="to-open-a-dynamic-tool-window"></a>Otevření dynamického okna nástrojů

1. Vytvořte projekt VSIX s názvem **DynamicToolWindow** a přidejte šablonu položky okna nástroje s názvem *DynamicWindowPane.cs*. Další informace najdete v tématu [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

2. V souboru *DynamicWindowPanePackage.cs* Najděte deklaraci DynamicWindowPanePackage. Přidejte <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> atributy a <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> pro registraci okna nástroje.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Výše uvedené atributy registrují okno nástroje s názvem DynamicWindowPane jako přechodné okno, které není trvalé při zavření a opětovném otevření aplikace Visual Studio. DynamicWindowPane se otevře vždy <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> , když se použije, a v opačném případě zavře.

3. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance. Okno nástroje byste neměli vidět.

4. Otevřete projekt v experimentální instanci. Měl by se zobrazit okno nástroje.
