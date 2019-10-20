---
title: Výpis zásobníku volání příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657650"
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
 `index` volitelné. Nastaví aktuální rámec zásobníku a nezobrazí žádný výstup.

## <a name="switches"></a>Přepínače
 Každý přepínač lze vyvolat buď pomocí jeho úplného formátu, nebo krátkého tvaru.

 /Count: `number` [nebo]/C: `number` volitelné. Maximální počet zásobníků volání, které se mají zobrazit Výchozí hodnota je neomezená.

 /ShowTypes: `yes`&#124; `no` [nebo]/t: `yes`&#124; `no` volitelné. Určuje, zda se mají zobrazit typy parametrů. Výchozí hodnota je `yes`.

 /ShowNames: `yes`&#124; `no` [nebo]/n: `yes`&#124; `no` volitelné. Určuje, zda se mají zobrazovat názvy parametrů. Výchozí hodnota je `yes`.

 /ShowValues: `yes`&#124; `no` [nebo]/v: `yes`&#124; `no` volitelné. Určuje, zda se mají zobrazovat hodnoty parametrů. Výchozí hodnota je `yes`.

 /ShowModule: `yes`&#124; `no` [nebo]/m: `yes`&#124; `no` volitelné. Určuje, zda se má zobrazit název modulu. Výchozí hodnota je `yes`.

 /ShowLineOffset: `yes`&#124; `no` [nebo]/#: `yes`&#124; `no` volitelné. Určuje, zda se má zobrazit posun řádku. Výchozí hodnota je `no`.

 /ShowByteOffset: `yes`&#124; `no` [nebo]/b: `yes`&#124; `no` volitelné. Určuje, zda se má zobrazovat posun bajtů. Výchozí hodnota je `no`.

 /ShowLanguage: `yes`&#124; `no` [nebo]/l: `yes`&#124; `no` volitelné. Určuje, zda se má jazyk zobrazit. Výchozí hodnota je `no`.

 /IncludeCallsAcrossThreads: `yes`&#124; `no` [nebo]/i: `yes`&#124; `no` volitelné. Určuje, zda se mají zahrnout volání do nebo z jiných vláken. Výchozí hodnota je `no`.

 /ShowExternalCode: `yes`&#124; `no` volitelné. Určuje, zda se má pro zásobník volání zobrazit Pouze můj kód. Pokud je Pouze můj kód vypnutý, zobrazí se všechen neuživatelský kód. Když je Pouze můj kód zapnutý, zobrazí se neuživatelský kód jako `[external]` ve výstupu zásobník volání.

 Vlákno: `n` volitelné. Zobrazí zásobník volání pro `n` vláken. Pokud není zadán žádný podproces, přehraje zásobník volání pro aktuální vlákno.

## <a name="remarks"></a>Poznámky
 Změny argumentů nebo přepínačů se vztahují na budoucí vyvolání tohoto příkazu. Pokud vydáte příkaz Debug. ListCallStackby, zobrazí se celý zásobník volání. Pokud zadáte index, například

```
Debug.ListCallStack 2
```

 aktuální rámec zásobníku je nastaven na tento rámec (v tomto případě druhý rámec).

 Tento příkaz můžete také napsat pomocí jeho předem definovaného aliasu KB. Můžete například zadat

```
kb 2
```

 Chcete-li nastavit aktuální rámec zásobníku na druhý snímek.

## <a name="example"></a>Příklad

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Viz také
 [Vypsat seznam příkazů pro zpětný překlad](../../ide/reference/list-disassembly-command.md) příkazového okna [příkazy](../../ide/reference/visual-studio-commands.md) [příkazového](../../ide/reference/command-window.md) řádku [Najít/příkaz](../../ide/find-command-box.md) [sady Visual Studio](../../ide/reference/list-threads-command.md) [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
