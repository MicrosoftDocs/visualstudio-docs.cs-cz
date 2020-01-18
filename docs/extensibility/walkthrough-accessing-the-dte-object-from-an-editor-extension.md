---
title: Přístup k objektu DTE z rozšíření editoru
ms.date: 04/24/2019
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d023359412b423c9c12d7c7d8a37e79571cbc11a
ms.sourcegitcommit: e3c3d2b185b689c5e32ab4e595abc1ac60b6b9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/18/2020
ms.locfileid: "76269089"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Návod: přístup k objektu DTE z rozšíření editoru

V rozhraních VSPackage můžete získat objekt DTE voláním metody <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> s typem objektu DTE. V rozšíření Managed Extensibility Framework (MEF) můžete importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a pak volat <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodu s typem <xref:EnvDTE.DTE>.

## <a name="prerequisites"></a>Požadavky

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Získat objekt DTE

1. Vytvořte projekt C# VSIX a pojmenujte ho **DTETest**. Přidejte šablonu položky **klasifikátoru editoru** a pojmenujte ji **DTETest**.

   Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Do projektu přidejte následující odkazy na sestavení:

    - Microsoft.VisualStudio.Shell.Framework
    - Microsoft.VisualStudio.Shell.Immutable.10.0

3. Do souboru *DTETestProvider.cs* přidejte následující direktivy `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve třídě `DTETestProvider` importujte <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V metodě `GetClassifier()` přidejte do příkazu `return` následující kód:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Do projektu přidejte následující odkazy na sestavení:

   - EnvDTE
   - Microsoft.VisualStudio.Shell.Framework

3. Do souboru *DTETestProvider.cs* přidejte následující direktivy `using`:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve třídě `DTETestProvider` importujte <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>.

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V metodě `GetClassifier()` přidejte do příkazu `return` následující kód:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Viz také:

- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Spuštění sady Visual Studio pomocí DTE](launch-visual-studio-dte.md)
