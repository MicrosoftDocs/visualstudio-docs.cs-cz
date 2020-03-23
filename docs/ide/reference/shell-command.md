---
title: Prostředí – příkaz
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bf13c7624d6c9d8e64b79f653eb83a0c5f3b3f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565874"
---
# <a name="shell-command"></a>Prostředí – příkaz
Spustí spustitelné programy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]z aplikace .

## <a name="syntax"></a>Syntaxe

```cmd
Tools.Shell [/command] [/output] [/dir:folder] path [args]
```

## <a name="arguments"></a>Argumenty
`path`

Povinná hodnota. Cesta a název souboru, který má být spuštěn, nebo dokument, který chcete otevřít. Úplná cesta je vyžadována, pokud zadaný soubor není v jednom z adresářů v proměnné prostředí PATH.

`args`

Nepovinný parametr. Všechny argumenty předat vyvolaný program.

## <a name="switches"></a>Přepínače
/commandwindow [nebo] /command [or] /c [or] /cmd

Nepovinný parametr. Určuje, že výstup spustitelného souboru se zobrazí v okně **Příkaz.**

/dir:`folder` [nebo] /d:`folder`

Nepovinný parametr. Určuje pracovní adresář, který má být nastaven při spuštění programu.

/outputwindow [nebo] /output [or] /out [or] /o

Nepovinný parametr. Určuje, že výstup spustitelného souboru se zobrazí v okně **Výstup.**

## <a name="remarks"></a>Poznámky
Přepínače /dir /o /c musí `Tools.Shell`být zadány ihned po . Vše, co bylo zadáno za názvem spustitelného souboru, je předáno jako argumenty příkazového řádku.

Předdefinovaný alias `Shell` lze použít místo `Tools.Shell`.

> [!CAUTION]
> Pokud `path` argument poskytuje cestu k adresáři i název souboru, měli byste celý název cesty uzavřít do literálových uvozovek ("""), jako v následujícím textu:

```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

Každá sada tří dvojitých uvozovek (""") je `Shell` interpretována procesorem jako jeden znak dvojité uvozovky. Předchozí příklad tedy ve skutečnosti předá příkazu následující řetězec `Shell` cesty:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Pokud neuzavřete řetězec cesty do literálových uvozovek (""),"), systém Windows použije pouze část řetězce až do první mezery. Pokud například výše uvedený řetězec cesty nebyl správně uveden, systém Windows by hledal soubor s názvem "Program" umístěný v c:\ kořenový adresář. Pokud by byl skutečně k dispozici spustitelný soubor C:\Program.exe, i když byl nainstalován nedovoleným neoprávněným zásahem, systém Windows by se pokusil spustit tento program namísto požadovaného programu "c:\Program Files\SomeFile.exe".

## <a name="example"></a>Příklad
Následující příkaz používá xcopy.exe ke `MyText.txt` zkopírování souboru do `Text` složky. Výstup z příkazu xcopy.exe se zobrazí v **okně Příkaz i** **Output.**

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Výstupní okno](../../ide/reference/output-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
