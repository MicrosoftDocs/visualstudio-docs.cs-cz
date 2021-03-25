---
description: Určuje, zda vlastní atribut existuje podle názvu.
title: 'IDebugCustomAttributeQuery2:: IsCustomAttributeDefined | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 646fe46f9d83a320423136b8601ee56b3f4ac583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077587"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Určuje, zda vlastní atribut existuje podle názvu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parametry
`pszCustomAttributeName`\
pro Řetězec obsahující název vlastního atributu, který se má najít

## <a name="return-value"></a>Návratová hodnota
 Vrátí S_OK, pokud je vlastní atribut definovaný v tomto poli, jinak vrátí S_FALSE.

## <a name="remarks"></a>Poznámky
 Chcete-li získat bajty atributů přidružené k vlastnímu atributu, zavolejte metodu [GetCustomAttributeByName –](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) .

## <a name="see-also"></a>Viz také
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
