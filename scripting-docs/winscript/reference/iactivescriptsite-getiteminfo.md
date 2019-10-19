---
title: 'IActiveScriptSite:: GetItemInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c0458f42466a264c30a440b1b14a028a2457f12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570925"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Umožňuje skriptovacímu stroji získat informace o položce přidané pomocí metody [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 pro Název přidružený k položce, jak je uvedeno v metodě [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `dwReturnMask`  
 pro Bitová maska určující, jaké informace o položce mají být vráceny. Skriptovací modul by měl vyžadovat minimální možný objem informací, protože některé návratové parametry (například `ITypeInfo`) mohou trvat značnou dobu, než se načtou nebo vygenerují. Může být kombinací následujících hodnot:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Vrátí rozhraní `IUnknown` pro tuto položku.|  
|SCRIPTINFO_ITYPEINFO|Vrátí rozhraní `ITypeInfo` pro tuto položku.|  
  
 `ppunkItem`  
 mimo Adresa proměnné, která obdrží ukazatel na rozhraní `IUnknown` přidružené k dané položce. Skriptovací stroj může pomocí metody `IUnknown::QueryInterface` získat rozhraní `IDispatch` pro položku. Tento parametr obdrží hodnotu NULL, pokud `dwReturnMask` nezahrnuje hodnotu SCRIPTINFO_IUNKNOWN. Také obdrží hodnotu NULL, pokud k názvu položky není přidružen žádný objekt; Tento mechanismus slouží k vytvoření jednoduché třídy, pokud byla pojmenovaná položka přidána s příznakem SCRIPTITEM_CODEONLY nastaveným v metodě [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) .  
  
 `ppTypeInfo`  
 mimo Adresa proměnné, která obdrží ukazatel na rozhraní `ITypeInfo` přidružené k položce. Tento parametr obdrží hodnotu NULL, pokud `dwReturnMask` nezahrnuje hodnotu SCRIPTINFO_ITYPEINFO, nebo pokud pro tuto položku nejsou k dispozici informace o typu. Pokud informace o typu nejsou k dispozici, objekt nemůže mít zdrojové události a vazba názvu musí být realizovaná pomocí metody `IDispatch::GetIDsOfNames`. Všimněte si, že rozhraní `ITypeInfo` načteno popisuje třídu coclass (TKIND_COCLASS) položky, protože objekt může podporovat více rozhraní a rozhraní události. Pokud položka podporuje rozhraní `IProvideMultipleTypeInfo`, načtené `ITypeInfo` rozhraní je stejné jako index nula `ITypeInfo`, který by byl získán pomocí metody `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Nástup.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`TYPE_E_ELEMENTNOTFOUND`|Položka se zadaným názvem nebyla nalezena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte pouze informace, které jsou označeny parametrem `dwReturnMask`; Tím se zlepší výkon. Například pokud `ITypeInfo` rozhraní není pro položku nutné, není určena pouze v `dwReturnMask`.  
  
## <a name="see-also"></a>Viz také:  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)