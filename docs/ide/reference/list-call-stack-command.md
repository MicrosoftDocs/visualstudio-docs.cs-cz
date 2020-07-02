---
title: Listovat zásobník volání – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34de768f41079311505ae7948502bb4356814ec7
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85770685"
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

## <a name="arguments"></a>Argumenty

`index`\
Nepovinný parametr. Nastaví aktuální rámec zásobníku a nezobrazí žádný výstup.

## <a name="switches"></a>Přepínače
Každý přepínač lze vyvolat buď pomocí jeho úplného formátu, nebo krátkého tvaru.

/Count: `number` [nebo]/c:`number`

Nepovinný parametr. Maximální počet zásobníků volání, které se mají zobrazit Výchozí hodnota je neomezená.

/ShowTypes: `yes`&#124;`no` [nebo]/t: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazit typy parametrů. Výchozí hodnota je `yes` .

/ShowNames: `yes`&#124;`no` [nebo]/n: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazovat názvy parametrů. Výchozí hodnota je `yes` .

/ShowValues: `yes`&#124;`no` [nebo]/v: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazovat hodnoty parametrů. Výchozí hodnota je `yes` .

/ShowModule: `yes`&#124;`no` [nebo]/m: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má zobrazit název modulu. Výchozí hodnota je `yes` .

/ShowLineOffset: `yes`&#124;`no` [nebo]/#: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má zobrazit posun řádku. Výchozí hodnota je `no` .

/ShowByteOffset: `yes`&#124;`no` [nebo]/b: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má zobrazovat posun bajtů. Výchozí hodnota je `no` .

/ShowLanguage: `yes`&#124;`no` [nebo]/l: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má jazyk zobrazit. Výchozí hodnota je `no` .

/IncludeCallsAcrossThreads: `yes`&#124;`no` [nebo]/i: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se mají zahrnout volání do nebo z jiných vláken. Výchozí hodnota je `no` .

/ShowExternalCode: `yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má pro zásobník volání zobrazit Pouze můj kód. Pokud je Pouze můj kód vypnutý, zobrazí se všechen neuživatelský kód. Když je Pouze můj kód zapnutý, zobrazí se neuživatelský kód jako `[external]` ve výstupu zásobník volání.

Doporučujeme`n`

Nepovinný parametr. Zobrazí zásobník volání pro vlákno `n` . Pokud není zadán žádný podproces, aplikace zobrazí zásobník volání pro aktuální vlákno.

## <a name="remarks"></a>Poznámky
Změny argumentů nebo přepínačů se vztahují na budoucí vyvolání tohoto příkazu. Pokud vydáte příkaz Debug. ListCallStackby, zobrazí se celý zásobník volání. Pokud zadáte index, například

```cmd
Debug.ListCallStack 2
```

aktuální rámec zásobníku je nastaven na tento rámec (v tomto případě druhý rámec).

Tento příkaz můžete také napsat pomocí jeho předem definovaného aliasu KB. Můžete například zadat

```cmd
kb 2
```

Chcete-li nastavit aktuální rámec zásobníku na druhý snímek.

## <a name="example"></a>Příklad

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Viz také:

- [Výpis zpětného překladu příkazu](../../ide/reference/list-disassembly-command.md)
- [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)