---
title: Otevřít projekt – příkaz | Dokumentace Microsoftu
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
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b25ee0e6ba4dfa5c29d5a009087afb55509d0c08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263912"
---
# <a name="open-project-command"></a>Otevřít projekt – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Otevře existující projekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Požadováno. Úplnou cestu a název souboru název projektu a otevřete.  
  
 Syntaxe `filename` argument vyžaduje, aby cesty obsahující mezery, použijte uvozovky.  
  
## <a name="remarks"></a>Poznámky  
 Automatické dokončování, pokusí se najít správnou cestu a název souboru během psaní.  
  
 Tento příkaz není k dispozici při ladění.  
  
## <a name="example"></a>Příklad  
 Tento příklad otevře [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



