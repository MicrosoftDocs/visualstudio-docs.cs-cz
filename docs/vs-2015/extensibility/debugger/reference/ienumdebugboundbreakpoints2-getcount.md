---
title: 'IEnumDebugBoundBreakpoints2:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::GetCount
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::GetCount
ms.assetid: 5a572eeb-beb7-4fc7-8259-792d277069be
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc4d9b6d343dfc5b3c4795bc82c07c1ec3b66ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551984"
---
# <a name="ienumdebugboundbreakpoints2getcount"></a>IEnumDebugBoundBreakpoints2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vrátí počet prvků ve výčtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 mimo Vrátí počet prvků ve výčtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda není součástí vlastního rozhraní výčtu modelu COM, které určuje, že `Next` `Clone` `Skip` `Reset` je nutné implementovat pouze metody,, a.  
  
## <a name="see-also"></a>Viz také  
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)
