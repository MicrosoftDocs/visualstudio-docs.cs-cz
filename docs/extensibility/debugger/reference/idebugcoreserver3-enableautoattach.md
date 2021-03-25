---
description: Povolí automatické připojení pro zadané moduly ladění.
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e3b78744d67183c368345af8c6c26e57edec8d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105058674"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Povolí automatické připojení pro zadané moduly ladění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametry
`rgguidSpecificEngines`\
pro Pole identifikátorů GUID pro každý ladicí stroj, který se má označit jako automatické připojení.

`celtSpecificEngines`\
pro Počet modulů určených v `rgguidSpecificEngines` .

`pszStartPageUrl`\
pro Počáteční adresa URL, která se má použít při automatickém připojení

`pbstrSessionID`\
mimo ID relace, která byla automaticky připojena.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. Jeden kód chyby je `E_AUTO_ATTACH_NOT_REGISTERED` , což indikuje, že objekt pro vytváření tříd automatického připojení není zaregistrován.

## <a name="remarks"></a>Poznámky
 Když se spustí program přidružený k zadané adrese URL, automaticky se spustí a připojí zadané moduly ladění.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
