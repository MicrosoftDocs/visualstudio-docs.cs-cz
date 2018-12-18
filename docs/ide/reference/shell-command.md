---
title: Prostředí – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04ec2719b57f387633a7244d7089be963d3ba87c
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704100"
---
# <a name="shell-command"></a>Prostředí – příkaz
Spustí spustitelné programy uvnitř [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Arguments
 `path`

 Požadováno. Název a cesta k souboru souboru provést nebo dokument, který chcete otevřít. Úplná cesta je vyžaduje, pokud zadaný soubor není v jednom z adresáře v proměnné prostředí PATH.

 `args`

 Volitelné. Všechny argumenty mají být předány vyvolaný program.

## <a name="switches"></a>Přepínače
 /CommandWindow [nebo] / Command – [nebo] /c [nebo] / cmd

 Volitelné. Určuje, že je v zobrazí výstup pro spustitelný soubor **příkaz** okno.

 /dir:`folder` [nebo] / d: `folder`

 Volitelné. Určuje pracovní adresář, který má být nastavená při spuštění programu.

 /outputwindow [nebo] / Output [nebo] / out [nebo] /o

 Volitelné. Určuje, že je v zobrazí výstup pro spustitelný soubor **výstup** okno.

## <a name="remarks"></a>Poznámky
 Musí být zadán přepínačích /c /o /dir hned za `Tools.Shell`. Nic zadaných po název spustitelného souboru je předán do ní jako argumenty příkazového řádku.

 Předdefinované alias `Shell` lze místě `Tools.Shell`.

> [!CAUTION]
> Pokud `path` argument poskytuje cesta k adresáři, jakož i název souboru, by měl uzavřete celý název cesty do uvozovek a být literálu ("" "), protože v následujících tématech:


```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Každá sada tři dvojité uvozovky ("" ") je interpretována `Shell` procesoru jako jeden dvojité uvozovky. Proto v předchozím příkladu ve skutečnosti předá následující řetězec cesty `Shell` příkaz:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Pokud je řetězec cesty není uzavřít do uvozovek a literálu ("" "), Windows použije jenom ta část řetězce po první mezeru. Například pokud řetězec cesty výše nebyly správně uvozovkách, Windows by hledat soubor s názvem "Programu" se nachází v kořenovém adresáři C:\. Pokud spustitelný soubor C:\Program.exe byly ve skutečnosti k dispozici, i jeden nainstalovat nezákonné manipulaci Windows by pokus o spuštění tohoto programu místo programu požadované "c:\Program Files\SomeFile.exe".


## <a name="example"></a>Příklad
 Následující příkaz používá xcopy.exe při kopírování souboru `MyText.txt` do `Text` složky. Zobrazí se výstup z xcopy.exe v obou **příkazové okno** a **výstup** okno.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Okno Výstup](../../ide/reference/output-window.md)
- [Pole najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)