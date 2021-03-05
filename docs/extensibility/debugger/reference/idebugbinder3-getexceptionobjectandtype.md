---
description: Tato metoda načte výjimku přidruženou k objektu, pokud existuje.
title: 'IDebugBinder3:: GetExceptionObjectAndType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetExceptionObjectAndType
helpviewer_keywords:
- IDebugBinder3::GetExceptionObjectAndType method
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ec511cc6145c890c4f62a76563c51aa7c667977
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167630"
---
# <a name="idebugbinder3getexceptionobjectandtype"></a>IDebugBinder3::GetExceptionObjectAndType
Tato metoda načte výjimku přidruženou k objektu, pokud existuje.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetExceptionObjectAndType(
   IDebugObject** ppException,
   IDebugField**  ppField
);
```

```csharp
int GetExceptionObjectAndType(
   out IDebugObject ppException,
   out IDebugField  ppField
);
```

## <a name="parameters"></a>Parametry
`ppException`\
mimo Vrátí objekt představující výjimku.

`ppField`\
mimo Vrátí objekt reprezentující určité pole, které mohlo způsobit výjimku (Tato hodnota může být null).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Chcete-li ověřit, zda existuje výjimka, zkontrolujte hodnotu vrácenou `ppException` : Pokud je hodnota null, není k tomuto objektu přidružena žádná výjimka.

## <a name="see-also"></a>Viz také
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
