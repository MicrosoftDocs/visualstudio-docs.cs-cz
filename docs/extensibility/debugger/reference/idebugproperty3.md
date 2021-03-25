---
title: IDebugProperty3 | Microsoft Docs
description: Toto rozhraní poskytuje podporu pro načtení libovolného dlouhého řetězce přidruženého k vlastnosti, přidružení jedinečného ID k vlastnosti, načítání seznamu vlastních čtenářů pro danou vlastnost, nastavení hodnoty vlastnosti s možností oznamovat případné chyby.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 933810ac5b1e0ba34edf7cfe8d4303180c862fe2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083905"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Toto rozhraní poskytuje podporu pro:

- Načítají se libovolně dlouhý řetězec přidružený k vlastnosti.

- Přidružení jedinečného ID k vlastnosti.

- Načítají se seznam vlastních prohlížečů pro danou vlastnost.

- Nastavení hodnoty vlastnosti s možností oznamovat všechny výsledné chyby

## <a name="syntax"></a>Syntax

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Ladicí stroj (DE) implementuje toto rozhraní na stejném objektu, který implementuje [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) k zajištění podpory pro dlouhé řetězce, ID vlastností a vlastní prohlížeče.

## <a name="notes-for-callers"></a>Poznámky pro volající
 [](/cpp/atl/queryinterface) `IDebugProperty2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z `IDebugProperty2` `IDebugProperty3` rozhraní zpřístupňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Vrátí délku řetězce přidruženého k vlastnosti.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Vrátí řetězec v uživatelsky zadané vyrovnávací paměti.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Vytvoří jedinečné ID pro tuto vlastnost.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Odstraní jedinečné ID pro tuto vlastnost.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Vrátí počet vlastních návštěvníků, se kterými se dá tato vlastnost zobrazit.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Vrátí seznam vlastních návštěvníků, se kterými se dá tato vlastnost zobrazit.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Nastaví hodnotu této vlastnosti a vrátí chybovou zprávu, pokud se něco pokazilo.|

## <a name="remarks"></a>Poznámky
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) je upřednostňovaný způsob, jakým Správce ladění relací (SDM) nastaví hodnotu vlastnosti.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
