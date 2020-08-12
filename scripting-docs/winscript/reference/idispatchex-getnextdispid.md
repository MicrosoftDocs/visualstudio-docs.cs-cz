---
title: 'IDispatchEx –:: GetNextDispID | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNextDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNextDispID method
ms.assetid: 8263d441-85ee-47f4-bdba-fbf2ad07e85f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8811e828a6701769badf45ca7c37f9c53529150f
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144426"
---
# <a name="idispatchexgetnextdispid"></a>IDispatchEx::GetNextDispID

Vytvoří výčet členů objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNextDispID(
   DWORD grfdex,
   DISPID id,
   DISPID *pid
);
```

## <a name="parameters"></a>Parametry

`grfdex`\
Určuje, která sada položek má být vyčíslena. Může se jednat o kombinaci následujících hodnot:

|Hodnota|Význam|
|-----------|-------------|
|fdexEnumDefault|Požaduje, aby objekt vytvořil výčet výchozích prvků. Objekt může vytvořit výčet libovolné sady prvků.|
|fdexEnumAll|Požaduje, aby objekt vyčísluje všechny prvky. Objekt může vytvořit výčet libovolné sady prvků.|

`id`\
Identifikuje aktuálního člena. GetNextDispID načítá položku ve výčtu po tomto. K získání tohoto identifikátoru používá GetDispID nebo předchozí volání GetNextDispID. Používá hodnotu DISPID_STARTENUM k získání prvního identifikátoru první položky.

`pid`\
Adresa proměnné DISPID, která přijímá identifikátor další položky ve výčtu.

Pokud člen odstraní `DeleteMemberByName` nebo `DeleteMemberByDispID` , `DISPID` musí zůstat platné pro `GetNextDispID` .

## <a name="return-value"></a>Návratová hodnota

Vrátí jednu z následujících hodnot:

|Hodnota|Význam|
|-|-|
|`S_OK`|Úspěch.|
|`S_FALSE`|Výčet je hotový.|

## <a name="example"></a>Příklad

```cpp
   HRESULT hr;
   BSTR bstrName;
   DISPID dispid;
   IDispatchEx *pdex;

   // Assign to pdex
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);
   while (hr == NOERROR)
   {
      hr = pdex->GetMemberName(dispid, &bstrName);
      if (!wcscmp(bstrName, OLESTR("Bar")))
      {
         SysFreeString(bstrName);
         return TRUE;
      }
      SysFreeString(bstrName);
      hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);
   }
```

## <a name="see-also"></a>Viz také

- [IDispatchEx – rozhraní](../../winscript/reference/idispatchex-interface.md)
- [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)
- [IDispatchEx::DeleteMemberByName](../../winscript/reference/idispatchex-deletememberbyname.md)
- [IDispatchEx::DeleteMemberByDispID](../../winscript/reference/idispatchex-deletememberbydispid.md)