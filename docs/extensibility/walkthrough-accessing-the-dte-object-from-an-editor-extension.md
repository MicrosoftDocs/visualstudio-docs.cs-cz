---
title: Přístup k objektu DTE z rozšíření editoru
description: Přečtěte si, jak získat přístup k objektu DTE z rozšíření editoru pomocí příkladu kódu v tomto návodu.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 094a37960fa5b32d018eebe3becee4fde43cc392
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905121"
---
# <a name="walkthrough-access-the-dte-object-from-an-editor-extension"></a>Návod: přístup k objektu DTE z rozšíření editoru

V rozhraních VSPackage můžete získat objekt DTE voláním <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody s typem objektu DTE. V rozšíření Managed Extensibility Framework (MEF) můžete importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a následně volat <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodu s typem <xref:EnvDTE.DTE> .

## <a name="prerequisites"></a>Požadavky

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="get-the-dte-object"></a>Získat objekt DTE

1. Vytvořte projekt VSIX v C# a pojmenujte ho **DTETest**. Přidejte šablonu položky **klasifikátoru editoru** a pojmenujte ji **DTETest**.

   Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

::: moniker range=">=vs-2019"

2. Do projektu přidejte následující odkazy na sestavení:

    - Microsoft. VisualStudio. Shell. Framework
    - Microsoft. VisualStudio. Shell. unmutable. 10.0

3. Do souboru *DTETestProvider. cs* přidejte následující `using` direktivy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve `DTETestProvider` třídě importujte <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V `GetClassifier()` metodě přidejte následující kód před `return` příkaz:

    ```csharp
   ThreadHelper.ThrowIfNotOnUIThread();
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

::: moniker range="vs-2017"

2. Do projektu přidejte následující odkazy na sestavení:

   - EnvDTE
   - Microsoft. VisualStudio. Shell. Framework

3. Do souboru *DTETestProvider. cs* přidejte následující `using` direktivy:

    ```csharp
    using EnvDTE;
    using Microsoft.VisualStudio.Shell;
    ```

4. Ve `DTETestProvider` třídě importujte <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .

    ```csharp
    [Import]
    internal SVsServiceProvider ServiceProvider = null;
    ```

5. V `GetClassifier()` metodě přidejte následující kód před `return` příkaz:

    ```csharp
   DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));
   ```

::: moniker-end

## <a name="see-also"></a>Viz také

- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
- [Spuštění sady Visual Studio pomocí DTE](launch-visual-studio-dte.md)
