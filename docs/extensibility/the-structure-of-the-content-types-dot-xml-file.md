---
title: Struktura souboru [Content_types].xml | Microsoft Docs
description: Seznamte se se strukturou souboru typů obsahu, který obsahuje informace o typech obsahu v balíčku VSIX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 96d4d0eeea34300894674a2105d080e8a6abb607
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900418"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura souboru [Content_types].xml
Obsahuje informace o typech obsahu v balíčku VSIX. Visual Studio balíček .xml pomocí souboru [Content_Types], ale neinstaluje samotný soubor.

> [!NOTE]
> I když se toto téma týká pouze souborů [Content_Type].xml, které se používají v balíčcích VSIX, typ souboru [Content_Types].xml je součástí standardu *OPC (Open Packaging Conventions).* Další informace najdete v tématu [OPC: Nový standard pro balení dat](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data) na webu MSDN.

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují kořenový prvek a jeho atributy a podřízené prvky.

### <a name="root-element"></a>Kořenový element

|Element|Popis|
|-------------|-----------------|
|`Types`|Obsahuje podřízené elementy, které vyčíslí typy souborů v balíčku VSIX.|

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Xmlns`|(Povinné.) Umístění schématu použitého pro tento soubor [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>{Název atributu} Atribut

| Hodnota | Popis |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Umístění schématu typů obsahu. |

### <a name="child-elements"></a>Podřízené elementy
 Element `Types` může obsahovat libovolný počet `Default` prvků.

|Element|Popis|
|-------------|-----------------|
|`Default`|Popisuje typ obsahu v balíčku VSIX. Každý typ souboru v balíčku musí mít svůj vlastní `Default` prvek.|

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Extension`|Přípona názvu souboru v balíčku VSIX.|
|`ContentType`|Popisuje druh obsahu, který je přidružen k příponě názvu souboru.|

### <a name="attribute-name-attribute"></a>{Název atributu} Atribut
 Visual Studio přidružené typy rozpozná `ContentType` následující `Extension` hodnoty.

|Linka|Contenttype|
|---------------|-----------------|
|Txt|text / prostý text|
|pkgdef|text / prostý text|
|xml|text/xml|
|vsixmanifest|text/xml|
|html nebo html|text/html|
|rtf (rtf)|application/rtf|
|Pdf|application/pdf|
|Gif|obrázek/gif|
|jpg nebo jpeg|image/jpg|
|tiff|image/tiff|
|vsix|application/zip|
|Zip|application/zip|
|Knihovny dll|application/octet-stream|
|všechny ostatní typy souborů|application/octet-stream|

## <a name="example"></a>Příklad

### <a name="description"></a>Description
 Následující soubor [Content_Types].xml popisuje typický balíček VSIX.

### <a name="code"></a>Kód

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Viz také
- [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Referenční informace k rozšíření VSIX Schema 1.0](/previous-versions/dd393700(v=vs.110))
- [OPC: Nový standard pro balení dat](/archive/msdn-magazine/2007/august/opc-a-new-standard-for-packaging-your-data)