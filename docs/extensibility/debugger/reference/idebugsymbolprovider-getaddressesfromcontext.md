---
title: 'IDebugSymbolProvider:: GetAddressesFromContext | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719429"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Tato metoda mapuje kontext dokumentu na pole adres ladění.

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
pro Kontext dokumentu.

`fStatmentOnly`\
pro Při hodnotě TRUE omezí adresy ladění na jediný příkaz.

`ppEnumBegAddresses`\
mimo Vrátí enumerátor pro počáteční adresy ladění přidružené k tomuto příkazu nebo řádku.

`ppEnumEndAddresses`\
mimo Vrátí enumerátor [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pro koncové adresy ladění přidružené k tomuto příkazu nebo řádku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Kontext dokumentu obvykle indikuje rozsah zdrojových řádků. Tato metoda poskytuje počáteční a koncové adresy ladění přidružené k těmto řádkům. Některé jazyky umožňují příkazy, které jsou rozloženy na více řádků nebo řádky, které obsahují více než jeden příkaz. Tato metoda poskytuje příznak pro omezení adres ladění na jediný příkaz.

 Jeden příkaz může mít několik ladicích adres, jako v případě šablon.

## <a name="see-also"></a>Viz také
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
