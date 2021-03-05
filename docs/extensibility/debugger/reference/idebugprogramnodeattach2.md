---
description: Umožňuje, aby byl uzel programu upozorněn na pokus o připojení k přidruženému programu.
title: IDebugProgramNodeAttach2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2
helpviewer_keywords:
- IDebugProgramNodeAttach2 interface
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aa623097224afc4f3a6b93d6b98ece0e14149ca5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171731"
---
# <a name="idebugprogramnodeattach2"></a>IDebugProgramNodeAttach2
Umožňuje, aby byl uzel programu upozorněn na pokus o připojení k přidruženému programu.

## <a name="syntax"></a>Syntax

```
IDebugProgramNodeAttach2 : IUnknown
```

## <a name="notes-for-implementers"></a>Poznámky pro implementátory
 Toto rozhraní je implementováno na stejné třídě, která implementuje rozhraní [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , aby bylo možné získat oznámení o operaci připojení a poskytnout příležitost k zrušení operace připojení.

## <a name="notes-for-callers"></a>Poznámky pro volající
 Získejte toto rozhraní voláním `QueryInterface` metody v objektu [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) . Metoda [Attach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) musí být volána před metodou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) , aby mohl uzel programu vyvolat zastavení procesu připojení.

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 Toto rozhraní implementuje následující metodu:

|Metoda|Popis|
|------------|-----------------|
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Připojí se k přidruženému programu nebo odloží proces připojení k metodě [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|

## <a name="remarks"></a>Poznámky
 Toto rozhraní je upřednostňovanou alternativou nepoužívané metody [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) . Všechny moduly ladění jsou vždy načteny pomocí `CoCreateInstance` funkce, to znamená, že jsou vytvořeny mimo adresní prostor programu, který je laděn.

 Pokud předchozí implementace `IDebugProgramNode2::Attach_V7` metody jednoduše nastavuje `GUID` ladit program, musí být implementována pouze metoda [Attach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .

 Pokud předchozí implementace `IDebugProgramNode2::Attach_V7` metody použila rozhraní zpětného volání, které bylo poskytnuto, pak musí být tato funkce přesunuta do implementace metody [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) a `IDebugProgramNodeAttach2` rozhraní není nutné implementovat.

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
