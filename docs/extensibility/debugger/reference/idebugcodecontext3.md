---
title: IDebugCodeContext3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCodeContext3 interface
ms.assetid: 524eb882-0ad5-4bfb-95eb-eb3abb3d0237
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 451e61ab7d6f74c83898987cdbecad2a9e13b06c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108505"
---
# <a name="idebugcodecontext3"></a>IDebugCodeContext3
Rozšiřuje [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) rozhraní, abyste umožnili načtení modulu a proces rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCodeContext3 : IDebugCodeContext2  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Implementované moduly ladění a spotřebovávají [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ladění balíčku.  
  
## <a name="methods"></a>Metody  
 Kromě metod na `IDebugCodeContext2` rozhraní, toto rozhraní implementuje následujících metod:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getmodule –](../../../extensibility/debugger/reference/idebugcodecontext3-getmodule.md)|Získá odkaz na rozhraní modulu ladění.|  
|[Getprocess –](../../../extensibility/debugger/reference/idebugcodecontext3-getprocess.md)|Získá odkaz na rozhraní procesu ladění.|  
  
## <a name="remarks"></a>Poznámky  
 Toto je volitelné rozhraní, která obvykle nemá k implementaci.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll