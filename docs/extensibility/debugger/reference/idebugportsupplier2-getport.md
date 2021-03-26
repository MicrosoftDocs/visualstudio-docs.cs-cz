---
description: Získá port od dodavatele portu.
title: 'IDebugPortSupplier2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPort
helpviewer_keywords:
- IDebugPortSupplier2::GetPort
ms.assetid: d55d5055-7386-4037-bf22-4c3e434a99ca
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c5626ce41181a711aafb7dbf26bbe5a65f218c9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072166"
---
# <a name="idebugportsupplier2getport"></a>IDebugPortSupplier2::GetPort
Získá port od dodavatele portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPort( 
   REFGUID       guidPort,
   IDebugPort2** ppPort
);
```

```csharp
int GetPort( 
   ref Guid        guidPort,
   out IDebugPort2 ppPort
);
```

## <a name="parameters"></a>Parametry
`guidPort`\
pro Globálně jedinečný identifikátor (GUID) portu.

`ppPort`\
mimo Vrátí objekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , který představuje port.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Vrátí `E_PORTSUPPLIER_NO_PORT` , pokud neexistuje žádný port s daným identifikátorem.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
