---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732559"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Získá vlastní atributy bajtů zadaný název vlastního atributu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>Parametry
`pszCustomAttributeName`\
[v] Řetězec obsahující název vlastního atributu, který chcete vyhledat.

`ppBlob`\
[dovnitř, ven] Pole, které je vyplněno bajty vlastního atributu.

`pdwLen`\
[dovnitř, ven] Určuje maximální počet bajtů, které `ppBlob` mají být vráceny v poli, a vrátí počet bajtů skutečně zapsaných do pole.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud vlastní atribut neexistuje. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Nastavte `ppBlob` parametr na hodnotu null, chcete-li vrátit počet dostupných bajtů atributů. Pak přidělit pole a předat `ppBlob` toto pole v pro parametr.

 Bajty atributu představují nezpracovaná data vlastního atributu.

 Pokud `ppBlob` a `pdwLen` parametry jsou nastaveny na hodnotu null, tato metoda lze určit, pokud vlastní atribut pouze existuje. Jednodušší alternativou je však volání [metody IsCustomAttributeDefined.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Viz také
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
