---
title: 'IDebugObject:: Equals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85252cdaf9fb076ebd4f8000115bcea576531bb1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159110"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Porovná objekt s tímto objektem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pObject`  
 pro Objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující objekt, na který se má porovnat.  
  
 `pfIsEqual`  
 mimo Vrátí nenulovou hodnotu ( `TRUE` ), pokud jsou hodnoty objektů stejné. v opačném případě vrátí hodnotu nula ( `FALSE` ).  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda obvykle může porovnat adresy hodnot reprezentovaných `pObject` parametrem a tímto objektem [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; Pokud jsou adresy stejné, lze objekty považovat za stejné.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
