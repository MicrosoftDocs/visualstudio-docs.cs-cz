---
title: 'IDebugProcessSecurity:: QueryCanSafelyAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187962"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda umožňuje dodavateli portů zobrazit upozornění předtím, než se uživatel připojí k nebezpečnému procesu.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Návratové hodnoty jsou následující:  
  
- `S_OK`: Připojení k procesu je bezpečné a nezobrazuje se dialogové okno s upozorněním.  
  
- `S_FALSE`: Připojení může být problém zabezpečení a zobrazí se dialogové okno s upozorněním.  
  
- `FAILURE`: Připojení k procesu selhalo.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
