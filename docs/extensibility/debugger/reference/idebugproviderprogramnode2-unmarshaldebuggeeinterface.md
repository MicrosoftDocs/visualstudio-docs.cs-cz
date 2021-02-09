---
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1449141885a51b3557f8c626b309fcc64c7fb268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909844"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Získá zadané rozhraní napříč hranicemi procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>Parametry
`riid`\
pro Identifikátor GUID rozhraní, které se má získat

`ppvObject`\
mimo Vrátí objekt implementující požadované rozhraní. [C++] Tato možnost může být převedena přímo na požadovaný typ rozhraní. [C#] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> k získání požadovaného rozhraní použijte metodu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se používá v případě, že ladicí stroj běží v [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] prostoru procesu a program, který se právě ladí, běží ve vlastním prostoru procesu.

## <a name="see-also"></a>Viz také
- [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
