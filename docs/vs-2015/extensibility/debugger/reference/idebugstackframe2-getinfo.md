---
title: 'IDebugStackFrame2:: GetInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetInfo
helpviewer_keywords:
- IDebugStackFrame2::GetInfo
ms.assetid: 19c6870b-b94e-453c-bf19-82ce95b79d26
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6ebfda26b58bb1e7048b969133fa1672edad8a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164782"
---
# <a name="idebugstackframe2getinfo"></a>IDebugStackFrame2::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá popis rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetInfo (   
   FRAMEINFO_FLAGS dwFieldSpec,  
   UINT            nRadix,  
   FRAMEINFO*      pFrameInfo  
);  
```  
  
```csharp  
int GetInfo (   
   enum_FRAMEINFO_FLAGS dwFieldSpec,  
   uint                 nRadix,  
   FRAMEINFO[]          pFrameInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 pro Kombinace příznaků z výčtu [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) , která určuje, která pole `pFrameInfo` parametru mají být vyplněna.  
  
 `nRadix`  
 pro Číselná soustava, která se má použít při formátování číselných informací  
  
 `pFrameInfo`  
 mimo Struktura [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) , která je vyplněna popisem rámce zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
