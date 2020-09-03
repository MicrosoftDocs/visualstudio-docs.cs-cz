---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f10dc6e9e00e2b7f66722f3c89b74bb14e45fdbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180578"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Přečte sekvenci bajtů počínaje daným umístěním.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 pro Objekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , který určuje, kde začít číst bajty.  
  
 `dwCount`  
 pro Počet bajtů, které mají být čteny. Určuje také délku `rgbMemory` pole.  
  
 `rgbMemory`  
 [in, out] Pole vyplněné bajty se skutečně čte.  
  
 `pdwRead`  
 mimo Vrátí počet souvislých bajtů, které jsou ve skutečnosti čteny.  
  
 `pdwUnreadable`  
 [in, out] Vrátí počet nečitelných bajtů. Může být hodnota null, pokud se klientovi nepodílí na počtu nečitelných bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud jsou požadovány 100 bajtů a první 50 je čitelný, další 20 je nečitelný a zbývající 30 je čitelný, tato metoda vrátí:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 V tomto případě `*pdwRead + *pdwUnreadable < dwCount` volající musí provést další volání ke čtení zbývajících 30 bajtů původní 100 a objekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) předaný `pStartContext` parametru musí být rozšířen o 70.  
  
## <a name="see-also"></a>Viz také  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
