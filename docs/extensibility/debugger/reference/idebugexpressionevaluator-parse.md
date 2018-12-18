---
title: IDebugExpressionEvaluator::Parse | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e348666514ea13a901a4c0be0a680ed4f83f688
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815121"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Tato metoda převede řetězec s výrazem na analyzovaný výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `upstrExpression`  
 [in] Řetězec výrazu, který má být analyzován.  
  
 `dwFlags`  
 [in] Kolekce [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) konstanty, které určují, jak má být analyzován výraz.  
  
 `nRadix`  
 [in] Základ, který se má použít pro interpretaci jakékoli číselné informace.  
  
 `pbstrError`  
 [out] Vrátí chybu jako čitelný text.  
  
 `pichError`  
 [out] Vrátí pozici znaku start Chyba v řetězci výraz.  
  
 `ppParsedExpression`  
 [out] Vrátí analyzovaný výrazu v [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`; v opačném případě vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vytváří analyzovaný výrazu, nikoli skutečnou hodnotu. Analyzovaná výrazu je připraven k vyhodnocení, to znamená, převést na hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)