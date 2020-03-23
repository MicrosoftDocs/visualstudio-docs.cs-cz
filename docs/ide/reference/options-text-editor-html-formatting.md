---
title: Volby, Textový editor, HTML (webové formuláře), formátování
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e28caf7f71af7c7a07634d1732a1001a32a4aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568318"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Volby, Textový editor, HTML (webové formuláře), formátování

Stránka **Možnosti formátování** slouží k nastavení možností projektu HTML pro formátování kódu v Editoru kódu. Chcete-li získat přístup k této stránce, zvolte na řádku nabídek**možnostI** **nástroje** > a potom rozbalte formátování**HTML (Webové formuláře)** >  **textového editoru** > (Webové formuláře).**Formatting**

## <a name="capitalization"></a>Velká písmena

Když jsou vybrány tyto možnosti, editory zobrazení zdroj a XML aplikují výchozí formát případu na názvy prvků a atributů při prvním vytvoření prvků a během automatického formátování. Nastavení **Použít automatické formátování** určuje čas automatického přeformátování.

> [!WARNING]
> Jazyk XML rozlišuje malá a velká písmena. Nastavení výchozího případu může mít vliv na analyzátory XML.

### <a name="uielement-list"></a>Seznam Prvků UI

**Značka serveru, atributy serveru**

Tyto možnosti určují, jak jsou značky pro ovládací prvky webového serveru velkými písmeny.

|Možnost|Výsledek|
|---------------------------------|------------------------------|
|**Jak bylo zadáno**|Případ elementu je přesně tak, jak jej zadáte.|
|**Velká písmena**|Názvy prvků jsou přeformátovány na velká písmena.|
|**Malá písmena**|Názvy prvků jsou přeformátovány na malá písmena.|
|**Definice sestavení**|Případ prvku je určen tím, jak je prvek definován v odpovídající třídě typu.|

**Značka klienta, atributy klienta**

Tyto volby určují, zda automatické formátování změní názvy atributů a vlastností HTML na velká nebo malá písmena, nebo zda je zachová tak, jak jsou zadány.

|Možnost|Výsledek|
|---------------------------------|------------------------------|
|**Jak bylo zadáno**|Případ atributu je přesně tak, jak jej zadáte.|
|**Velká písmena**|Názvy atributů jsou přeformátovány na velká písmena.|
|**Malá písmena**|Názvy atributů jsou přeformátovány na malá písmena.|

## <a name="automatic-formatting-options"></a>Možnosti automatického formátování

Tyto možnosti způsobí, že editor zobrazení zdroje přidá nebo odebere fyzické zalomení řádků během automatického formátování. Můžete také určit, zda editor přidá uvozovky kolem atributů.

> [!NOTE]
> Tato nastavení nemění prázdné místo v rámci značek XML.

### <a name="uielement-list"></a>Seznam Prvků UI

- **Vložení uvozovek hodnoty atributu při psaní**

   Je-li vybrána tato možnost, editor při psaní automaticky umístí uvozovky kolem atributů (například: ID="Select1"). Zrušte zaškrtnutí této možnosti, pokud dáváte přednost ručnímu vkládání uvozovek do značek.

   > [!NOTE]
   > Bez ohledu na to, zda je tato možnost vybrána, budou zachovány všechny existující uvozovky ve značce. uvozovky nejsou nikdy odstraněny.

- **Vložení uvozovek hodnoty atributu při formátování**

   Je-li vybrána tato možnost, přidá automatické formátování uvozovky kolem hodnot atributů (například: ID="Select1").

   > [!NOTE]
   > Bez ohledu na to, zda je tato možnost vybrána, budou zachovány všechny existující uvozovky ve značkách.

- **Značka automatického vložení zavření**

   Je-li vybrána tato možnost, editor automaticky vytvoří uzavírací značku (například ** \</b>) **při zavření otevírací značky.

## <a name="tag-wrapping"></a>Balení značek

Tyto možnosti určují, zda editor rozdělí značky na řádky, pokud překročí určitou délku.

### <a name="uielement-list"></a>Seznam Prvků UI

- **Zalamování tagů při překročení zadané délky**

   Když je tato volba vybraná, editor rozdělí tagy mezi řádky, pokud značka překročí délku, kterou zadáte v textovém poli **Délka.** K této akci dochází pouze při formátování značky, nikoli při zadávání nové značky.

   > [!NOTE]
   > Zadaná hodnota se používá jako minimální hodnota. Editor nerozbije jednotlivé atributy.

- **Délka**

   Určuje počet znaků, které se mají zobrazit v řádku před obtékáním. Toto vstupní pole je zakázáno, pokud není zaškrtnuto políčko **Zalamovat značky při překročení zadané délky.**

- **Možnosti pro konkrétní značky**

   Zobrazí dialogové okno **Volby specifické pro značku,** které umožňuje nastavit možnosti formátování pro jednotlivé značky nebo skupiny tagů.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
