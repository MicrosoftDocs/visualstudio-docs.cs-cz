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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3c0f6e66b6585eafde656cd7be88d0c76bbb3f37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720701"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
Získá zadané rozhraní napříč hranicemi procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnmarshalDebuggeeInterface(
   REFIID riid,
   void** ppvObject
);
```

```csharp
int UnmarshalDebuggeeInterface(
   ref Guid   riid,
   out IntPtr ppvObject
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
