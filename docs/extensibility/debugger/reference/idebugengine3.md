---
title: IDebugEngine3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3
helpviewer_keywords:
- IDebugEngine3 interface
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7026156eac7f60e7435e32244c3cc03ae5f08e1e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730654"
---
# <a name="idebugengine3"></a>IDebugEngine3
Představuje jeden ladicí modul (DE), který řídí ladění jednoho nebo více modulů.

## <a name="syntax"></a>Syntaxe

```
IDebugEngine3 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastní DE (pokud podporuje symboly) povolit JustMyCode stavu. Toto rozhraní musí být implementováno DE, pokud podporuje symboly a JustMyCode.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je voláno správcem ladění relace (SDM) předat možnosti uživatele pro umístění, ze kterých chcete načíst symboly. Je také volána k nastavení IDENTIFIKÁTOR GUID motoru, když je vytvořena instance (tento identifikátor GUID je založen na metriky od okamžiku registrace motoru). SDM také volá toto rozhraní nastavit JustMyCode stavu a nastavit všechny výjimky známé ladicím programem do zadaného stavu.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)rozhraní `IDebugEngine3` zveřejňuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Nastaví cestu nebo cesty, které de použije k hledání ladicích symbolů.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Načte symboly pro všechny moduly, které ještě neměly své symboly načteny.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Informuje DE o justmycode informace.|
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Nastaví identifikátor GUID DE z metriky.|
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Nastavte všechny výjimky, které jsou aktuálně nevyřešené, do zadaného stavu.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
