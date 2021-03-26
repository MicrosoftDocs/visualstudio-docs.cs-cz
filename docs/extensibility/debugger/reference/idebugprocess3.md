---
description: Toto rozhraní představuje běžící proces a jeho programy.
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d08169b196e01b5e2a7effdfe54829d17a970ef3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076508"
---
# <a name="idebugprocess3"></a>IDebugProcess3
Toto rozhraní představuje běžící proces a jeho programy. Toto rozhraní existuje jako náhrada pro několik metod v rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Poskytuje kontrolu nad všemi programy v procesu.

> [!NOTE]
> Metody [Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)a [Step](../../../extensibility/debugger/reference/idebugprogram2-step.md) jsou zastaralé a neměly by již být používány. Místo toho použijte odpovídající metody v `IDebugProcess3` rozhraní.

## <a name="syntax"></a>Syntax

```
IDebugProcess3 : IDebugProcess2
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno vlastním dodavatelem portu pro správu programů jako skupiny. Když jsou programy spravované jako skupina, můžete řídit jejich spouštění a stanovit jazyk pro vyhodnocení výrazu. Toto rozhraní musí být implementováno dodavatelem portu.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Toto rozhraní se nazývá Správce ladění relace (SDM), aby bylo možné komunikovat se skupinou programů identifikovaných v tomto procesu.

 Chcete-li získat toto rozhraní, zavolejte na rozhraní [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) [QueryInterface](/cpp/atl/queryinterface) .

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Kromě metod zděděných z [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) `IDebugProcess3` implementuje následující metody.

|Metoda|Popis|
|------------|-----------------|
|[Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Pokračuje v provádění nebo krokování prostřednictvím procesu.|
|[Spuštěním](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Zahájí provádění procesu.|
|[Krok](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Postup předejte jednu instrukci nebo příkaz v procesu.|
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Získá důvod, proč byl proces spuštěn pro ladění.|
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Nastaví jazyk hostování tak, aby ladicí stroj mohl načíst příslušný vyhodnocovací filtr výrazů.|
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Načte jazyk aktuálně nastavený pro tento proces.|
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Zakáže funkci upravit a pokračovat (ENC) pro tento proces.<br /><br /> Vlastní dodavatel portu neimplementuje tuto metodu (měla by vždycky vracet `E_NOTIMPL` ).|
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Získá stav ENC pro tento proces.<br /><br /> Vlastní dodavatel portu neimplementuje tuto metodu (měla by vždycky vracet `E_NOTIMPL` ).|
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Načte pole jedinečných identifikátorů pro dostupné moduly ladění.|

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
