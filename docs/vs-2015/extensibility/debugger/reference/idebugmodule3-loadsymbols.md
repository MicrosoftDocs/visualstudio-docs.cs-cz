---
title: 'IDebugModule3:: LoadSymbols | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 46385a61c5cc8cc30f75fd06a55bbe155e045f0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157277"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte symboly pro aktuální modul.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT LoadSymbols(  
   void  
);  
```  
  
```csharp  
int LoadSymbols();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je metoda úspěšná, vrátí `S_OK` . Pokud dojde k chybě, vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte symboly z aktuální cesty pro hledání (které lze změnit voláním metody [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).  
  
 Tato metoda je upřednostňována nad metodou [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
