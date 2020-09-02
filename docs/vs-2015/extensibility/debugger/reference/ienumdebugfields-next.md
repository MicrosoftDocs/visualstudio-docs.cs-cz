---
title: 'IEnumDebugFields:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a6cdf99bdfce0b53bf431bf456c276bb88b87e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199644"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda vrací další sadu prvků z výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet prvků, které mají být načteny. Určuje také maximální velikost `rgelt` pole.  
  
 `rgelt`  
 [in, out] Pole [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) prvků, které se mají vyplnit  
  
 `pceltFetched`  
 mimo Vrátí počet prvků, které jsou ve skutečnosti vráceny v `rgelt` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud je možné vrátit méně než požadovaný počet prvků. v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
