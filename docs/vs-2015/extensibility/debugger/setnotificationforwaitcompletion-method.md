---
title: Metoda SetNotificationForWaitCompletion | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874e31c331f16e760e030f337dda715473b77af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423397"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion – metoda
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví nebo vymaže bit stavu TASK_STATE_WAIT_COMPLETION_NOTIFICATION.  
  
 **Obor názvů:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Sestavení:** mscorlib (v mscorlib.dll)  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
internal void SetNotificationForWaitCompletion(bool enabled)  
```  
  
#### <a name="parameters"></a>Parametry  
 `enabled`  
  
 `true` nastavení bitu; `false` Chcete-li zrušit nastavení bitu.  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program nastaví tento bit tak, aby pomohly krokovat tělo asynchronní metody. Pokud `enabled` má hodnotu `true` , tato metoda musí být volána pouze pro úkol, který ještě nebyl dokončen. `enabled` `false` V takovém případě může být tato metoda volána u dokončených úloh. V obou případech by se měla použít jenom pro úlohy ve stylu Promise.  
  
## <a name="requirements"></a>Požadavky  
  
## <a name="see-also"></a>Viz také  
 [Task – třída](../../extensibility/debugger/task-class-internal-members.md)
