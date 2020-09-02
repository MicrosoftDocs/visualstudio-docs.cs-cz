---
title: MODULE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO
helpviewer_keywords:
- MODULE_INFO structure
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59ab4d0bb2a7aaa4b08f616ea0a99be85b521bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80714317"
---
# <a name="module_info"></a>MODULE_INFO
Popisuje konkrétní modul (DLL, EXE nebo Assembly).

## <a name="syntax"></a>Syntax

```cpp
typedef struct tagMODULE_INFO { 
   MODULE_INFO_FIELDS dwValidFields;
   BSTR               m_bstrName;
   BSTR               m_bstrUrl;
   BSTR               m_bstrVersion;
   BSTR               m_bstrDebugMessage;
   UINT64             m_addrLoadAddress;
   UINT64             m_addrPreferredLoadAddress;
   DWORD              m_dwSize;
   DWORD              m_dwLoadOrder;
   FILETIME           m_TimeStamp;
   BSTR               m_bstrUrlSymbolLocation;
   MODULE_FLAGS       m_dwModuleFlags;
} MODULE_INFO;
```

```csharp
public struct MODULE_INFO { 
   public uint     dwValidFields;
   public string   m_bstrName;
   public string   m_bstrUrl;
   public string   m_bstrVersion;
   public string   m_bstrDebugMessage;
   public ulong    m_addrLoadAddress;
   public ulong    m_addrPreferredLoadAddress;
   public uint     m_dwSize;
   public uint     m_dwLoadOrder;
   public FILETIME m_TimeStamp;
   public string   m_bstrUrlSymbolLocation;
   public uint     m_dwModuleFlags;
};
```

## <a name="members"></a>Členové
 `dwValidFields`\
 Kombinace příznaků z výčtu [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) , která určuje, která pole jsou vyplněna.

 `m_bstrName`\
 Název modulu.

 `m_bstrUrl`\
 Adresa URL modulu

 `m_bstrVersion`\
 Verze modulu

 `m_bstrDebugMessage`\
 Volitelná zpráva o modulu, například "symboly nelze načíst".

 `m_addrLoadAddress`\
 Adresa načtení modulu.

 `m_addrPreferredLoadAddress`\
 Upřednostňovaná adresa načtení modulu.

 `m_dwSize`\
 Velikost modulu.

 `m_dwLoadOrder`\
 Pořadí načtení modulu.

 `m_TimeStamp`\
 Čas poslední změny souboru symbolů

 `m_bstrUrlSymbolLocation`\
 Umístění souboru symbolů (například ". \\ ") uvedeného v modulu. Slouží jako počáteční umístění pro hledání symbolů pro modul.

 `m_dwModuleFlags`\
 Kombinace příznaků z výčtu [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) popisující modul.

## <a name="remarks"></a>Poznámky
 Tato struktura je předána metodě [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) , kde je vyplněna.

 Tato struktura odpovídá každému modulu uvedenému v okně **moduly** .

## <a name="requirements"></a>Požadavky
 Záhlaví: msdbg. h

 Obor názvů: Microsoft. VisualStudio. Debugger. Interop

 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také
- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
