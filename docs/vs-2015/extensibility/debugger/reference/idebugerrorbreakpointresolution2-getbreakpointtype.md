---
title: 'IDebugErrorBreakpointResolution2:: GetBreakpointType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugErrorBreakpointResolution2::GetBreakpointType
ms.assetid: 0bdb1152-4752-4464-ae7c-6d666dc293b7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5e4522bf344b8d94c7c449d10b9e8c3fbbb64ff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188877"
---
# <a name="idebugerrorbreakpointresolution2getbreakpointtype"></a>IDebugErrorBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získá typ zarážky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBPType`  
 mimo Vrací hodnotu z výčtu [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) , který popisuje typ zarážky.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrací typ zarážky, která selhala při vytváření vazby, takže vyžaduje událost zarážky chyby.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CDebugErrorBreakpointResolution` objekt, který zpřístupňuje rozhraní [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) .  
  
```  
HRESULT CDebugErrorBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPERESI_BPRESLOCATION flag is set in BPERESI_FIELDS.    
      if (IsFlagSet(m_bpErrorResolutionInfo.dwFields, BPERESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpErrorResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Viz také  
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
