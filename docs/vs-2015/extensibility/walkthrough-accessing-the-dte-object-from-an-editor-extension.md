---
title: 'Návod: přístup k objektu DTE z rozšíření editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b14b59465b94ddd0a09748f0e309166bf3d4114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148880"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>Návod: Přístup k objektu DTE z rozšíření editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V rozhraních VSPackage můžete získat objekt DTE voláním <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metody s typem objektu DTE. V rozšíření Managed Extensibility Framework (MEF) můžete importovat <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> a následně volat <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> metodu s typem <xref:EnvDTE.DTE> .  
  
## <a name="prerequisites"></a>Předpoklady  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="getting-the-dte-object"></a>Získání objektu DTE  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>Získání objektu DTE z ServiceProvider  
  
1. Vytvořte projekt VSIX v jazyce C# s názvem `DTETest` . Přidejte šablonu položky klasifikátoru editoru a pojmenujte ji `DTETest` . Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
2. Do projektu přidejte následující odkazy na sestavení:  
  
    - EnvDTE  
  
    - EnvDTE80  
  
    - Microsoft. VisualStudio. Shell. unmutable. 10.0  
  
3. Otevřete soubor DTETest.cs a přidejte následující `using` direktivy:  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4. Ve `GetDTEProvider` třídě importujte <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> .  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5. Do `GetClassifier()` metody přidejte následující kód.  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6. Pokud je nutné použít <xref:EnvDTE80.DTE2> rozhraní, můžete do něj přetypovat objekt DTE.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
