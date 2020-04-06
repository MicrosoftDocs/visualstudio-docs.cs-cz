---
title: IDebugProcess3 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b423ee2cb95ad55296c452cfdc4b891ee4cd26a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723540"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Toto rozhraní představuje spuštěný proces a jeho programy. Toto rozhraní existuje jako náhrada za několik metod v rozhraní [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Poskytuje kontrolu nad všemi programy v procesu.

> [!NOTE]
> [Metody Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)a [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) jsou zastaralé a neměly by se používat. Místo toho použijte `IDebugProcess3` odpovídající metody v rozhraní.

## <a name="syntax"></a>Syntaxe

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno dodavatelem vlastního portu pro správu programů jako skupiny. Pokud jsou programy spravovány jako skupina, můžete řídit jejich provádění a vytvořit jazyk pro vyhodnocení výrazu. Toto rozhraní musí být implementováno dodavatelem portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní je voláno především správcem ladění relace (SDM) za účelem interakce se skupinou programů identifikovaných v tomto procesu.

 Volání [QueryInterface](/cpp/atl/queryinterface) na [rozhraní IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) získat toto rozhraní.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Kromě metod zděděných z [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)implementuje `IDebugProcess3` následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Pokračuje v provádění nebo krokování procesu.|
|[Spuštění](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Zahájí provádění procesu.|
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Kroky vpřed jednu instrukce nebo příkaz v procesu.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Získá důvod, že proces byl spuštěn pro ladění.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Nastaví hostitelský jazyk tak, aby ladicí modul mohl načíst příslušný vyhodnocení výrazu.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Načte jazyk aktuálně nastavený pro tento proces.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Zakáže upravit a pokračovat (ENC) pro tento proces.<br /><br /> Dodavatel vlastního portu tuto metodu neimplementuje (měl by vždy vrátit). `E_NOTIMPL`|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Získejte stav ENC pro tento proces.<br /><br /> Dodavatel vlastního portu tuto metodu neimplementuje (měl by vždy vrátit). `E_NOTIMPL`|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Načte pole jedinečných identifikátorů pro dostupné ladicí moduly.|

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
