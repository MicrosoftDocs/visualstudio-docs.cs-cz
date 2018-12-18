---
title: Setnotificationforwaitcompletion – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 42c5bca56bc46c0b8124fbfaf7ca046c2c1e59ec
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276335"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion – metoda
Nastaví nebo vymaže stav bit TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v *mscorlib.dll*)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
### <a name="parameters"></a>Parametry  
 `enabled`  
  
 `true` Chcete-li nastavit bit; `false` na Zrušit nastavení bitu.  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program nastaví tento bit ke kroku mimo tělo metody na asynchronní. Pokud `enabled` je `true`, tato metoda musí být volána pouze na úkol, který dosud nebyl dokončen. Když `enabled` je `false`, tuto metodu lze volat pro dokončené úlohy. V obou případech to by měla sloužit pouze pro příslib – vizuální styl úlohy.  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také:  
 [Třída úlohy](../../extensibility/debugger/task-class-internal-members.md)