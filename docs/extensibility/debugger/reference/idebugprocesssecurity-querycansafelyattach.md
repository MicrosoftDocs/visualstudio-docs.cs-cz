---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fe132ddbd154e04e3cef1a20e826c3634c65bdb2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114226"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Tato metoda umožňuje dodavatele port předtím, než uživatel připojí k unsafe proces zobrazila upozornění.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty jsou následující:  
  
-   `S_OK`: Připojení k procesu je bezpečné a zobrazí se dialogové okno bez upozornění.  
  
-   `S_FALSE`: Připojení může být problém se zabezpečením a zobrazí se dialogové okno s upozorněním.  
  
-   `FAILURE`: Připojení k proces se nezdaří.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)