---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4fcccffecaf465af36d5e4925d43214ff132756f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147515"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Určuje, jaké akce se mají provést při zachytávání výjimek.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
typedef DWORD INTERCEPT_EXCEPTION_ACTION;  
```  
  
```csharp  
public enum enum_INTERCEPT_EXCEPTION_ACTION  
{  
   IEA_INTERCEPT = 0x0001  
}  
```  
  
#### <a name="parameters"></a>Parametry  
 IEA_INTERCEPT  
 Povoluje zachycení aktuální výjimky. Toto je jediná hodnota podporovaná v současnosti a musí se zadat.  
  
## <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou předány do metody [InterceptCurrentException –](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Výčty](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
