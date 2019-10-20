---
title: Možnosti, textový editor, HTML (webové formuláře), formátování
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d1e5f07a2b68d86051452a16ac0f42fc9b9acf0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666197"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Možnosti, textový editor, HTML (webové formuláře), formátování

Stránka možnosti **formátování** slouží k nastavení možností projektu HTML pro formátování kódu v editoru kódu. Chcete-li získat přístup k této stránce, v řádku nabídek zvolte možnost **nástroje**  > **Možnosti**a poté rozbalte položku **textový editor**  > **HTML (webové formuláře)**  > **formátování**.

## <a name="capitalization"></a>Malá

Pokud jsou tyto možnosti vybrány, zobrazení zdroje a editory XML použijí výchozí formát případu pro názvy prvků a atributů při prvním vytvoření prvků a při automatickém formátování. Nastavení **použít automatické formátování** určuje čas, kdy dochází k automatickému přeformátování.

> [!WARNING]
> V jazyce XML se rozlišují malá a velká písmena. Nastavení výchozího případu může mít vliv na analyzátory XML.

### <a name="uielement-list"></a>UIElement – seznam

**Značka serveru, atributy serveru**

Tyto možnosti určují, jak se má kód pro ovládací prvky webového serveru navýšit na velká.

|Možnost|Výsledek|
|---------------------------------|------------------------------|
|**Jak je zadáno**|Případ prvku je přesně tak, jak ho zadáte.|
|**Všechna**|Názvy elementů jsou přeformátovány na velká písmena.|
|**Malá**|Názvy elementů jsou přeformátovány na malá písmena.|
|**Definice sestavení**|Element Case je určen podle toho, jak je element definován v odpovídající třídě typu.|

**Klientské značky, atributy klienta**

Tyto možnosti určují, zda automatické formátování mění názvy atributů HTML a vlastností na velká a malá písmena, nebo je zachovává jako zadané.

|Možnost|Výsledek|
|---------------------------------|------------------------------|
|**Jak je zadáno**|Atribut Case je přesně tak, jak ho zadáte.|
|**Všechna**|Názvy atributů se přeformátují na velká písmena.|
|**Malá**|Názvy atributů se přeformátují na malá písmena.|

## <a name="automatic-formatting-options"></a>Možnosti automatického formátování

Tyto možnosti způsobí, že editor zobrazení zdroje při automatickém formátování přidá nebo odebere přerušení fyzické čáry. Můžete také určit, zda editor přidá uvozovky kolem atributů.

> [!NOTE]
> Tato nastavení nemění prázdné znaky v kódu XML.

### <a name="uielement-list"></a>UIElement – seznam

- **Při psaní vkládat hodnoty atributů do uvozovek**

   Pokud je vybrána tato možnost, Editor automaticky vloží uvozovky kolem atributů, jak píšete (například: ID = "select1"). Tuto možnost zrušte, pokud dáváte přednost ručnímu vložení značek do kódu.

   > [!NOTE]
   > Bez ohledu na to, zda je tato možnost vybrána, jsou zachovány všechny existující uvozovky ve vašem kódu; uvozovky se nikdy neodebraly.

- **Při formátování vkládat hodnoty atributů do uvozovek**

   Pokud je vybrána tato možnost, automatické formátování přidá uvozovky kolem hodnot atributů (například: ID = "select1").

   > [!NOTE]
   > Bez ohledu na to, zda je tato možnost vybrána, jsou zachovány všechny existující uvozovky ve vašem kódu.

- **Automaticky vkládat uzavírací značku**

   Pokud je vybrána tato možnost, editor při zavření počáteční značky automaticky vytvoří uzavírací značku (například **\</b >** ).

## <a name="tag-wrapping"></a>Zalamování značky

Tyto možnosti určují, zda editor rozdělí štítky na řádky, pokud přesahují určitou délku.

### <a name="uielement-list"></a>UIElement – seznam

- **Zalamovat značky při překročení zadané délky**

   Je-li vybrána tato možnost, Editor rozdělí značky mezi řádky, pokud značka přesahuje délku, kterou zadáte v textovém poli **Délka** . K této akci dochází pouze při formátování značky, nikoli při psaní nové značky.

   > [!NOTE]
   > Hodnota, kterou zadáte, se používá jako minimální hodnota. Editor nerozdělí jednotlivé atributy.

- **Časový**

   Určuje počet znaků, které mají být zobrazeny v řádku před zabalením. Toto vstupní pole je zakázáno, pokud je zaškrtnuto políčko **po překročení zadané délky** .

- **Možnosti specifické pro značku**

   Zobrazí dialogové okno **možnosti specifické pro značku** , které umožňuje nastavit možnosti formátování pro jednotlivé značky nebo skupiny značek.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)