---
title: IDebugArrayObject::GetDimensions | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a931b488f2827e59a6b9b9ecaf86bf938ddc72a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896429"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Získá rozměry pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCount`  
 [in] Počet dimenzí pro načtení.  
  
 `dwDimensions`  
 [out v] Pole, které se vyplní velikosti jednotlivých rozměrů. `dwCount` Určuje maximální velikost `dwDimensions` pole.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Vícerozměrné pole může mít různé velikosti pro jednotlivé rozměry. Mějme například trojrozměrného pole `myarray[3][2][6]`, vrátí tato metoda 3, 2 a 6 `dwDimensions` parametrů v tomto pořadí.  
  
## <a name="see-also"></a>Viz také  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)