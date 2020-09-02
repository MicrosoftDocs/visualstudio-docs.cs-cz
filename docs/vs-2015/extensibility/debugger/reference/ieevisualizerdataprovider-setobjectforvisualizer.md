---
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540276"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tato metoda změní objekt, který Vizualizér představuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pNewObject`  
 pro Objekt, který chcete nastavit.  
  
 `error`  
 mimo Pokud při nastavování objektu došlo k chybě, tento řetězec obsahuje chybovou zprávu.  
  
 `pException`  
 mimo Pokud došlo k chybě, tento objekt obsahuje informace o výjimce.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Je až implementátor, který určí, jak se vrátí informace o chybě. Je však možné, že někteří volající mohou zjistit, zda došlo k chybě objektu výjimky, aby bylo známo, že došlo k chybě, takže tato metoda by měla vždy vracet objekt výjimky, pokud došlo k chybě. Řetězec chyby by měl být také dodán pro případ, že ho volající chce využít.  
  
## <a name="see-also"></a>Viz také  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
