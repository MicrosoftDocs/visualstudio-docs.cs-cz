---
title: Struktura souboru [Content_types] .xml | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 538a518d1186dc50a9e5e89635af0a07c2542041
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893270"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struktura souboru [Content_types].xml
Obsahuje informace o druzích obsah v balíčku souboru VSIX. Visual Studio používá k instalaci balíčku souboru [Content_Types] .xml, ale nenainstaluje samotný soubor.  
  
> [!NOTE]
>  I když toto téma se týká pouze soubory XML [Content_Type], které se používají v balíčků VSIX, typ souboru [Content_Types] .xml je součástí *Open Packaging konvence (OPC)* standard. Další informace najdete v tématu [OPC: A nový standardní pro vytváření balíčků dat](http://go.microsoft.com/fwlink/?LinkID=148207) na webové stránce MSDN.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují kořenovým prvkem a jeho atributy a podřízené prvky.  
  
### <a name="root-element"></a>Kořenový Element  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Types`|Obsahuje podřízené prvky, které zobrazí výčet typů souborů v balíčku souboru VSIX.|  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Xmlns`|(Povinné). Umístění schéma používané k tomuto souboru [Content_Types] .xml.|  
  
### <a name="attribute-name-attribute"></a>{Atribut name} Atribut  
  
| Hodnota | Popis |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Umístění schématu typy obsahu. |
  
### <a name="child-elements"></a>Podřízené elementy  
 `Types` Element může obsahovat libovolný počet `Default` elementy.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`Default`|Popisuje typ obsahu v balíčku souboru VSIX. Všechny typy souborů v balíčku musí mít svůj vlastní `Default` elementu.|  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Extension`|Přípona názvu souboru souboru v balíčku souboru VSIX.|  
|`ContentType`|Popisuje typ obsahu, který je spojen s příponou názvu souboru.|  
  
### <a name="attribute-name-attribute"></a>{Atribut name} Atribut  
 Visual Studio rozpoznává následující `ContentType` hodnoty pro přidružený `Extension` typy.  
  
|Rozšíření|contentType|  
|---------------|-----------------|  
|TXT|text/plain|  
|pkgdef|text/plain|  
|XML|text/xml|  
|vsixmanifest|text/xml|  
|htm nebo html|text/html|  
|RTF|aplikace/rtf|  
|soubor PDF|aplikace/pdf|  
|GIF|image/gif|  
|JPG nebo jpeg|obrázek nebo jpg|  
|TIFF|Image/tiff|  
|vsix|aplikace/zip|  
|PSČ|aplikace/zip|  
|knihovny DLL|application/octet-stream|  
|všechny ostatní typy souborů|application/octet-stream|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následujícího souboru [Content_Types] .xml popisuje typického balíčku VSIX.  
  
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
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referenční dokumentace schématu 1.0 rozšíření VSIX](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Novým standardem pro vytváření balíčků dat](http://go.microsoft.com/fwlink/?LinkID=148207)