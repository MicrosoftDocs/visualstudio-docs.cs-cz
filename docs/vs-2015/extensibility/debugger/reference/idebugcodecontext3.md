---
title: IDebugCodeContext3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62b84bd77038c7a17b65f764bd303d6a6372a52c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154160"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rozšiřuje rozhraní [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , aby bylo možné načíst rozhraní modulu a procesu.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Implementováno ladicími moduly a spotřebované [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ladicím balíčkem.  
  
## <a name="methods"></a>Metody  
 Kromě metod v `IDebugCodeContext2` rozhraní implementuje toto rozhraní následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetModule](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Načte odkaz na rozhraní modulu ladění.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Načte odkaz na rozhraní procesu ladění.|  
  
## <a name="remarks"></a>Poznámky  
 Toto je volitelné rozhraní, které obecně nemusí být implementováno.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
