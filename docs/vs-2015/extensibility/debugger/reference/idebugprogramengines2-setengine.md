---
title: IDebugProgramEngines2::SetEngine | Dokumentace Microsoftu
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
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd2d758ae58483757c808a78a3822e7acb87dfbc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759417"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Říká program nebo program uzel které ladicího stroje (DE) použít pro ladění tohoto programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetEngine(   
   REFGUID guidEngine  
);  
```  
  
```csharp  
int SetEngine(   
   ref Guid guidEngine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidEngine`  
 [in] Identifikátor GUID je DE.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)

