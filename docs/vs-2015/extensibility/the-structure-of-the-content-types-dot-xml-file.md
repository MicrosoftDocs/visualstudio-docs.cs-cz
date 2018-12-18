---
title: Struktura Content_types] .xml soubor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5892ab545c41f7d58f0d097f3d27c90c090f0ff
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736579"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Struktura Content_types] .xml souboru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
|                           Hodnota                           |                Popis                |
|-----------------------------------------------------------|-------------------------------------------|
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
 [Referenční dokumentace schématu 1.0 rozšíření VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Novým standardem pro vytváření balíčků dat](http://go.microsoft.com/fwlink/?LinkID=148207)

