---
title: 'IDebugArrayField:: GetRank | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10f42ca10496d89955032bd531651186d0aecf37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926350"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Získá rozměr nebo počet rozměrů pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parametry
`pdwRank`\
mimo Vrátí pořadí.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Rozměr pole odpovídá počtu rozměrů. Multidimenzionální pole v jazyce C++ a C# jsou ve skutečnosti pole polí a lze je proto považovat za pouze jednorozměrné pole (a `GetRank` Metoda vždy vrátí hodnotu 1). V na [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] druhé straně multidimenzionální pole jsou zpracovávány jinak a pořadí takového pole odráží počet dimenzí (a `GetRank` Metoda vždy vrací počet dimenzí).

## <a name="see-also"></a>Viz také
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
