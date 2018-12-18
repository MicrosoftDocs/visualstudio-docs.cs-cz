---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a93877066e90bbc72ca58181d192219e898897d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833886"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
Tato metoda přidá program uzel pro každý ladicí stroj (DE) zadaná.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidLaunchingEngine`  
 [in] `GUID` Z DE, který se má použít ke spuštění aplikace (a se předpokládá, že můžete přidat vlastní program uzly).  
  
 `rgguidSpecificEngines`  
 [in] Pole `GUID`s DEs pro program, který se přidá uzly.  
  
 `celtSpecificEngines`  
 [in] Počet `GUID`ve `rgguidSpecificEngines` pole.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [Program uzly](../../../extensibility/debugger/program-nodes.md) přidá pro každý DE uvedený v `rgguidSpecificEngines`– s výjimkou spouštění modulu (jak je uvedeno v `guidLaunchingEngine`), který předpokládá, že je přidejte vlastní program uzlu při spuštění programu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Uzly programů](../../../extensibility/debugger/program-nodes.md)