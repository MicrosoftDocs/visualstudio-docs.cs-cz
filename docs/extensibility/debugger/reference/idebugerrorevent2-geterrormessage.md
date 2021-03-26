---
description: Vrátí informace, které umožňují konstrukci chybové zprávy čitelné člověkem.
title: 'IDebugErrorEvent2:: GetErrorMessage | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a0ab15c0f232695dbc017d80f666154e5c35a8fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065772"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Vrátí informace, které umožňují konstrukci chybové zprávy čitelné člověkem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetErrorMessage(
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrErrorFormat,
   HRESULT*     hrErrorReason,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetErrorMessage(
   out enum_MESSAGETYPE   pMessageType,
   out string             pbstrErrorFormat,
   out int                phrErrorReason,
   out uint               pdwType,
   out string             pbstrHelpFileName,
   out uint               pdwHelpId
);
```

## <a name="parameters"></a>Parametry
`pMessageType`\
mimo Vrací hodnotu z výčtu [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) , která popisuje typ zprávy.

`pbstrErrorFormat`\
mimo Formát konečné zprávy pro uživatele (podrobnosti naleznete v části "poznámky").

`hrErrorReason`\
mimo Kód chyby, o které se zpráva týká

`pdwType`\
mimo Závažnost chyby (použijte konstanty MB_XXX pro `MessageBox` , například `MB_EXCLAMATION` nebo `MB_WARNING` ).

`pbstrHelpFileName`\
mimo Cesta k souboru s příponou (nastaveno na hodnotu null, pokud není k dispozici žádný soubor v nápovědě).

`pdwHelpId`\
mimo ID tématu nápovědy, které se má zobrazit (Pokud není k dispozici téma nápovědy), je nastaveno na hodnotu 0.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chybová zpráva by měla být naformátována podél řádků `"What I was doing.  %1"` . `"%1"`By měl být nahrazen volajícím s chybovou zprávou odvozenou z kódu chyby (který je vrácen v rámci `hrErrorReason` ). `pMessageType`Parametr oznamuje volajícímu, jak by se měla zobrazit Závěrečná chybová zpráva.

## <a name="see-also"></a>Viz také
- [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
