---
title: IDebugSymbolProvider::GetAddressesFromContext | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719429"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Tato metoda mapuje kontext dokumentu do pole ladicí adresy.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parametry
`pDocContext`\
[v] Kontext dokumentu.

`fStatmentOnly`\
[v] Pokud TRUE, omezuje ladicí adresy na jeden příkaz.

`ppEnumBegAddresses`\
[out] Vrátí čítač výčtu pro počáteční ladicí adresy přidružené k tomuto příkazu nebo řádku.

`ppEnumEndAddresses`\
[out] Vrátí čítač [výčtu IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pro koncové ladicí adresy přidružené k tomuto příkazu nebo řádku.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext dokumentu obvykle označuje oblast zdrojových řádků. Tato metoda poskytuje počáteční a koncové ladicí adresy přidružené k těmto řádkům. Některé jazyky umožňují příkazy, které zahrnují více řádků nebo řádků, které obsahují více než jeden příkaz. Tato metoda poskytuje příznak omezit ladicí adresy na jeden příkaz.

 Je možné, že jeden příkaz má více ladicích adres, jako v případě šablon.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
