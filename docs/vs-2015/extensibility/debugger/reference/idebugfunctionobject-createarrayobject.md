---
title: 'IDebugFunctionObject:: CreateArrayObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205809"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří objekt Array. Toto pole může obsahovat hodnoty primitivního nebo instančního objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ot`  
 pro Určuje hodnotu z výčtu [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) , která označuje typ nového objektu Array.  
  
 `pClassField`  
 pro Objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující třídu objektu, pokud se vytváří pole hodnot instance objektu. Pokud vytváříte pole primitivních objektů, tento parametr je hodnota null.  
  
 `dwRank`  
 pro Rozměr nebo počet rozměrů pole.  
  
 `dwDims`  
 pro Velikosti jednotlivých rozměrů pole.  
  
 `dwLowBounds`  
 pro Původ každé dimenze (obvykle 0 nebo 1).  
  
 `ppObject`  
 mimo Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující nově vytvořené pole. Toto je vlastně objekt [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Zavolejte tuto metodu pro vytvoření objektu, který představuje parametr pole pro funkci, která je reprezentovaná [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) rozhraním.  
  
## <a name="see-also"></a>Viz také  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
