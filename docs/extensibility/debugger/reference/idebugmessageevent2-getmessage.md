---
title: IDebugMessageEvent2::GetMessage | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 819b796a656f0ef8775fbb1c9e800e3019b81729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727399"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Získá zprávu, která má být zobrazena.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parametry
`pMessageType`\
[out] Vrátí hodnotu z výčtu [MESSAGETYPE,](../../../extensibility/debugger/reference/messagetype.md) který popisuje typ zprávy.

`pbstrMessage`\
[out] Vrátí zprávu.

`pdwType`\
[out] Vrátí typ zprávy pomocí konvencí funkce Win32. `MessageBox` Podrobnosti najdete ve funkci [AfxMessageBox.](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)

`pbstrHelpFileName`\
[dovnitř, ven] Vrátí název souboru nápovědy. Může být hodnota null (C++) nebo prázdná (C#), pokud neexistuje žádný soubor nápovědy.

`pdwHelpId`\
[dovnitř, ven] Vrátí identifikátor nápovědy. Může být 0, pokud není k této zprávě přidružena žádná nápověda.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)
