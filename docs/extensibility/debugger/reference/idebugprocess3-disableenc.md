---
description: Tato metoda explicitně zakáže funkci upravit a pokračovat v tomto procesu (a všechny programy, které obsahuje).
title: IDebugProcess3::D isableENC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffedebd14f720e006c0bec2044afe80901762b52
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158485"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Tato metoda explicitně zakáže funkci upravit a pokračovat v tomto procesu (a všechny programy, které obsahuje). Vlastní dodavatel portu by měl vždycky vracet `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DisableENC(
   EncUnavailableReason reason
);
```

```csharp
   EncUnavailableReason reason
);
```

## <a name="parameters"></a>Parametry
`reason`\
pro Hodnota z výčtu [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Vlastní dodavatel portu by měl vždycky vracet `E_NOTIMPL` .

## <a name="remarks"></a>Poznámky
 Jakmile je operace Upravit a pokračovat pro proces zakázaná, můžete ji znovu povolit jenom restartováním procesu.

## <a name="see-also"></a>Viz také
- [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)
- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
