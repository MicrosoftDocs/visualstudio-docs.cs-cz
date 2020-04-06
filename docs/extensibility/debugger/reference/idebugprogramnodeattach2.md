---
title: IDebugProgramNodeAttach2 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d527dfcfcd09e4d70adca86436aa56e1852bee70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721830"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umožňuje upozorňování uzlu programu na pokus o připojení k přidruženému programu.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno ve stejné třídě, která implementuje rozhraní [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) za účelem přijetí oznámení o operaci připojení a poskytnutí příležitosti ke zrušení operace připojení.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Získat toto rozhraní `QueryInterface` voláním metody v objektu [IDebugProgramNode2.](../../../extensibility/debugger/reference/idebugprogramnode2.md) [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Metoda musí být volána před [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda dát uzlu programu možnost zastavit proces připojení.

## <a name="methods-in-vtable-order"></a>Metody v pořadí Vtable
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Připojí se k přidruženému programu nebo odloží proces připojení k metodě [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je upřednostňovanou alternativou k zastaralé [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) metody. Všechny ladicí moduly `CoCreateInstance` jsou vždy načteny s funkcí, to znamená, že jsou vytvořena instance mimo adresní prostor programu, který je laděn.

 Pokud předchozí implementace `IDebugProgramNode2::Attach_V7` metody byla jednoduše `GUID` nastavení programu, který je laděn, pak je třeba implementovat pouze [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metoda.

 Pokud předchozí implementace `IDebugProgramNode2::Attach_V7` metody používá rozhraní zpětného volání, které bylo poskytnuto, pak tato funkce musí `IDebugProgramNodeAttach2` být přesunuta do implementace [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody a rozhraní nemusí být implementováno.

## <a name="requirements"></a>Požadavky
 Záhlaví: Msdbg.h

 Obor názvů: Microsoft.VisualStudio.Debugger.Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
