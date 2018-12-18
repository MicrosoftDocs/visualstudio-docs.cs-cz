---
title: Přejděte na příkaz | Dokumentace Microsoftu
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
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d23f7b9961f8386fb023fa747a647c14c9cd5db1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49303469"
---
# <a name="go-to-command"></a>Přejít na – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Přesune kurzor na zadaný řádek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Arguments  
 `linenumber`  
 Volitelné. Celé číslo představující číslo řádku, přejděte na.  
  
## <a name="remarks"></a>Poznámky  
 Číslování řádků začíná u jedné. Pokud hodnota `linenumber` je menší než 1, první řádek zobrazí. Pokud hodnota `linenumber` je větší než počet poslední řádek zobrazí poslední řádek.  
  
 Pokud hodnotu `linenumber` není zadán, **přejít na řádek** zobrazí dialogové okno.  
  
 Alias pro tento příkaz je GoToLn.  
  
## <a name="example"></a>Příklad  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



