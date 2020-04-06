---
title: IDebugErrorEvent2::GetErrorMessage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1ff1da2f2a2d24b958a613e6fe5cb58c0081ed3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730042"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Vrátí informace, které umožňuje konstrukci chybové zprávy čitelné pro člověka.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parametry
`pMessageType`\
[out] Vrátí hodnotu z výčtu [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) popisující typ zprávy.

`pbstrErrorFormat`\
[out] Formát závěrečné zprávy pro uživatele (viz "Poznámky" pro podrobnosti).

`hrErrorReason`\
[out] Kód chyby, o které se zpráva nachází.

`pdwType`\
[out] Závažnost chyby (použijte MB_XXX konstanty `MessageBox`; `MB_EXCLAMATION` například `MB_WARNING`nebo ).

`pbstrHelpFileName`\
[out] Cesta k souboru nápovědy (nastavena na hodnotu null, pokud neexistuje žádný soubor nápovědy).

`pdwHelpId`\
[out] ID tématu nápovědy, které se má zobrazit (nastaveno na 0, pokud není k dispozici žádné téma nápovědy).

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chybová zpráva by měla být `"What I was doing.  %1"`formátována podle písmene . By `"%1"` pak nahrazen volajícího s chybovou zprávou odvozenou z kódu `hrErrorReason`chyby (který je vrácen v ). Parametr `pMessageType` informuje volajícího, jak by měla být zobrazena poslední chybová zpráva.

## <a name="see-also"></a>Viz také
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
