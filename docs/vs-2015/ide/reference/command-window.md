---
title: Příkazové okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c3bcac9f320840faaed32d0622f30e4cbd288ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660835"
---
# <a name="command-window"></a>Příkazové okno
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Příkazové** okno se používá ke spouštění příkazů nebo aliasů přímo v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] integrovaném vývojovém prostředí (IDE). Příkazy nabídky a příkazy, které se nezobrazí v žádné nabídce, můžete spustit. Chcete-li zobrazit **příkazové** okno, zvolte možnost **Další okna** v nabídce **zobrazení** a vyberte **příkazová okna**.

## <a name="displaying-the-values-of-variables"></a>Zobrazení hodnot proměnných
 Chcete-li zjistit hodnotu proměnné `varA` , použijte [příkaz Print](../../ide/reference/print-command.md):

```
>Debug.Print varA
```

 Otazník (?) je alias pro `Debug.Print` , takže tento příkaz lze také zapsat:

```
>? varA
```

 Obě verze tohoto příkazu vrátí hodnotu proměnné `varA` .

## <a name="entering-commands"></a>Zadávání příkazů
 Symbol větší než ( `>` ) se zobrazí na levém okraji okno příkaz jako výzva pro nové řádky. Pomocí kláves Šipka nahoru a šipka dolů můžete procházet předchozí vydané příkazy.

|Úkol|Řešení|Příklad|
|----------|--------------|-------------|
|Vyhodnotit výraz.|Předtvářte výraz s otazníkem ( `?` ).|`? myvar`|
|Přepněte do příkazového podokna.|Zadejte `immed` do okna bez znaménka větší než (>).|`immed`|
|Přepněte zpět na okno Příkaz z příkazového podokna.|`cmd`Do okna zadejte.|`>cmd`|

 Následující klávesové zkratky vám pomůžou s navigací v režimu příkazu.

|Akce|Umístění kurzoru|KeyBinding teprve|
|------------|---------------------|----------------|
|Procházení seznamu dříve zadaných příkazů|Vstupní řádek|ŠIPKA NAHORU & ŠIPKA DOLŮ|
|Posuňte se do okna.|Obsah okno Příkaz|CTRL + ŠIPKA NAHORU|
|Posuňte se dolů na okno.|Obsah okno Příkaz|Šipka dolů nebo CTRL + šipka dolů|

> [!TIP]
> Můžete zkopírovat celý nebo celý předchozí příkaz na vstupní řádek tak, že ho posunete, zvýrazníte jeho část nebo jeho část a potom stisknete klávesu ENTER.

## <a name="mark-mode"></a>Režim označení
 Když kliknete na libovolný předchozí řádek v **příkazovém** okně, automaticky se posune do režimu označení. To vám umožní vybrat, upravit a zkopírovat text předchozích příkazů jako v libovolném textovém editoru a vložit je do aktuálního řádku.

## <a name="the-equals--sign"></a>Symbol rovná se (=)
 Okno použité k zadání `EvaluateStatement` příkazu určuje, zda je znak rovná se (=) interpretován jako operátor porovnání nebo jako operátor přiřazení.

 V **příkazovém** okně je znak rovná se (=) interpretován jako operátor porovnání. V **příkazovém** okně nemůžete použít operátory přiřazení. Takže pokud se například hodnoty proměnných `varA` `varB` liší, pak příkaz

```
>Debug.EvaluateStatement(varA=varB)
```

 Vrátí hodnotu `False` .

 V **příkazovém podokně** je naopak znak rovná se (=) interpretován jako operátor přiřazení. Například příkaz

```
>Debug.EvaluateStatement(varA=varB)
```

 se přiřadí k proměnné `varA` s hodnotou proměnné `varB` .

## <a name="parameters-switches-and-values"></a>Parametry, přepínače a hodnoty
 Některé [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] příkazy mají požadované a nepovinné argumenty, přepínače a hodnoty. Určitá pravidla platí při obchodování s takovými příkazy. V následujícím příkladu je k dispozici příklad bohatých příkazů k objasnění terminologie.

```
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

 V tomhle příkladu je

- `Edit.ReplaceInFiles` je příkaz

- `/case` a `/pattern:regex` jsou přepínače (před znakem lomítka [/])

- `regex` je hodnota `/pattern` přepínače; `/case` přepínač nemá žádnou hodnotu.

- `var[1-3]+` a `oldpar` jsou parametry

  > [!NOTE]
  > Všechny příkazy, parametry, přepínače nebo hodnoty, které obsahují mezery, musí mít na obou stranách dvojité uvozovky.

  Pozice přepínačů a parametrů lze volně měnit na příkazovém řádku s výjimkou příkazu [Shell](../../ide/reference/shell-command.md) , který vyžaduje jeho přepínače a parametry v určitém pořadí.

  Skoro každý přepínač podporovaný příkazem má dvě formy: krátký tvar (jeden znak) a dlouhý tvar. Do skupiny lze sloučit více přepínačů s krátkým tvarem. Například `/p /g /m` může být vyjádřena Alternativně jako `/pgm` .

  Pokud jsou zkrácené přepínače kombinovány do skupiny a zadány hodnoty, tato hodnota se vztahuje na každý přepínač. Například je `/pgm:123` rovno `/p:123 /g:123 /m:123` . Pokud některý z přepínačů ve skupině nepřijímá hodnotu, dojde k chybě.

## <a name="escape-characters"></a>Řídicí znaky
 Znak stříšky (^) na příkazovém řádku znamená, že znak bezprostředně za ním je interpretován doslova, nikoli jako řídicí znak. To lze použít k vložení přímých uvozovek ("), mezer, počátečních lomítek, znakových přepínačů nebo jiných literálových znaků v parametru nebo hodnotě přepínače s výjimkou názvů přepínačů. Příklad:

```
>Edit.Find ^^t /regex
```

 Blikající kurzor funguje stejně, bez ohledu na to, zda se nachází uvnitř nebo vně uvozovek. Pokud je poslední znak na řádku blikající kurzor, ignoruje se. Zde uvedený příklad ukazuje, jak vyhledat vzor "^ t".

## <a name="use-quotes-for-path-names-with-spaces"></a>Použití uvozovek pro názvy cest s mezerami
 Pokud například chcete otevřít soubor, který obsahuje cestu obsahující mezery, je nutné umístit dvojité uvozovky kolem cesty nebo segmentu cesty, který obsahuje mezery: **C: \\ "Program Files"** nebo **"C:\Program Files"**.

## <a name="see-also"></a>Viz také
 Příkazy sady Visual [Studio aliasy](../../ide/reference/visual-studio-command-aliases.md) [příkazů sady Visual Studio](../../ide/reference/visual-studio-commands.md)
