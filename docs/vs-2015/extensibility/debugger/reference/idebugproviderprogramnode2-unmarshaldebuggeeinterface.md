---
title: 'IDebugProviderProgramNode2:: UnmarshalDebuggeeInterface | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3007d13ec3eae46511e4775497d0aad5b6325b2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146254"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 pro Identifikátor GUID rozhraní, které se má získat  
  
 `ppvObject`  
 mimo Vrátí objekt implementující požadované rozhraní. [C++] Tato možnost může být převedena přímo na požadovaný typ rozhraní. [C#] <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> k získání požadovaného rozhraní použijte metodu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se používá v případě, že ladicí stroj běží v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] prostoru procesu a program, který se právě ladí, běží ve vlastním prostoru procesu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)
