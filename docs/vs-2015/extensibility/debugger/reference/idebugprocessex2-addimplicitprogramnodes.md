---
title: 'IDebugProcessEx2:: AddImplicitProgramNodes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202823"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda přidá uzel programu pro každý zadaný ladicí stroj (DE).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 pro A `GUID` , který se má použít ke spuštění programů (a předpokládá se, že se mají přidat vlastní uzly programu).  
  
 `rgguidSpecificEngines`  
 pro Pole `GUID` s des, pro které budou přidány uzly programu.  
  
 `celtSpecificEngines`  
 pro Počet `GUID` s v poli `rgguidSpecificEngines` .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 [Uzly programu](../../../extensibility/debugger/program-nodes.md) budou přidány pro každý z níže uvedených v `rgguidSpecificEngines` – bez spouštěcího modulu (jak je uvedeno v části `guidLaunchingEngine` ), což předpokládá, že při spuštění programu dojde k přidání vlastního uzlu programu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Uzly programů](../../../extensibility/debugger/program-nodes.md)
