---
title: Zásobník volání – příkaz seznamu | Dokumentace Microsoftu
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
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 69c3708960f5b1ddaf0ff6620b8d90eb64cd86d8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194373"
---
# <a name="list-call-stack-command"></a>Listovat zásobník volání – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zobrazí aktuální zásobník volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]  
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]  
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]  
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]  
[/ShowExternalCode:yes|no] [Thread:n] [index]  
```  
  
## <a name="arguments"></a>Arguments  
 `index`  
 Volitelné. Nastaví aktuální rámec zásobníku a nezobrazí se žádný výstup.  
  
## <a name="switches"></a>Přepínače  
 Každý přepínač je možné vyvolat pomocí jeho dokončení formuláře nebo krátký tvar.  
  
 / Počet:`number` [nebo] sady`number`  
 Volitelné. Maximální počet zásobníky volání pro zobrazení. Výchozí hodnota neomezený.  
  
 / Showtypeszobrazittypy:`yes` &#124; `no` [nebo] t:`yes`&#124;`no`  
 Volitelné. Určuje, zda chcete-li zobrazit typy parametrů. Výchozí hodnota je `yes`.  
  
 / Shownameszobrazitnázvy:`yes` &#124; `no` [nebo] / n:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se mají zobrazovat názvy parametrů. Výchozí hodnota je `yes`.  
  
 / Showvalueszobrazithodnoty:`yes` &#124; `no` [nebo] / v:`yes`&#124;`no`  
 Volitelné. Určuje, zda chcete-li zobrazit hodnoty parametrů. Výchozí hodnota je `yes`.  
  
 / Showmodulezobrazitmoduly:`yes` &#124; `no` [nebo] / m:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se mají zobrazovat název modulu. Výchozí hodnota je `yes`.  
  
 / Showlineoffsetzobrazitodsazenířádku:`yes` &#124; `no` [nebo] které:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se mají zobrazovat posun řádku. Výchozí hodnota je `no`.  
  
 / Showbyteoffsetzobrazitodsazeníbajtu:`yes` &#124; `no` [nebo] / b:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se má zobrazit bajtovým posunem. Výchozí hodnota je `no`.  
  
 / Showlanguagezobrazitjazyk:`yes` &#124; `no` [nebo] l:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se má zobrazit jazyk. Výchozí hodnota je `no`.  
  
 / Includecallsacrossthreadszahrnoutvolánínapříčvlákny:`yes` &#124; `no` [nebo] / i:`yes`&#124;`no`  
 Volitelné. Určuje, jestli se mají zahrnout volání do nebo z jiných vláken. Výchozí hodnota je `no`.  
  
 / Showexternalcodezobrazitexterníkód:`yes`&#124;`no`  
 Volitelné. Určuje, zda má být zobrazen pouze můj kód pro zásobník volání. Když funkce pouze můj kód je vypnuté, zobrazí se všechny neuživatelský kód. Po zapnutí funkce pouze můj kód neuživatelském kódu se zobrazí jako `[external]` ve výstupu zásobník volání.  
  
 Vlákna:`n`  
 Volitelné. Zobrazí zásobník volání pro vlákno `n`. Pokud není zadána žádná vlákna, zobrazuje zásobník volání pro aktuální vlákno.  
  
## <a name="remarks"></a>Poznámky  
 Změny provedené argumenty nebo přepínače platí pro budoucí volání tohoto příkazu. Pokud vydáte Debug.ListCallStackby samotného, zobrazí se celý zásobník volání. Pokud například zadáte indexu,  
  
```  
Debug.ListCallStack 2  
```  
  
 aktuální rámec zásobníku je nastaven na tomto snímku (v tomto případě druhý snímek).  
  
 Tento příkaz pomocí jeho předem definovaný alias, můžete je zapsat také kb. Například můžete zadat  
  
```  
kb 2  
```  
  
 nastavit aktuální rámec zásobníku na druhý snímek.  
  
## <a name="example"></a>Příklad  
  
```  
>Debug.CallStack /Count:4 /ShowTypes:yes  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)   
 [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)   
 [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Okno příkazového řádku](../../ide/reference/command-window.md)   
 [Pole najít/příkaz](../../ide/find-command-box.md)   
 [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



