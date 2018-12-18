---
title: IDebugDefaultPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6d131ab24cc57af1846f89b61afa2d89ae2cacb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106900"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Toto rozhraní poskytuje několik metod pro přístup k serveru na port a zařízení oznámení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Visual Studio implementuje toto rozhraní představují ladění port pro přístup k programy. Vlastní port dodavatele můžete taky implementovat toto rozhraní, pokud ho zpracuje vzdálené ladění.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Argumentu metody [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) rozhraní poskytuje toto rozhraní. Volání metody [QueryInterface](/cpp/atl/queryinterface) na [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) rozhraní můžete získat i toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Kromě metody definované v [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), toto rozhraní implementuje následujících metod:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Získá rozhraní portu oznámení z tohoto portu.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Získá rozhraní na serveru, který hostuje tento port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Určuje, zda tento port je spuštěn v místním počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Název "`IDebugDefaultPort2`" je bit misnomer, protože nepředstavuje výchozí port. Může být volána "IDebugPort3."  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)