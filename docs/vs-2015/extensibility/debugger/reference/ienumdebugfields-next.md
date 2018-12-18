---
title: IEnumDebugFields::Next | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 737cb311f87a8012da03bc2b0dfbb65a0d172047
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797881"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda vrátí další sadu elementů z výčtu.  
  
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
 [in] Počet prvků, které mají načíst. Také určuje maximální velikost `rgelt` pole.  
  
 `rgelt`  
 [out v] Pole [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) prvků, které mají být vyplněna.  
  
 `pceltFetched`  
 [out] Vrátí počet prvků ve skutečnosti vrácených v `rgelt`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. Vrátí `S_FALSE` pokud menší než požadovaný počet prvků, které může být vrácena; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

