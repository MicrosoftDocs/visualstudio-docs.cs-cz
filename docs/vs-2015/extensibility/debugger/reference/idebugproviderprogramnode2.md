---
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a81668d5c45dd4b3363821972914e3f9dc10266a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692218"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní zařazování rozhraní souvisejících s programy napříč hranicemi procesů.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProviderProgramNode2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Ladicí stroj (DE) implementuje toto rozhraní na stejném objektu, který implementuje [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pro podporu zařazování rozhraní napříč hranicemi procesů.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) `IDebugProgramNode2` Chcete-li získat toto rozhraní, zavolejte na rozhraní QueryInterface. Pokud toto rozhraní nelze získat, DE nepodporuje zařazování rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Toto rozhraní implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Získá zadané rozhraní napříč hranicemi procesu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je implementováno, když je DE spuštěna v odděleném prostoru procesu z laděného programu: například při spuštění DE v prostoru procesu sady Visual Studio namísto procesu ladění programu.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
