---
description: Určuje, zda je ve třídě definováno konkrétní rozhraní.
title: IDebugClassField::D oesInterfaceExist | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::DoesInterfaceExist
helpviewer_keywords:
- IDebugClassField::DoesInterfaceExist method
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4248b653f5eea43a91d0c78a593431d53f5e68b8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173465"
---
# <a name="idebugclassfielddoesinterfaceexist"></a>IDebugClassField::DoesInterfaceExist
Určuje, zda je ve třídě definováno konkrétní rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DoesInterfaceExist( 
   LPCOLESTR pszInterfaceName
);
```

```csharp
int DoesInterfaceExist(
   [In] string pszInterfaceName
);
```

## <a name="parameters"></a>Parametry
`pszInterfaceName`\
pro Řetězec obsahující název rozhraní, který se má hledat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK, vrátí S_FALSE, pokud rozhraní neexistuje. v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda v podstatě získá výčet všech rozhraní a vyhledá v seznamu vyhovující rozhraní.

## <a name="see-also"></a>Viz také
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
