---
title: Struktura souboru Content_types]. XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395361"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Struktura souboru [Content_types].xml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsahuje informace o typech obsahu v balíčku VSIX. Sada Visual Studio používá soubor [Content_Types]. XML k instalaci balíčku, ale neinstaluje samotný soubor.  
  
> [!NOTE]
> I když toto téma se týká pouze souborů [Content_Type]. XML, které se používají v balíčcích VSIX, typ souboru [Content_Types]. XML je součástí standardu *OPC (Open Package Conventions)* . Další informace najdete v tématu [OPC: nový standard pro balení dat](https://msdn.microsoft.com/magazine/cc163372.aspx) na webu MSDN.  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují kořenový prvek a jeho atributy a podřízené prvky.  
  
### <a name="root-element"></a>Kořenový element  
  
|Element|Popis|  
|-------------|-----------------|  
|`Types`|Obsahuje podřízené prvky, které vyčíslují typy souborů v balíčku VSIX.|  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Xmlns`|(Povinné.) Umístění schématu používaného pro tento soubor [Content_Types]. XML.|  
  
### <a name="attribute-name-attribute"></a>{Název atributu} Přidělen  
  
|                           Hodnota                           |                Popis                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | Umístění schématu typů obsahu. |
  
### <a name="child-elements"></a>Podřízené elementy  
 `Types`Element může obsahovat libovolný počet `Default` prvků.  
  
|Element|Popis|  
|-------------|-----------------|  
|`Default`|Popisuje typ obsahu v balíčku VSIX. Každý typ souboru v balíčku musí mít svůj vlastní `Default` element.|  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Extension`|Přípona názvu souboru v balíčku VSIX.|  
|`ContentType`|Popisuje druh obsahu, který je přidružen k příponě názvu souboru.|  
  
### <a name="attribute-name-attribute"></a>{Název atributu} Přidělen  
 Visual Studio rozpoznává následující `ContentType` hodnoty pro přidružené `Extension` typy.  
  
|Rozšíření|Třída|  
|---------------|-----------------|  
|txt|Text/prostý|  
|pkgdef|Text/prostý|  
|xml|text/XML|  
|vsixmanifest|text/XML|  
|htm nebo HTML|text/html|  
|připojeny|aplikace/RTF|  
|formátu|aplikace/PDF|  
|ve|obrázek/GIF|  
|jpg nebo JPEG|Obrázek/jpg|  
|tiff|obrázek/TIFF|  
|vsix|aplikace/zip|  
|věřitel|aplikace/zip|  
|DLL|aplikace/oktet – Stream|  
|všechny ostatní typy souborů|aplikace/oktet – Stream|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující soubor [Content_Types]. XML popisuje typický balíček VSIX.  
  
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
 [Referenční dokumentace schématu rozšíření VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: nový standard pro vytváření balíčků dat](https://msdn.microsoft.com/magazine/cc163372.aspx)
