---
title: Element licence (schéma jazykové sady VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477078"
---
# <a name="license-element-vsix-language-pack-schema"></a>License – element (schéma jazykové sady VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Volitelné. Cesta k lokalizované verzi souboru s licencí pro rozšíření.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Žádná||  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Žádná||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[LanguagePack – element VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Povinná hodnota. Poskytuje kořenový prvek pro jazykovou sadu VSIX.|  
  
## <a name="text-value"></a>Textová hodnota  
 Relativní cesta k lokalizovanému souboru s licencí, která se má zobrazit  
  
## <a name="remarks"></a>Poznámky  
 Pokud je definován element `License`, zobrazí se text určeného licenčního souboru během instalace a uživatel musí licenci přijmout, aby bylo možné pokračovat.  
  
## <a name="element-information"></a>Informace o elementu  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Obor názvů    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Název schématu   |                 Schéma jazykové sady VSIX                 |
| Soubor ověření |                VSIXLanguagePackSchema. xsd                 |
|  Může být prázdné   |                      Neuvedeno                       |
  
## <a name="see-also"></a>Viz také  
 [Referenční  schématu VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)  
 [Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referenční dokumentace schématu rozšíření VSIX 1,0](/previous-versions/dd393700(v=vs.110))
