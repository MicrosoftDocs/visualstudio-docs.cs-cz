---
description: Vytvoří národní prostředí, které se bude používat pro všechny prostředky specifické pro národní prostředí.
title: 'IDebugProgramProvider2:: SetLocale | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::SetLocale
helpviewer_keywords:
- IDebugProgramProvider2::SetLocale
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23a6cc5b2724e925efcb9b7f4d6f272fc808121
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102167006"
---
# <a name="idebugprogramprovider2setlocale"></a>IDebugProgramProvider2::SetLocale
Vytvoří národní prostředí, které se bude používat pro všechny prostředky specifické pro národní prostředí.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetLocale(
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parametry
`wLangID`\
pro ID jazyka, který se má vytvořit Například 1033 pro angličtinu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
