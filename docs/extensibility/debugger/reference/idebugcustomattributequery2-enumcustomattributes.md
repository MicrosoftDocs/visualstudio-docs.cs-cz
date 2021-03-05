---
description: Získá enumerátor pro všechny vlastní atributy připojené k tomuto poli.
title: 'IDebugCustomAttributeQuery2:: EnumCustomAttributes – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 348d5e753702e523f09bef8cbd5f374294c197e4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154441"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Získá enumerátor pro všechny vlastní atributy připojené k tomuto poli.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
mimo Vrátí objekt [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) představující seznam vlastních atributů; v opačném případě vrátí hodnotu null, pokud nejsou k dispozici žádné vlastní atributy.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo S_FALSE, pokud v tomto poli nejsou žádné vlastní atributy. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pole může mít více vlastních atributů.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
