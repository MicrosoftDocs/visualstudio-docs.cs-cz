---
title: IDebugProcess2::EnumThreads | Dokumentace Microsoftu
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
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69d4606b03504751a98b6fc0274defed4af99870
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747330"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Načte seznam všech vláken spuštěných v rámci procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Vrátí [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) objekt, který obsahuje seznam všech vláken ve všech aplikacích v procesu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří výčet vlákna spuštěná v každém programu a kombinuje je do procesu zobrazení vlákna. Jedno vlákno může běžet ve více programech; Tato metoda vytvoří výčet bylo vlákno pouze jednou.  
  
 Tato metoda představuje seznam vláken procesu bez duplicitní položky. V opačném případě se vytvořit výčet vlákna spuštěná v konkrétní aplikaci, použijte [enumthreads –](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)

