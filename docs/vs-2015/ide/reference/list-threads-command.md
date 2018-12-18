---
title: Příkaz vlákna seznamu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7ffad16bc121582b4f8a8ec4c58ac44aa2449617
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49286660"
---
# <a name="list-threads-command"></a>Listovat vlákna – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zobrazí seznam vláken v aktuálním programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Volitelné. Vybere vlákno podle jejich indexu bude aktuální vlákno.  
  
## <a name="remarks"></a>Poznámky  
 -Li zadána, `index` argument označí vláknu označený jako aktuální vlákno. Hvězdička (*) se zobrazí v seznamu vedle aktuální vlákno.  
  
## <a name="example"></a>Příklad  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz listovat zásobník volání](../../ide/reference/list-call-stack-command.md)   
 [Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)   
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



