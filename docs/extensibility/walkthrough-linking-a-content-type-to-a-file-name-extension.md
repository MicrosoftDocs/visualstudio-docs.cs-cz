---
title: 'Návod: Propojení typu obsahu s příponou názvu souboru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697070"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Návod: Propojení typu obsahu s příponou názvu souboru
Můžete definovat vlastní typ obsahu a propojit příponu názvu souboru pomocí rozšíření editoru Managed Extensibility Framework (MEF). V některých případech je přípona názvu souboru již definována jazykovou službou. Chcete-li jej však použít s mef, musíte jej stále propojit s typem obsahu.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `ContentTypeTest`řešení .

2. V souboru **source.extension.vsixmanifest** přejděte na kartu **Datové zdroje** a nastavte pole **Typ** na **Microsoft.VisualStudio.MefComponent**, pole **Zdroj** na projekt **v aktuálním řešení**a pole **Projekt** na název projektu.

## <a name="define-the-content-type"></a>Definování typu obsahu

1. Přidejte soubor třídy `FileAndContentTypes`a pojmenujte jej .

2. Přidejte odkazy na následující sestavení:

    1. System.ComponentModel.Složení

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Přidejte `using` následující direktivy.

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

5. V této třídě <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> exportovat s názvem "hid" a deklarovat jeho základní definice je "text".

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

- Chcete-li tento typ obsahu namapovat <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> na příponu názvu souboru, exportujte a, která má příponu *HID* a typ obsahu "hid".

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

1. Vytvořte rozšíření editoru. Můžete například použít rozšíření okraje glyfu popsané v [návodu: Vytvoření okraje glyfu](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Přidejte třídu, kterou jste definovali v tomto postupu.

3. Při exportu třídy rozšíření <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> přidejte typ "hid".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Viz také
- [Jazykové služby a rozšiřující body editoru](../extensibility/language-service-and-editor-extension-points.md)
