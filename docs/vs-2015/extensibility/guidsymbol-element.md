---
title: Element GuidSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204226"
---
# <a name="guidsymbol-element"></a>GuidSymbol – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`Element obsahuje identifikátor GUID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz. ID pochází z `IDSymbol` prvku v `GuidSymbol` elementu. `GuidSymbol`Element má `name` atribut, který poskytuje popisný název identifikátoru GUID, který je obsažen v `value` atributu.  
  
## <a name="syntax"></a>Syntax  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|name|Povinná hodnota. Název symbolu GUID|  
|value|Povinná hodnota. Identifikátor GUID symbolu GUID|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[IDSymbol – element](../extensibility/idsymbol-element.md)|Obsahuje ID páru identifikátorů GUID: ID, který představuje nabídku, skupinu nebo příkaz.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Symbols – element](../extensibility/symbols-element.md)|Seskupí `GuidSymbol` elementy v souboru. vsct.|  
  
## <a name="remarks"></a>Poznámky  
 Soubor. vsct obvykle obsahuje tři `GuidSymbol` prvky v jeho `Symbols` části, jednu pro samotný balíček, jednu pro sadu příkazů (kolekci nabídek, skupin a příkazů, které balíček zpřístupňuje), a jeden pro rastrové obrázky, které poskytují ikony pro tlačítka a další vizuální komponenty. Každý `IDSymbol` prvek v daném `GuidSymbol` elementu musí mít jedinečný `value` . Nicméně `IDSymbol` prvky, které mají stejné hodnoty, mohou existovat v balíčku, pokud mají různé nadřazené položky.  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
