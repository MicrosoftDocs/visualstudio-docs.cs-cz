---
title: Licence Element (VSIX Language Pack Schema) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b390c9d390a23a8a5030d06acdb0f2470a946fde
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740315"
---
# <a name="license-element-vsix-language-pack-schema"></a>Licence – Element (VSIX Language Pack schéma)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Volitelné. Cesta lokalizovanou verzi souboru s licencí pro rozšíření.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Žádné||  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|Žádné||  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[LanguagePack – element VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Požadováno. Obsahuje kořenový prvek pro jazykové sady VSIX.|  
  
## <a name="text-value"></a>Textová hodnota  
 Relativní cesta lokalizované licenční soubor, který se má zobrazit.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `License` element definován, pak během instalace se zobrazí text určené licenční soubor a uživatel musí přijmout licenci, abyste mohli pokračovat.  
  
## <a name="element-information"></a>Informace o elementu  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Obor názvů    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Název schématu   |                 VSIX Language Pack Schema                 |
| Soubor ověření |                VSIXLanguagePackSchema.xsd                 |
|  Může být prázdné.   |                      Nelze použít                       |
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)   
 [Referenční dokumentace schématu 1.0 rozšíření VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

