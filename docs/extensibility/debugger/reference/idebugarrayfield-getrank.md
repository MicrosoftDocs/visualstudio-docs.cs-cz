---
title: IDebugArrayField::GetRank | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736306"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Získá pořadí nebo počet dimenzí pole.

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
[out] Vrátí pořadí.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pořadí pole odpovídá počtu dimenzí. V jazycích C++ a C# jsou vícerozměrná pole ve skutečnosti pole polí a proto `GetRank` mohou být považována pouze za jednorozměrné pole (a metoda vždy vrátí 1). V [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]aplikaci jsou naopak vícerozměrná pole zpracována odlišně a pořadí takového pole odráží počet `GetRank` rozměrů (a metoda vždy vrací počet dimenzí).

## <a name="see-also"></a>Viz také
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
