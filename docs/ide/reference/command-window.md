---
title: Příkazové okno
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb855cbed67bffc5ff2fb63b1785c577dd9fea25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570346"
---
# <a name="command-window"></a>Příkazové okno
Okno **Příkaz** se používá ke spouštění příkazů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nebo aliasů přímo v integrovaném vývojovém prostředí (IDE). Můžete provést příkazy nabídky i příkazy, které se nezobrazují v žádné nabídce. Chcete-li zobrazit **okno Příkaz,** zvolte Z nabídky **Zobrazení** vyberte Jiný **systém Windows** a vyberte Příkaz **Window**.

## <a name="displaying-the-values-of-variables"></a>Zobrazení hodnot proměnných
Chcete-li zkontrolovat hodnotu proměnné `varA`, použijte příkaz [Tisk](../../ide/reference/print-command.md):

```cmd
>Debug.Print varA
```

Otazník (?) je `Debug.Print`alias pro , takže tento příkaz může být také zapsán:

```cmd
>? varA
```

Obě verze tohoto příkazu vrátí hodnotu `varA`proměnné .

## <a name="entering-commands"></a>Zadávání příkazů
Symbol větší než`>`( ) se zobrazí na levém okraji okna Příkaz jako výzva k zadání nových řádků. Pomocí kláves ŠIPKA NAHORU a ŠIPKA DOLŮ můžete procházet dříve vydané příkazy.

|Úkol|Řešení|Příklad|
|----------|--------------|-------------|
|Vyhodnoťte výraz.|Předmluva výrazu s`?`otazníkem ( ).|`? myvar`|
|Přepněte do okna Okamžité.|Vstup `immed` do okna bez větší než znaménko (>)|`immed`|
|Přepněte zpět do okna Příkaz z okna Okamžité.|Vstupte `cmd` do okna.|`>cmd`|

Následující klávesové zkratky vám pomohou procházet v režimu příkazu.

|Akce|Umístění kurzoru|Keybinding|
|------------| - |----------------|
|Procházet seznam emitovaných příkazů.|Vstupní řádek|ŠIPKA NAHORU & ŠIPKA DOLŮ|
|Posuňte se nahoru v okně.|Obsah okna příkazu|CTRL + ŠIPKA NAHORU|
|Posuňte se dolů v okně.|Obsah okna příkazu|ŠIPKA DOLŮ nebo CTRL+ŠIPKA DOLŮ|

> [!TIP]
> Můžete zkopírovat celý předchozí příkaz nebo jeho část na vstupní řádek posouváním, zvýrazněním celého příkazu nebo jeho části a stisknutím klávesy ENTER.

## <a name="mark-mode"></a>Označit režim
Když kliknete na libovolný předchozí řádek v okně **Příkaz,** automaticky se přesunete do režimu označit. To vám umožní vybrat, upravit a zkopírovat text předchozích příkazů stejně jako v libovolném textovém editoru a vložit je do aktuálního řádku.

## <a name="the-equals--sign"></a>Znaménko rovná se (=)
Okno použité k `EvaluateStatement` zadání příkazu určuje, zda je znaménko rovná se (=) interpretováno jako operátor porovnání nebo jako operátor přiřazení.

V okně **Příkaz** je znaménko rovná se (=) interpretováno jako operátor porovnání. V okně **Příkaz** nelze použít operátory přiřazení. Pokud se tedy například hodnoty `varA` proměnných liší, `varB` příkaz `>Debug.EvaluateStatement(varA=varB)` vrátí hodnotu `False`.

V okně **Okamžité** je naopak znaménko rovná se (=) interpretováno jako operátor přiřazení. Tak například, příkaz `>Debug.EvaluateStatement(varA=varB)` přiřadí `varA` proměnné hodnotu `varB`proměnné .

## <a name="parameters-switches-and-values"></a>Parametry, přepínače a hodnoty
Některé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] příkazy mají povinné a volitelné argumenty, přepínače a hodnoty. Při práci s těmito příkazy platí určitá pravidla. Následuje příklad bohatého příkazu k objasnění terminologie.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

V tomhle příkladu je

- `Edit.ReplaceInFiles`je příkaz

- `/case`a `/pattern:regex` jsou přepínače (předlohy znaku lomítka [/])

- `regex`je hodnota spínače; `/pattern` `/case` přepínač nemá žádnou hodnotu

- `var[1-3]+`a `oldpar` jsou parametry

    > [!NOTE]
    > Všechny příkazy, parametry, přepínače nebo hodnoty, které obsahují mezery, musí mít na obou stranách dvojité uvozovky.

Poloha přepínačů a parametrů může být volně zaměřována na příkazovém řádku s výjimkou příkazu [Shell,](../../ide/reference/shell-command.md) který vyžaduje jeho přepínače a parametry v určitém pořadí.

Téměř každý přepínač podporovaný příkazem má dvě formy: krátký (jeden znak) formulář a dlouhý formulář. Více přepínačů krátkého tvaru lze kombinovat do skupiny. Například `/p /g /m` může být vyjádřena `/pgm`střídavě jako .

Pokud jsou přepínače krátkého tvaru sloučeny do skupiny a mají hodnotu, tato hodnota platí pro každý přepínač. Například `/pgm:123` se rovná `/p:123 /g:123 /m:123`. K chybě dochází, pokud některý z přepínačů ve skupině nepřijímá hodnotu.

## <a name="escape-characters"></a>Řídicí znaky
Znak stříšky (^) v příkazovém řádku znamená, že znak bezprostředně za ním je interpretován doslovně, nikoli jako řídicí znak. To lze použít k vložení rovných uvozovek (), mezery, úvodní lomítka, stříšky nebo jiné literál znaky v parametru nebo přepínač hodnoty, s výjimkou názvů přepínačů. Například:

```cmd
>Edit.Find ^^t /regex
```

Stříška funguje stejně bez ohledu na to, zda je uvnitř nebo vně uvozovek. Pokud stříška je poslední znak na řádku, je ignorována. Zde uvedený příklad ukazuje, jak vyhledat vzor ^t.

## <a name="use-quotes-for-path-names-with-spaces"></a>Použití uvozovek pro názvy cest s mezerami
Pokud například chcete otevřít soubor, který má cestu obsahující mezery, musíte dát dvojité uvozovky kolem cesty nebo segmentu cesty, který obsahuje mezery: **C:\\"ProgramFiles"** nebo **"C:\Program Files"**.

## <a name="see-also"></a>Viz také

- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
