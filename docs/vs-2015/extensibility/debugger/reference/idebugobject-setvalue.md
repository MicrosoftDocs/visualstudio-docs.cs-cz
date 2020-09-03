---
title: 'IDebugObject:: SetValue | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d898852c6bcca42cb0df1e7fab1597df74427a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203261"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Nastaví hodnotu objektu z po sobě jdoucí řady bajtů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pValue`  
 pro Pole bajtů představující novou hodnotu.  
  
 `nSize`  
 pro Velikost hodnoty v bajtech  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty v poli jsou zkopírovány do tohoto objektu [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) a nahradí všechny existující hodnoty. Velikost nové hodnoty může být větší nebo menší než stávající hodnota. `IDebugObject`Nemůže se jednat o odkaz s hodnotou null.  
  
## <a name="see-also"></a>Viz také  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
