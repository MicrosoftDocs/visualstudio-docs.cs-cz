---
title: Propojení typu obsahu s příponou názvu souboru
description: Naučte se, jak propojit vlastní typ obsahu s příponou názvu souboru pomocí editoru Managed Extensibility Framework rozšíření v tomto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fb65f581994c6ba90cbb49166612d81bc00de803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955499"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Návod: propojení typu obsahu s příponou názvu souboru
Můžete definovat vlastní typ obsahu a propojit s ním příponu názvu souboru pomocí rozšíření Editor Managed Extensibility Framework (MEF). V některých případech je přípona názvu souboru již definovaná jazykovou službou. Chcete-li však použít s MEF, je nutné stále propojit s typem obsahu.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `ContentTypeTest` .

2. V souboru **source. extension. vsixmanifest** klikněte na kartu **aktiva** a nastavte pole **typ** na **Microsoft. VisualStudio. MefComponent**, **zdrojové** pole na **projekt v aktuálním řešení** a pole **projekt** na název projektu.

## <a name="define-the-content-type"></a>Definovat typ obsahu

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

## <a name="link-a-file-name-extension-to-a-content-type"></a>Propojení přípony názvu souboru s typem obsahu

- Chcete-li mapovat tento typ obsahu na příponu názvu souboru, exportujte soubor s <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> příponou *. HID* a typem obsahu "HID".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Přidání typu obsahu do exportu editoru

1. Vytvořte rozšíření editoru. Můžete například použít rozšíření glyfu marže popsané v tématu [Návod: vytvoření glyfu marže](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Přidejte třídu, kterou jste definovali v tomto postupu.

3. Při exportování třídy rozšíření přidejte <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> do ní typ "HID".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Viz také
- [Rozšiřovací body služby jazyka a editoru](../extensibility/language-service-and-editor-extension-points.md)
