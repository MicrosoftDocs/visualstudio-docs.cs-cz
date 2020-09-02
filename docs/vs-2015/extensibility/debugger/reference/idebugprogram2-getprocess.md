---
title: 'IDebugProgram2:: getprocess | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148658"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Získejte proces, ve kterém je tento program spuštěn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppProcess`  
 mimo Vrátí rozhraní [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , které představuje proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Pokud modul ladění (DE) neimplementuje rozhraní [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , implementace de této metody by měla vždycky vracet, `E_NOTIMPL` protože de nemůže určit, který proces je spuštěný, a proto nemůže splnit implementaci této metody.  
  
 Implementace `IDebugEngineLaunch2` rozhraní znamená, že de musí znát, jak vytvořit proces; proto implementace rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) je schopna zjistit, v jakém procesu běží.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
