---
title: Přístup k objektu DTE z rozšíření editoru
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e37bdb21b7c8132f0dfb166d19e03d36e838245d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697662"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Návod: Přístup k objektu DTE z rozšíření editoru

V VSPackages můžete získat dte objekt <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> voláním metody s typem dte objektu. V rozšíření chození rozšiřitelnosti (MEF) můžete <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> importovat a <xref:EnvDTE.DTE>volat metodu s typem .

## <a name="prerequisites"></a>Požadavky

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Získání objektu DTE

1. Vytvořte projekt C# VSIX a pojmenujte jej **DTETest**. Přidejte šablonu **položky třídění editoru** a pojmenujte ji **DTETest**.

   Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Do projektu přidejte následující odkazy na sestavení:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Do *DTETestProvider.cs* souboru přidejte následující `using` direktivy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve `DTETestProvider` třídě importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V `GetClassifier()` metodě přidejte následující `return` kód před příkaz:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Do projektu přidejte následující odkazy na sestavení:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Do *DTETestProvider.cs* souboru přidejte následující `using` direktivy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve `DTETestProvider` třídě importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V `GetClassifier()` metodě přidejte následující `return` kód před příkaz:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Viz také

- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Spuštění sady Visual Studio pomocí DTE](launch-visual-studio-dte.md)
