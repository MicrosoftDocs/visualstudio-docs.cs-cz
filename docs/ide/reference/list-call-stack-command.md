---
title: Listovat zásobník volání – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e809af75f0a4a47da6af30a3d93748401ca4609d
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512002"
---
# <a name="list-call-stack-command"></a>Listovat zásobník volání – příkaz
Zobrazí aktuální zásobník volání.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Arguments
 `index` Volitelné. Nastaví aktuální rámec zásobníku a nezobrazí se žádný výstup.

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

 Volitelné. Zobrazí zásobník volání pro vlákno `n`. Pokud není zadána žádná vlákna, zobrazí se zásobník volání pro aktuální vlákno.

## <a name="remarks"></a>Poznámky
 Změny provedené argumenty nebo přepínače platí pro budoucí volání tohoto příkazu. Pokud vydáte Debug.ListCallStackby samotného, zobrazí se celý zásobník volání. Pokud například zadáte indexu,

```cmd
Debug.ListCallStack 2
```

 aktuální rámec zásobníku je nastaven na tomto snímku (v tomto případě druhý snímek).

 Tento příkaz pomocí jeho předem definovaný alias, můžete je zapsat také kb. Například můžete zadat

```cmd
kb 2
```

 nastavit aktuální rámec zásobníku na druhý snímek.

## <a name="example"></a>Příklad

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Viz také

- [Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)
- [Příkaz Listovat vlákna](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)