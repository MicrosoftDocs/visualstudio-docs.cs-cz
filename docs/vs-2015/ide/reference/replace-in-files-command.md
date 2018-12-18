---
title: Příkaz Nahradit v souborech | Dokumentace Microsoftu
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
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eba6dfcf95c006fb05d4faaa0c370c9dba56e4e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197662"
---
# <a name="replace-in-files-command"></a>Nahradit v souborech – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Nahradí text v souborech pomocí některé podsady z možností, které jsou k dispozici na **nahradit v souborech** karty **najít a nahradit** okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>Arguments  
 `findwhat`  
 Požadováno. Text tak, aby odpovídaly.  
  
 `replacewith`  
 Požadováno. Text, který nahradí odpovídající text.  
  
## <a name="switches"></a>Přepínače  
 / all nebo /  
 Volitelné. Nahradí všechny výskyty hledaný text Nahrazovací text.  
  
 /Case nebo /c  
 Volitelné. Odpovídá dojde pouze v případě, že při velká a malá písmena přesně odpovídá platformám zadaným v `findwhat` argument.  
  
 /ext: `extensions`  
 Volitelné. Určuje rozšíření souboru pro soubory k prohledání.  
  
 /Keep nebo /k  
 Volitelné. Určuje, že všechny změněné soubory jsou ponechány otevřené.  
  
 /lookin: `searchpath`  
 Volitelné. Adresář pro hledání. Pokud cesta obsahuje mezery, uzavřete do uvozovek celou cestu.  
  
 / Options nebo /t  
 Volitelné. Zobrazí seznam aktuální nastavení možnosti hledání a nebude provádět vyhledávání.  
  
 /Regex nebo/r  
 Volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy, které představují vzorů textu spíše než literálními znaky. Úplný seznam znaky regulárního výrazu, naleznete v tématu [regulární výrazy](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset nebo /e  
 Volitelné. Vrátí možnosti hledání na jejich výchozí nastavení a nebude provádět vyhledávání.  
  
 / stop  
 Volitelné. Zastaví aktuální operace vyhledávání, pokud je v průběhu. Nahradit ignoruje všechny argumenty při `/stop` nebyl zadán. Třeba zastavit aktuální nahrazení zadáte následující:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 / Sub nebo /s  
 Volitelné. Vyhledá podsložky v adresáři uvedeném na /lookin:`searchpath` argument.  
  
 /Text2 nebo /2  
 Volitelné. Zobrazí výsledky v nahrazení **Najít výsledky 2** okna.  
  
 /Wild nebo/l  
 Volitelné. Používá předdefinované speciální znaky v `findwhat` argument jako zápisy představující znak nebo posloupnost znaků.  
  
 lze nebo /w  
 Volitelné. Vyhledá pouze celá slova.  
  
## <a name="example"></a>Příklad  
 Tento příklad vyhledá `btnCancel` a nahradí jej s `btnReset` ve všech .cls soubory umístěné ve složce "Moje projekty sady visual studio" a zobrazí informace o nahrazení v **Najít výsledky 2** okna.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>Viz také  
 [Hledání a nahrazení textu](../../ide/finding-and-replacing-text.md)   
 [Nahradit v souborech](../../ide/replace-in-files.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



