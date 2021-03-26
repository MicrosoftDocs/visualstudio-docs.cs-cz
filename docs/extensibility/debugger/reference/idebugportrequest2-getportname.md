---
description: Získá název portu.
title: 'IDebugPortRequest2:: GetPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89bff19026a8bbdab72f1bec84c5feef0b37d8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072231"
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
mimo Vrátí název portu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Rozhraní [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) se obvykle předává z ladicího balíčku (klienta) na dodavatele portu (Server) pro získání připojení k portu. Ladicí balíček i dodavatel portu si vědomi možných možností pro port. Pokud jednoduchý řetězec může popisovat port, pak `IDebugPortRequest2::GetPortName` má metoda dostatek informací pro vytvoření připojení. V opačném případě může klient poskytnout další rozhraní, které může server získat pomocí nástroje `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Viz také
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
