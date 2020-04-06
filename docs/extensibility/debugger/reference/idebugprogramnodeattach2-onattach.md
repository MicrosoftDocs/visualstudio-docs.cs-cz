---
title: IDebugProgramNodeAttach2::OnAttach | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721874"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Připojí se k přidruženému programu nebo odloží proces připojení k metodě [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>Parametry
`guidProgramId`\
[v] `GUID` přiřadit přidruženému programu.

## <a name="return-value"></a>Návratová hodnota
 Pokud je `S_OK`úspěšná, vrátí . Vrátí, `S_FALSE` pokud [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda by neměla být volána. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána během procesu připojení, před [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) metoda je volána. Metoda `OnAttach` může provést samotný proces připojení (v takovém `S_FALSE`případě tato metoda vrátí `IDebugEngine2::Attach` ) `OnAttach` nebo `S_OK`odložit proces připojení k metodě (metoda vrátí). V obou případech `OnAttach` může metoda `GUID` nastavit program, který je `GUID`laděn na daný .

## <a name="see-also"></a>Viz také
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
