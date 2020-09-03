---
title: 'IDebugFunctionObject:: Evaluate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e19baa193bb015056b9e5abde4c7a274f635c0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179427"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Volá funkci a vrátí výslednou hodnotu jako objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Evaluate(   
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate(  
   IDebugObject[]   ppParams,   
   IntPtr           dwParams,   
   uint             dwTimeout,   
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppParams`  
 pro Pole objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představujících vstupní parametry. Každý z těchto parametrů byl vytvořen pomocí jedné z `Create` metod v rozhraní [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
 `dwParams`  
 pro Počet parametrů v `ppParams` poli.  
  
 `dwTimeout`  
 pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.  
  
 `ppResult`  
 mimo Vrátí [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující hodnotu funkce jako objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda nastaví a spustí volání funkce reprezentované objektem [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
