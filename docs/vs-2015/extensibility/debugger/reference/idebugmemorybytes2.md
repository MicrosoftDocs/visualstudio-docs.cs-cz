---
title: IDebugMemoryBytes2 | Dokumentace Microsoftu
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
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddbe101efe069787bbbb2ad6462c87bc1151c0cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751959"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní představuje počet bajtů paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugMemoryBytes2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní k reprezentaci bajtů v paměti.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) vrátí toto rozhraní můžete poskytnout přístup k systémové paměti. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) a [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) vrátit toto rozhraní pro poskytnutí přístupu k objektu bajtů.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu `IDebugMemoryBytes2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Načte posloupnost bajtů, spouští se v daném umístění.|  
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Zapíše `dwCount` bajtů počínaje `pStartContext`.|  
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Získá velikost v bajtech paměti reprezentovaný tímto rozhraním.|  
  
## <a name="remarks"></a>Poznámky  
 Pro vlastnosti [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) poskytuje rozhraní představující pole `IDebugMemoryBytes2` rozhraní pro přístup k hodnoty v tomto poli.  
  
 Visual Studio **zobrazení paměti** volání [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) k načtení `IDebugMemoryBytes2` rozhraní pro přístup k systémové paměti. Získat adresu přístup k analýze výrazu zadat jako adresu do zobrazení paměti a vyhodnotíte analyzovaný výraz pomocí [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zobrazíte `IDebugProperty2` rozhraní. Volání [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) vrátí [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) adresa paměti, který popisuje. Tento kontext paměti je pak předán [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) a [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)   
 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

