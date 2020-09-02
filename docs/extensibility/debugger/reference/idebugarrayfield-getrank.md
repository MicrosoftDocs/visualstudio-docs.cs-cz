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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 692f2f13d861d9688ba349fbc80cb1ca426582c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736306"
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
