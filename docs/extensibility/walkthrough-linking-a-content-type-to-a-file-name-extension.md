---
title: 'Návod: Propojení typu obsahu s příponu názvu souboru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54570ec03788f88f58f14249f200ed2028686c37
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566750"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Návod: Propojení typ obsahu, který má příponu názvu souboru
Můžete definovat vlastní typ obsahu a odkaz na něj příponu názvu souboru s použitím rozšíření editoru Managed Extensibility Framework (MEF). V některých případech přípona souboru už definuje služba jazyka. Ale na jeho použití s MEF, je třeba stále propojit ho typu obsahu.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Vytvořit projekt rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `ContentTypeTest`.  
  
2.  V **source.extension.vsixmanifest** souboru, přejděte na **prostředky** kartu a nastavit **typ** pole **Microsoft.VisualStudio.MefComponent**, **zdroj** pole **projekt v aktuálním řešení**a **projektu** pole pro název projektu.  
  
## <a name="define-the-content-type"></a>Typ obsahu definovat  
  
1.  Přidejte soubor třídy a pojmenujte ho `FileAndContentTypes`.  
  
2.  Přidejte odkazy na následující sestavení:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Přidejte následující `using` direktivy.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Deklarujte statickou třídu, která obsahuje definice.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  V této třídě exportovat <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> s názvem "hid" a deklarovat jeho základní definici, aby se "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="link-a-file-name-extension-to-a-content-type"></a>Odkaz na typ obsahu příponu názvu souboru  
  
-   Pokud chcete namapovat příponu názvu souboru tohoto typu obsahu, exportovat <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> , který má příponu *HID* a typu obsahu "hid".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
         [Export]  
         [Name("hid")]  
         [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
  
         [Export]  
         [FileExtension(".hid")]  
         [ContentType("hid")]  
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;  
    }  
    ```  
  
## <a name="add-the-content-type-to-an-editor-export"></a>Přidat typ obsahu k editoru export  
  
1.  Vytvoření rozšíření editoru. Například můžete použít rozšíření piktogram okraj, je popsáno v [návod: vytvoření okrajového piktogramu](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Přidání třídy, které jste definovali v tomto postupu.  
  
3.  Při exportu rozšíření třídy, přidejte <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> typu "hid" k němu.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Viz také:  
 [Jazykové služby a editor Rozšiřovací body](../extensibility/language-service-and-editor-extension-points.md)