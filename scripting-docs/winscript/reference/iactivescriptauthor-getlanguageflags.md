---
title: IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793254"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Vrátí jazyk informace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pgrfasa`  
 [out] Příznaky, které obsahují informace jazyk. Může být kombinací následujícího:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Jazyk upřednostní vytvoření obslužné rutiny událostí skriptu skriptem vytváření modulu namísto aplikace.|  
|fasaSupportInternalHandler|0x0002|Jazyk podporuje vytvořen skriptem vytváření modulu obslužné rutiny událostí skriptu.|  
|fasaCaseSensitive|0x0004|Skriptovací jazyk je malá a velká písmena.|  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud skript vytváření modul spravuje obslužné rutiny událostí, vaše aplikace by měly volat `CreateChildHandler` z `IScriptEntry` objektu. Tím se vytvoří `IScriptScriptlet` objekt, který odpovídá obslužné rutiny události. Obslužné rutiny události modul také přidá položku skriptu. Obslužné rutiny události je prázdný funkce, který obsahuje informace o zadané podpisu.  
  
 Pokud vaše aplikace spravuje obslužné rutiny událostí, by měly volat `CreateChildHandler` z `IScriptNode` objekt, který reprezentuje skriptlet obslužná rutina události. Tím se vytvoří `IScriptScriptlet` objekt, který je přidružen skriptlet obslužná rutina události. Aplikace má také přidat prázdný funkce jako událost obslužné rutiny na nový nebo existující `IScriptEntry` objektu.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)