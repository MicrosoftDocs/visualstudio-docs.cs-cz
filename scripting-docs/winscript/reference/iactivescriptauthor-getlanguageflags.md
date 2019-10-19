---
title: 'Iactivescriptauthor –:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576193"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Vrátí informace o jazyce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pgrfasa`  
 mimo Příznaky obsahující informace o jazyce Může být kombinací následujících hodnot:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|Jazyk upřednostňuje vytváření obslužných rutin událostí skriptu místo aplikace pomocí modulu vytváření skriptů.|  
|fasaSupportInternalHandler|0x0002|Jazyk podporuje obslužné rutiny událostí skriptů vytvořené modulem vytváření skriptů.|  
|fasaCaseSensitive|0x0004|Skriptovací jazyk rozlišuje velká a malá písmena.|  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud modul pro vytváření skriptů spravuje obslužné rutiny událostí, měla by vaše aplikace volat `CreateChildHandler` z objektu `IScriptEntry`. Tím se vytvoří objekt `IScriptScriptlet`, který odpovídá obslužné rutině události. Modul také přidá obslužnou rutinu události do položky skriptu. Obslužná rutina události je prázdná funkce, která obsahuje zadané informace o podpisu.  
  
 Pokud vaše aplikace spravuje obslužné rutiny událostí, měla by volat `CreateChildHandler` z objektu `IScriptNode`, který představuje obslužnou rutinu události skriptletu. Tím se vytvoří objekt `IScriptScriptlet`, který je přidružen k obslužné rutině události skriptletu. Aplikace také musí přidat prázdnou funkci jako obslužnou rutinu události do nového nebo existujícího objektu `IScriptEntry`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptAuthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)