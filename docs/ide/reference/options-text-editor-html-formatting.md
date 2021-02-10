---
title: Možnosti, textový editor, HTML (webové formuláře), formátování
description: Naučte se používat stránku formátování v sekci HTML k nastavení možností projektu HTML pro formátování kódu v editoru kódu.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd8d7e6bd81e32858f990c70bbcdf0bf00049867
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943832"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Možnosti, textový editor, HTML (webové formuláře), formátování

Stránka možnosti **formátování** slouží k nastavení možností projektu HTML pro formátování kódu v editoru kódu. Chcete-li získat přístup k této stránce, v řádku nabídek zvolte  >  **možnost** nástroje a potom rozbalte formátování **textový editor**  >  **HTML (webové formuláře)**  >  .

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
|**Velká písmena**|Názvy elementů jsou přeformátovány na velká písmena.|
|**Malá písmena**|Názvy elementů jsou přeformátovány na malá písmena.|
|**Definice sestavení**|Element Case je určen podle toho, jak je element definován v odpovídající třídě typu.|

**Klientské značky, atributy klienta**

Tyto možnosti určují, zda automatické formátování mění názvy atributů HTML a vlastností na velká a malá písmena, nebo je zachovává jako zadané.

|Možnost|Výsledek|
|---------------------------------|------------------------------|
|**Jak je zadáno**|Atribut Case je přesně tak, jak ho zadáte.|
|**Velká písmena**|Názvy atributů se přeformátují na velká písmena.|
|**Malá písmena**|Názvy atributů se přeformátují na malá písmena.|

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

   Pokud je vybrána tato možnost, Editor automaticky vytvoří uzavírací značku (například **\</b>** ) při zavření otevírací značky.

## <a name="tag-wrapping"></a>Zalamování značky

Tyto možnosti určují, zda editor rozdělí štítky na řádky, pokud přesahují určitou délku.

### <a name="uielement-list"></a>UIElement – seznam

- **Zalamovat značky při překročení zadané délky**

   Je-li vybrána tato možnost, Editor rozdělí značky mezi řádky, pokud značka přesahuje délku, kterou zadáte v textovém poli **Délka** . K této akci dochází pouze při formátování značky, nikoli při psaní nové značky.

   > [!NOTE]
   > Hodnota, kterou zadáte, se používá jako minimální hodnota. Editor nerozdělí jednotlivé atributy.

- **Délka**

   Určuje počet znaků, které mají být zobrazeny v řádku před zabalením. Toto vstupní pole je zakázáno, pokud je zaškrtnuto políčko **po překročení zadané délky** .

- **Možnosti specifické pro značku**

   Zobrazí dialogové okno **možnosti specifické pro značku** , které umožňuje nastavit možnosti formátování pro jednotlivé značky nebo skupiny značek.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
