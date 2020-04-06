---
title: IDebugCustomViewer::DisplayValue | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732452"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Tato metoda je volána k zobrazení zadané hodnoty.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parametry
`hwnd`\
[v] Nadřazené okno

`dwID`\
[v] ID pro vlastní prohlížeče, které podporují více než jeden typ.

`pHostServices`\
[v] Vyhrazena. Vždy nastavena na hodnotu null.

`pDebugProperty`\
[v] Rozhraní, které lze použít k načtení hodnoty, která má být zobrazena.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Displej je "modální" v tom, že tato metoda vytvoří potřebné okno, zobrazí hodnotu, čeká na vstup a zavře okno, to vše před návratem volajícímu. To znamená, že metoda musí zpracovat všechny aspekty zobrazení hodnoty vlastnosti, od vytvoření okna pro výstup, čekání na vstup uživatele, zničení okna.

 Chcete-li podpořit změnu hodnoty daného objektu [IDebugProperty3,](../../../extensibility/debugger/reference/idebugproperty3.md) můžete použít metodu [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) – pokud lze hodnotu vyjádřit jako řetězec. V opačném případě je nutné vytvořit vlastní rozhraní – výhradní `DisplayValue` pro vyhodnocení výrazu implementující `IDebugProperty3` tuto metodu – na stejný objekt, který implementuje rozhraní. Toto vlastní rozhraní by poskytnout metody pro změnu dat libovolné velikosti nebo složitosti.

## <a name="see-also"></a>Viz také
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)
