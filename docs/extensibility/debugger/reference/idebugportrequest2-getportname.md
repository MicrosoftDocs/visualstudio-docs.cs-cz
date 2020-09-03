---
title: 'IDebugPortRequest2:: GetPort | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
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
mimo Vrátí název portu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Rozhraní [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) se obvykle předává z ladicího balíčku (klienta) na dodavatele portu (Server) pro získání připojení k portu. Ladicí balíček i dodavatel portu si vědomi možných možností pro port. Pokud jednoduchý řetězec může popisovat port, pak `IDebugPortRequest2::GetPortName` má metoda dostatek informací pro vytvoření připojení. V opačném případě může klient poskytnout další rozhraní, které může server získat pomocí nástroje `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Viz také
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
