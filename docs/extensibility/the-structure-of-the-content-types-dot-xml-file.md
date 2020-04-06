---
title: Struktura souboru [Content_types].xml | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761e012d32516265e61c8001491e3c605372ff5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699021"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura souboru [Content_types].xml
Obsahuje informace o druhy obsahu v balíčku VSIX. Visual Studio používá soubor [Content_Types].xml k instalaci balíčku, ale nenainstaluje soubor sám.

> [!NOTE]
> Ačkoli toto téma platí pouze pro soubory [Content_Type].xml, které se používají v balíčcích VSIX, je typ souboru [Content_Types].xml součástí standardu *Open Packaging Conventions (OPC).* Další informace naleznete [v tématu OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) on the MSDN web.

## <a name="attributes-and-elements"></a>Atributy a elementy
 Následující části popisují kořenový prvek a jeho atributy a podřízené prvky.

### <a name="root-element"></a>Kořenový prvek

|Element|Popis|
|-------------|-----------------|
|`Types`|Obsahuje podřízené prvky, které výčet typů souborů v balíčku VSIX.|

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Xmlns`|(Povinné.) Umístění schématu použitého pro tento soubor [Content_Types].xml.|

### <a name="attribute-name-attribute"></a>{Název atributu} Atribut

| Hodnota | Popis |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Umístění schématu typů obsahu. |

### <a name="child-elements"></a>Podřízené elementy
 Prvek `Types` může obsahovat `Default` libovolný počet prvků.

|Element|Popis|
|-------------|-----------------|
|`Default`|Popisuje typ obsahu v balíčku VSIX. Každý typ souboru v balíčku `Default` musí mít svůj vlastní prvek.|

### <a name="attributes"></a>Atributy

|Atribut|Popis|
|---------------|-----------------|
|`Extension`|Přípona názvu souboru v balíčku VSIX.|
|`ContentType`|Popisuje druh obsahu, který je spojen s příponou názvu souboru.|

### <a name="attribute-name-attribute"></a>{Název atributu} Atribut
 Visual Studio rozpozná `ContentType` následující hodnoty `Extension` pro přidružené typy.

|Linka|Contenttype|
|---------------|-----------------|
|Txt|text/prostý|
|pkgdef|text/prostý|
|xml|text/xml|
|vsixmanifest|text/xml|
|htm nebo html|text/html|
|rtf|aplikace/rtf|
|Pdf|aplikace/pdf|
|Gif|obrázek/gif|
|jpg nebo jpeg|obrázek/jpg|
|tiff|obrázek/tiff|
|vsix|aplikace/zip|
|Zip|aplikace/zip|
|Knihovny dll|aplikace/oktet-stream|
|všechny ostatní typy souborů|aplikace/oktet-stream|

## <a name="example"></a>Příklad

### <a name="description"></a>Popis
 Následující soubor [Content_Types].xml popisuje typický balíček VSIX.

### <a name="code"></a>kód

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
- [Odkaz na schéma rozšíření VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: Nový standard pro balení dat](https://msdn.microsoft.com/magazine/cc163372.aspx)
