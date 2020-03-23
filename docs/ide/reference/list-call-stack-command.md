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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f62852550c161566832a7ab78d4058d1d14028f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "72748712"
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
Nepovinný parametr. Nastaví aktuální snímek zásobníku a nezobrazí žádný výstup.

## <a name="switches"></a>Přepínače
Každý přepínač lze vyvolat pomocí jeho kompletní formulář nebo krátký formulář.

/Počet:`number` [nebo] /C:`number`

Nepovinný parametr. Maximální počet zásobníků volání, které se mají zobrazit. Výchozí hodnota je neomezená.

/ShowTypes:`yes` `no`&#124;[nebo]`yes` /T:&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazit typy parametrů. Výchozí hodnota `yes`je .

/ShowNames:`yes` `no`&#124;[nebo]`yes` /N:&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazit názvy parametrů. Výchozí hodnota `yes`je .

/ShowValues:`yes` `no`&#124;[nebo]`yes` /V:&#124;`no`

Nepovinný parametr. Určuje, zda se mají zobrazit hodnoty parametrů. Výchozí hodnota `yes`je .

/ShowModule:`yes` `no`&#124;[nebo]`yes` /M:&#124;`no`

Nepovinný parametr. Určuje, zda se má zobrazit název modulu. Výchozí hodnota `yes`je .

/ShowLineOffset:`yes` `no`&#124;[nebo]`yes` /#:&#124;`no`

Nepovinný parametr. Určuje, zda se má odsazení čáry zobrazit. Výchozí hodnota `no`je .

/ShowByteOffset:`yes` `no`&#124;[nebo]`yes` /B:&#124;`no`

Nepovinný parametr. Určuje, zda se má odsazení bajtů zobrazit. Výchozí hodnota `no`je .

/ShowLanguage:`yes` `no`&#124;[nebo]`yes` /L:&#124;`no`

Nepovinný parametr. Určuje, zda se má jazyk zobrazit. Výchozí hodnota `no`je .

/IncludeCallsAcrossThreads:`yes` `no`&#124;[nebo]`yes` /I:&#124;`no`

Nepovinný parametr. Určuje, zda má být zahrnuta volání do nebo z jiných vláken. Výchozí hodnota `no`je .

/ShowExternalCode:`yes`&#124;`no`

Nepovinný parametr. Určuje, zda se má zobrazit pouze můj kód pro zásobník volání. Když je vypnutý jen můj kód, zobrazí se veškerý neuživatelský kód. Když jen můj kód je zapnutý, neuživatelský `[external]` kód se zobrazí jako ve výstupu zásobníku volání.

Vlákno:`n`

Nepovinný parametr. Zobrazí zásobník volání `n`pro vlákno . Pokud není zadáno žádné vlákno, zobrazí zásobník volání pro aktuální vlákno.

## <a name="remarks"></a>Poznámky
Změny provedené v argumentech nebo přepínačích platí pro budoucí vyvolání tohoto příkazu. Pokud problém debug.ListCallStackby sám, zobrazí se celý zásobník volání. Pokud například zadáte index,

```cmd
Debug.ListCallStack 2
```

pak je aktuální snímek zásobníku nastaven na tento snímek (v tomto případě druhý snímek).

Tento příkaz můžete také napsat pomocí jeho předdefinovaného aliasu kb. Můžete například zadat

```cmd
kb 2
```

nastavte aktuální snímek zásobníku na druhý snímek.

## <a name="example"></a>Příklad

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Viz také

- [Zobrazit zpětný překlad – příkaz](../../ide/reference/list-disassembly-command.md)
- [Listovat vlákna – příkaz](../../ide/reference/list-threads-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)