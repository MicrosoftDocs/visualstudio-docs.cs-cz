---
title: IDebugCoreServer3::EnableAutoAttach | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d529bb80f79a3f2972e9349a2679bb528cc10463
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732909"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Umožňuje automatické připojení pro zadané ladicí motory.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnableAutoAttach(
   GUID*     rgguidSpecificEngines,
   DWORD     celtSpecificEngines,
   LPCOLESTR pszStartPageUrl,
   BSTR*     pbstrSessionId
);
```

```csharp
int EnableAutoAttach(
   Guid[]     rgguidSpecificEngines,
   uint       celtSpecificEngines,
   string     pszStartPageUrl,
   out string pbstrSessionId
);
```

## <a name="parameters"></a>Parametry
`rgguidSpecificEngines`\
[v] Pole identifikátorů GUID pro každý ladicí modul označit jako automatické připojení.

`celtSpecificEngines`\
[v] Počet motorů uvedených `rgguidSpecificEngines`v písmenu a).

`pszStartPageUrl`\
[v] Počáteční adresa URL, která se má použít při automatickém připojování.

`pbstrSessionID`\
[out] ID relace, která byla automaticky připojena.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Jeden kód `E_AUTO_ATTACH_NOT_REGISTERED`chyby je , což znamená, že automatické připojení factory třídy nebyla zaregistrována.

## <a name="remarks"></a>Poznámky
 Při spuštění programu přidruženého k zadané adrese URL jsou zadané ladicí moduly automaticky spuštěny a připojeny.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
