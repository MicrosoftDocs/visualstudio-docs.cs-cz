---
title: IDebugCustomAttributeQuery2 | Dokumentace Microsoftu
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
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b175a15520b9956ecd2a1418f35f1aa9bdbc1330
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739063"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje existenci vlastní atribut pro toto pole a pokud existuje, vrátí informace o atributu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Poskytovatel symbolů implementuje toto rozhraní na stejný objekt, který implementuje [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) za účelem podpory vlastních atributů.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Použití [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) získat z tohoto rozhraní [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 V následující tabulce jsou uvedeny metody objektu **IDebugCustomAttributeQuery** rozhraní.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Určuje, zda existuje vlastní atribut podle názvu.|  
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Získá informace o atributu pro dané vlastní atribut.|  
  
 Kromě **IDebugCustomAttributeQuery** metody, `IDebugCustomAttributeQuery2` implementuje následující metodu:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Získá enumerátor pro všechny vlastní atributy připojené k tomuto poli.|  
  
## <a name="remarks"></a>Poznámky  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) metoda může vrátit enumerátor pro všechny vlastní atributy definované pro toto pole.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)

