---
title: IActiveScriptAuthor::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793275"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Přidá název položky kořenové úrovně do skriptu pro tvorbu názvů stroje. A *kořenovou položku* je objekt obsahující vlastnosti a metody a může obsahovat také zdroje událostí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [v] Název položky, které se zobrazují ve skriptu. Název musí být jedinečný a trvalá.  
  
 `dwFlags`  
 [v] Příznaky, které jsou spojeny s pojmenovanou položku. Může být kombinací následujícího:  
  
|Konstanta|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Určuje, zda je název položky k dispozici v oboru názvů skriptu. To umožňuje přístup k vlastnosti položky, metod a události.<br /><br /> Podle konvence vlastnosti položky zahrnout členy podřízené položky. Proto všechny vlastnosti objektu podřízené a metody (a jejich podřízené členy, rekurzivně) jsou dostupné.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Určuje zdroj položek událostí, skript můžou mít obslužné rutiny událostí skriptu.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Označuje, že položka je kolekce globální vlastnosti a metody, které jsou spojeny pomocí skriptu. Členy jsou vytvořené jako globální proměnné a metody.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Označuje, že pokud je uloženo skript vytváření modul by měl uložit položky.|  
|SCRIPTITEM_CODEONLY|0x00000200|Označuje, že pojmenovanou položku představuje objekt pouze kód, a nemá členem, abyste mohli vytvořit.|  
|SCRIPTITEM_NOCODE|0x00000400|Označuje, že je právě název přidávané pojmenovanou položku, a má nic k vytváření.|  
  
 `pdisp`  
 [v] `IDispatch` z `NamedItem` objekt, který se používá ke shromažďování metody, vlastnosti nebo zdroj události.  
  
## <a name="return-value"></a>Návratová hodnota  
 `HRESULT`. Možné hodnoty zahrnují hodnoty v následující tabulce, ale nejsou na ně omezeny.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptauthor – rozhraní](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)