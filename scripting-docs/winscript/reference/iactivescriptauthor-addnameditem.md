---
title: 'Iactivescriptauthor –:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577246"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Přidá název položky na kořenové úrovni do oboru názvů modulu vytváření skriptů. *Položka kořenové úrovně* je objekt, který může obsahovat vlastnosti a metody a může také obsahovat zdroj události.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 pro Název položky zobrazený ve skriptu Název musí být jedinečný a trvalý.  
  
 `dwFlags`  
 pro Příznaky, které jsou spojeny s pojmenovanou položkou. Může být kombinací následujících hodnot:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Označuje, že název položky je k dispozici v oboru názvů skriptu. To umožňuje přístup k vlastnostem, metodám a událostem položky.<br /><br /> Podle konvence vlastnosti položky zahrnují podřízené členy položky. Proto jsou všechny vlastnosti podřízeného objektu a metody (a jejich dceřiné členy rekurzivně) přístupné.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Označuje události zdroje položky, které skript může mít obslužné rutiny událostí skriptu.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Označuje, že položka je kolekcí globálních vlastností a metod, které jsou přidruženy ke skriptu. Její členové jsou vytvořeni jako globální proměnné a metody.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Označuje, že položka má být uložena, pokud je uložen modul pro vytváření skriptů.|  
|SCRIPTITEM_CODEONLY|0x00000200|Označuje, že pojmenovaná položka představuje objekt pouze s kódem a nemá člena pro vytváření.|  
|SCRIPTITEM_NOCODE|0x00000400|Označuje, že pojmenovaná položka je pouze přidaný název a nemá nic k vytváření.|  
  
 `pdisp`  
 pro @No__t_0 objektu `NamedItem`, který se používá ke shromažďování metod, vlastností nebo zdroje událostí.  
  
## <a name="return-value"></a>Návratová hodnota  
 @No__t_0. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také:  
 @No__t_1 [rozhraní iactivescriptauthor –](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)