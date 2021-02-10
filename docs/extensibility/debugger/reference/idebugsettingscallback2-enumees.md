---
title: 'IDebugSettingsCallback2:: EnumEEs | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::EnumEEs
ms.assetid: 9f884c49-426f-461b-b547-9d909486e73f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af31c78058ffa0816a566a090288cb1e31c17b70
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963026"
---
# <a name="idebugsettingscallback2enumees"></a>IDebugSettingsCallback2::EnumEEs
Vytvoří výčet dostupných vyhodnocení výrazů pro daný jazyk a identifikátory dodavatelů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumEEs(
   DWORD  celtBuffer,
   GUID*  rgguidLang,
   GUID*  rgguidVendor,
   DWORD* pceltEEs
);
```

```csharp
public int EnumEEs(
   uint       celtBuffer,
   ref Guid   rgguidLang,
   ref Guid   rgguidVendor,
   ref uint[] pceltEEs
);
```

## <a name="parameters"></a>Parametry
`celtBuffer`\
pro Počet prvků ve `pceltEEs` vyrovnávací paměti.

`rgguidLang`\
[in, out] Jedinečný identifikátor programovacího jazyka.

`rgguidVendor`\
[in, out] Jedinečný identifikátor pro dodavatele.

`pceltEEs`\
[in, out] Pole vyhodnocovacích hodnotitelů výrazů.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
