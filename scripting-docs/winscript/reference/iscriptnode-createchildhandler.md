---
title: IScriptNode::CreateChildHandler | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795021"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Přidá skriptletu jako podřízené instanci `IScriptNode`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszDefaultName`  
 [v] Adresa pro přidružení skriptletu výchozí název.  
  
 `prgpszNames`  
 [v části size_is – (`cpszNames`)] seznam identifikátorů z plně kvalifikovaný název na hostiteli.  
  
 `cpszNames`  
 [v] Počet identifikátorů v `prgpszNames` parametr.  
  
 `pszEvent`  
 [v] Adresa vyrovnávací paměti, který identifikuje název události související s skriptletu.  
  
 `pszDelimiter`  
 [v] Adresa koncového ze skriptu bloku oddělovač. Pro analýzu, hostitele většinou používá oddělovač (například dvě jednoduchých uvozovek), na zjištění konce bloku skriptu.  
  
 Oddělovač, který umožňuje předzpracování skriptem vytváření modulu. Modul může například nahraďte jednoduché uvozovky dvě jednoduchých uvozovek pro použití jako oddělovač. Modul určuje, jak se používá jako oddělovač.  
  
 Pokud žádný oddělovač slouží k identifikaci konec bloku skriptu nastavena na hodnotu NULL.  
  
 `ptiSignature`  
 [v] Informace o typu pro objekt funkce.  
  
 `iMethodSignature`  
 [v] Index funkci v `ITypeInfo``ptiSignature` parametr.  
  
 `isn`  
 [v] Index podřízené v nadřazené.  
  
 `dwCookie`  
 [v] Definované aplikací hodnota, která slouží k přiřazení položky objektu hostitele.  
  
 `ppse`  
 [out] Proměnné, která přijímá ukazatel na adresu `IScriptEntry` rozhraní podřízené instance.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Skriptletu určuje obslužné rutiny události. Tato metoda vytvoří skriptletu, pokud je volána metodou `IScriptNode` objekt, který představuje webovou stránku. Tato metoda neproběhne úspěšně, pokud je volána metodou dalších rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Iscriptnode – rozhraní](../../winscript/reference/iscriptnode-interface.md)   
 [Iscriptentry – rozhraní](../../winscript/reference/iscriptentry-interface.md)