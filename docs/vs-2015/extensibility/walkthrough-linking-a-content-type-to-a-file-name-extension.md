---
title: 'Návod: propojení typu obsahu s příponou názvu souboru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201999"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Návod: Propojení typu obsahu s příponou názvu souboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí rozšíření Editor Managed Extensibility Framework (MEF) můžete definovat vlastní typ obsahu a propojit k němu příponu názvu souboru. V některých případech už přípona názvu souboru je definovaná jazykovou službou. Pokud je však chcete použít s MEF, je nutné ji stále propojit s typem obsahu.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu MEF  
  
1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost**a potom **projekt VSIX**.) Pojmenujte řešení `ContentTypeTest` .  
  
2. V souboru **source. extension. vsixmanifest** klikněte na kartu **aktiva** a nastavte pole **typ** na **Microsoft. VisualStudio. MefComponent**, **zdrojové** pole na **projekt v aktuálním řešení**a pole **projekt** na název projektu.  
  
## <a name="defining-the-content-type"></a>Definování typu obsahu  
  
1. Přidejte soubor třídy a pojmenujte ho `FileAndContentTypes` .  
  
2. Přidejte odkazy na následující sestavení:  
  
    1. System. ComponentModel. složení  
  
    2. Microsoft. VisualStudio. text. Logic  
  
    3. Microsoft. VisualStudio. CoreUtility  
  
3. Přidejte následující `using` direktivy.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4. Deklarujte statickou třídu, která obsahuje definice.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5. V této třídě exportujte <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> název "HID" a deklarujte jeho základní definici jako "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Propojení přípony názvu souboru s typem obsahu  
  
- Chcete-li mapovat tento typ obsahu na příponu názvu souboru, exportujte soubor s <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> příponou. HID a typem obsahu "HID".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Přidání typu obsahu do exportu editoru  
  
1. Vytvořte rozšíření editoru. Můžete například použít rozšíření glyfu marže popsané v [tématu Návod: vytvoření glyfu marže](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Přidejte třídu, kterou jste definovali v tomto postupu.  
  
3. Při exportování třídy rozšíření přidejte <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do ní typ "HID".  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřovací body služeb jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
