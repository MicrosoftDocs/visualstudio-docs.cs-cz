---
title: IActiveScriptSite::GetItemInfo | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793779"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
Umožňuje skriptovací stroj získat informace o položce přidán s [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrName`  
 [v] Název přidružený k položce, jak je uvedeno v [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metoda.  
  
 `dwReturnMask`  
 [v] Bitová maska určující, které informace o položce má být vrácen. Skriptovací stroj by měla minimální množství informací možný požadavek, protože některé návratový parametry (například `ITypeInfo`) může trvat poměrně dlouho načíst nebo vygenerovat. Může být kombinací následujícího:  
  
|Hodnota|Význam|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|Vrátí `IUnknown` rozhraní pro tuto položku.|  
|SCRIPTINFO_ITYPEINFO|Vrátí `ITypeInfo` rozhraní pro tuto položku.|  
  
 `ppunkItem`  
 [out] Adresy proměnné, která přijímá ukazatel na `IUnknown` rozhraní přidružené k dané položce. Skriptovací stroje můžete použít `IUnknown::QueryInterface` metoda získat `IDispatch` rozhraní pro položku. Tento parametr obdrží hodnotu NULL, pokud `dwReturnMask` nezahrnuje SCRIPTINFO_IUNKNOWN hodnota. Navíc pokud se žádný objekt přidružený název položky; obdrží hodnotu NULL Tento mechanismus se používá k vytvoření jednoduchá při přidání pojmenovanou položku s příznakem SCRIPTITEM_CODEONLY nastaveným [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metoda.  
  
 `ppTypeInfo`  
 [out] Adresy proměnné, která přijímá ukazatel na `ITypeInfo` rozhraní přidružené k položce. Tento parametr obdrží hodnotu NULL, pokud `dwReturnMask` nezahrnuje SCRIPTINFO_ITYPEINFO hodnotu, nebo pokud informace o typu není k dispozici pro tuto položku. Pokud není k dispozici informace o typu, objekt nelze zdroje událostí a vazbu na název musí být realizován pomocí `IDispatch::GetIDsOfNames` metoda. Všimněte si, že `ITypeInfo` rozhraní načíst popisuje položky třída typu coclass (TKIND_COCLASS), protože objekt může podporovat více rozhraní a událostí rozhraní. Pokud položka podporuje `IProvideMultipleTypeInfo` rozhraní, `ITypeInfo` rozhraní načíst je stejný jako index založený na nule `ITypeInfo` který by byl získán, pomocí `IProvideMultipleTypeInfo::GetInfoOfIndex` metoda.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí jednu z následujících hodnot:  
  
|Návratová hodnota|Význam|  
|------------------|-------------|  
|`S_OK`|Úspěch.|  
|`E_INVALIDARG`|Argument byl neplatný.|  
|`E_POINTER`|Byl zadán neplatný ukazatel.|  
|`TYPE_E_ELEMENTNOTFOUND`|Položku se zadaným názvem nebyla nalezena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načítá pouze informace uvedené `dwReturnMask` parametr; to zvyšuje výkon. Například pokud `ITypeInfo` rozhraní není nutný pro položku, není jednoduše zadaný v `dwReturnMask`.  
  
## <a name="see-also"></a>Viz také  
 [Iactivescriptsite –](../../winscript/reference/iactivescriptsite.md)