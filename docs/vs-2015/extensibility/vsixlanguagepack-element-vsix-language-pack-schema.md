---
title: Element VSIXLanguagePack (schéma jazykové sady VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114226"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack – element (schéma jazykové sady VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Povinná hodnota. Poskytuje kořenový prvek pro jazykovou sadu VSIX. Jazyková sada VSIX poskytuje lokalizované informace o instalaci balíčku VSIX.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`xmlns`|Obor názvů XML, ve kterém je definováno schéma jazykové sady VSIX|  
  
## <a name="xmlns-attribute"></a>Atribut xmlns  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Povinná hodnota. Umístění souboru, který definuje schéma pro jazykové sady.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[LocalizedName – element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Povinná hodnota. Lokalizovaný název rozšíření, které má být nainstalováno.|  
|[LocalizedDescription – element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Povinná hodnota. Lokalizovaný popis rozšíření, které se má nainstalovat|  
|[MoreInfoURL – element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Nepovinný parametr. Odkaz na lokalizované informace o rozšíření.|  
|[License – element](../extensibility/license-element-vsix-language-pack-schema.md)|Nepovinný parametr. Cesta k lokalizované verzi souboru s licencí pro rozšíření.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|Žádné||  
  
## <a name="element-information"></a>Informace o elementu  

:::row:::
    :::column:::
        Obor názvů
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Název schématu
    :::column-end:::
    :::column:::
        Schéma jazykové sady VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Soubor ověření
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Může být prázdné
    :::column-end:::
    :::column:::
        Ne
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma VSX Language Pack – referenční](../extensibility/vsx-language-pack-schema-reference.md) [dokumentace](../extensibility/localizing-vsix-packages.md) [schématu rozšíření VSIX](/previous-versions/dd393700(v=vs.110)) balíčku VSIX – Referenční dokumentace schématu 1,0
