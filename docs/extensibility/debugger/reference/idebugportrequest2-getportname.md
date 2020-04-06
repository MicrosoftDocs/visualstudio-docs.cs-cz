---
title: IDebugPortRequest2::GetPortName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724809"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Získá název portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortName( 
   BSTR* pbstrPortName
);
```

```csharp
int GetPortName( 
   out string pbstrPortName
);
```

## <a name="parameters"></a>Parametry
`pbstrPortName`\
[out] Vrátí název portu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 [Rozhraní IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) je obvykle předáno z ladicího balíčku (klienta) dodavateli portu (serveru) za účelem získání připojení k portu. Ladicí balíček i dodavatel portu jsou si vědomi možných možností pro port. Pokud jednoduchý řetězec může popsat port, pak `IDebugPortRequest2::GetPortName` metoda má dostatek informací, aby připojení. V opačném případě mohou být klientovi poskytnuta další rozhraní, `IDebugPortRequest2::QueryInterface`která může server získat pomocí .

## <a name="see-also"></a>Viz také
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
