---
title: IActiveScript::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792135"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Název položky kořenové úrovni přidá do oboru názvů skriptovacího stroje. Kořenovou položku je objekt s vlastností a metod, zdroje událostí nebo všechny tři.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [v] Adresa vyrovnávací paměť, která obsahuje název položky, které se zobrazují ve skriptu. Název musí být jedinečný a trvalá.  
  
 `dwFlags`  
 [v] Příznaky přidružený k položce. Může být kombinací těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Určuje, že pojmenovanou položku představuje objekt pouze kód, a hostitel nemá `IUnknown` mají být spojeny s tímto objektem jen kódu. Hostitel má jenom název pro tento objekt. V jazyce objektově orientované například C++ by tento příznak vytvořte třídu. Tento příznak nepodporují všechny jazyky.|  
|SCRIPTITEM_GLOBALMEMBERS|Označuje, že položka je kolekce globální vlastnosti a metody přidružené skript. Za normálních okolností by skriptovací stroj ignorovat název objektu (jiných než pro účely použití jako soubor cookie pro [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metoda, nebo pro vyřešení explicitní rozsahu) a její členy jako globální vystavit proměnné a metody. To umožňuje hostitele do rozšíření knihovny (běhové funkce a tak dále) k dispozici pro skript. Je ponechán na skriptovací stroj jak nakládat s názvem konfliktu (například když dvě položky SCRIPTITEM_GLOBALMEMBERS mají metody se stejným názvem), i když by neměl být vrácena chyba z důvodu této situaci.|  
|SCRIPTITEM_ISPERSISTENT|Označuje, že položka by měla uložit, pokud je uloženo skriptovacího stroje. Podobně nastavení tento příznak určuje, že přechod zpět na inicializovaný stav by měl uchovávat informace název a typ položky (skriptovací stroj však nutné, uvolnit všechny odkazy na rozhraní na vlastním objektu).|  
|SCRIPTITEM_ISSOURCE|Označuje, že položka zdroje události, které můžete skript jímky. Podřízené objekty (vlastnosti objektu, které jsou v samotných objekty) můžete také zdroje událostí do skriptu. Toto není rekurzivní, ale poskytuje vhodný mechanismus pro běžně, například vytvoření kontejneru a všechny její členské ovládací prvky.|  
|SCRIPTITEM_ISVISIBLE|Určuje, zda je název položky k dispozici v oboru názvů skriptu, povolení přístupu k vlastnosti, metod a události položky. Podle konvence vlastnosti položky zahrnují podřízené položky; proto všechny vlastnosti objektu podřízené a metody (a jejich podřízené rekurzivně) budou přístupné.|  
|SCRIPTITEM_NOCODE|Označuje, že položka je jednoduše název přidávané do oboru názvů skript a by neměla být zpracována jako položku, pro které by měly být přidruženy kódu. Bez tento příznak se nastavuje, například VBScript vytvoří samostatný modul pro položku s názvem a C++ může vytvořit samostatné obálkové třídy pro položku s názvem.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Nebyl očekáván volání (například skriptovací stroj ještě byla načtena nebo inicializovat).|  
  
## <a name="see-also"></a>Viz také  
 [IActiveScript –](../../winscript/reference/iactivescript.md)