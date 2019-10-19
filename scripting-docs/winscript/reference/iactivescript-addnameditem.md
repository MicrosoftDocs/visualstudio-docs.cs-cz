---
title: 'IActiveScript:: AddNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a343e38b944ca36da221da39832046c19b332230
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575816"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Přidá název položky na kořenové úrovni do oboru názvů skriptovacího modulu. Položka kořenové úrovně je objekt s vlastnostmi a metodami, zdrojem události nebo všemi třemi.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 pro Adresa vyrovnávací paměti, která obsahuje název položky zobrazené ze skriptu. Název musí být jedinečný a trvalý.  
  
 `dwFlags`  
 pro Příznaky přidružené k položce Může být kombinací těchto hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Označuje, že pojmenovaná položka představuje objekt pouze s kódem a že hostitel nemá žádné `IUnknown` k tomuto objektu pouze s kódem. Hostitel má pouze název tohoto objektu. V objektově orientovaných jazycích, C++jako je tento příznak vytvoří třídu. Ne všechny jazyky podporují tento příznak.|  
|SCRIPTITEM_GLOBALMEMBERS|Označuje, že položka je kolekcí globálních vlastností a metod přidružených ke skriptu. V normálním případě by skriptovací stroj ignoroval název objektu (jiný než pro účely jeho použití jako soubor cookie pro metodu [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) nebo pro řešení explicitního oboru) a zveřejňuje své členy jako globální proměnné a metody. To umožňuje hostiteli, aby rozšířil knihovnu (běhové funkce atd.), která je k dispozici pro skript. Je ponecháno na skriptovacím stroji, který se zabývat konflikty názvů (například když dvě SCRIPTITEM_GLOBALMEMBERS položky mají metody se stejným názvem), i když by v důsledku této situace neměla být vrácena chyba.|  
|SCRIPTITEM_ISPERSISTENT|Indikuje, že by měla být položka uložena, pokud je uložen skriptovací modul. Podobně nastavení tohoto příznaku označuje, že přechod zpátky do inicializovaného stavu by měl uchovávat název položky a informace o typu (skriptovací stroj musí nicméně uvolnit všechny ukazatele na rozhraní na aktuálním objektu).|  
|SCRIPTITEM_ISSOURCE|Označuje, že položka je zdrojem událostí, které může skript zajímky. Podřízené objekty (vlastnosti objektu, které jsou v samotných objektech) mohou také zdrojové události skriptu. Toto není rekurzivní, ale poskytuje pohodlný mechanizmus pro běžný případ, například vytvoření kontejneru a všech jeho členských ovládacích prvků.|  
|SCRIPTITEM_ISVISIBLE|Označuje, že název položky je k dispozici v oboru názvů skriptu a umožňuje přístup k vlastnostem, metodám a událostem položky. Podle konvence vlastnosti položky zahrnují podřízené položky položky; Proto budou k dispozici všechny vlastnosti podřízeného objektu a metody (a jejich podřízené, rekurzivně).|  
|SCRIPTITEM_NOCODE|Označuje, že položka je jednoduše názvem přidaným do oboru názvů skriptu a neměla by být považována za položku, ke které by měl být kód přidružen. Například bez nastaveného tohoto příznaku vytvoří jazyk VBScript samostatný modul pro pojmenovanou položku a C++ může vytvořit samostatnou obálkovou třídu pro pojmenovanou položku.|  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`E_UNEXPECTED`|Volání nebylo očekáváno (například skriptovací stroj ještě nebyl načten nebo inicializován).|  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScript](../../winscript/reference/iactivescript.md)