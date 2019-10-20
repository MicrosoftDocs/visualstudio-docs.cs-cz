---
title: 'Postupy: použití editoru výrazů | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6157646526a2d634ff5034d98eb497c00585c067
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659093"
---
# <a name="how-to-use-the-expression-editor"></a>Postupy: použití editoru výrazů
Editor výrazů je [!INCLUDE[wfd1](../includes/wfd1-md.md)] ovládací prvek, který se používá v mnoha aktivitách pracovního postupu jako způsob, jak zadávat a vyhodnocovat tyto výrazy. Editor výrazů poskytuje podrobnějším prostředí pro úpravy integrovaného vývojového prostředí (IDE), včetně IntelliSense, barev, ParamInfo, chybových vlnovek, mimo jiné funkce. Kompilátor po zadání vyhodnotí výraz. Pokud je výraz neplatný, zobrazí se ikona chyby. Editor lze také otevřít jako dialogové okno **Editor výrazů** .

 Výrazy jsou hodnoty literálu nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kód vázaný na argumenty nebo vlastnosti. Obsahují prvky hodnoty (např. proměnné, konstanty, literály, vlastnosti), které jsou kombinovány s operacemi, aby vydávaly novou hodnotu. Výrazy jsou zapisovány pomocí syntaxe VB.NET, i když je aplikace v programu pomocí C#. To znamená, že při použití velkých a malých písmen je porovnávání provedeno pomocí jednoho znaménka rovná se ("=") namísto ("= ="), logické operátory jsou slova "a" nebo "namísto symbolů" & & "a"&#124;&#124;"a **nic** se nepoužívá. místo **hodnoty null**. Další informace o výrazech a operátorech v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a některých ukázkách naleznete v tématu [operátory a výrazy v Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 **Editor výrazů** se chová takto:

- Pokud fokus není v editoru výrazů, vypadá to jako pravidelný ovládací prvek TextBlock.

- Jakmile je fokus v editoru výrazů, vypadá a chová se jako ovládací prvek editor výrazů. Až se fokus ztratí, vypadá to jako běžné TextBlock.

- Pokud se zaměříte na Editor výrazů v rámci přehostovaného návrháře pracovního postupu, chová se jako textové pole. Když dojde ke ztrátě fokusu v Návrháři pracovního postupu pro opětovné hostování, Editor výrazů vypadá jako regulární TextBlock znovu.

> [!NOTE]
> IntelliSense pro Editor výrazů je k dispozici pouze uvnitř [!INCLUDE[vs2010](../includes/vs2010-md.md)]. V [!INCLUDE[vs2010](../includes/vs2010-md.md)] i ve scénářích opětovného hostování kompilátor po jeho zadání ověří výraz a Editor výrazů zobrazí chybovou ikonu, pokud je výraz neplatný.

### <a name="using-the-expression-editor"></a>Použití editoru výrazů

1. V [!INCLUDE[vs2010](../includes/vs2010-md.md)] otevřete nový nebo existující projekt pracovního postupu.

2. Přidejte například aktivitu <xref:System.Activities.Statements.Assign> do pracovního postupu.

    > [!NOTE]
    > Několik aktivit pracovního postupu má editory výrazů. Výraz TextBlocks se také zobrazí v Návrháři proměnných, v Návrháři argumentů a v Návrháři dynamického argumentu. Jako příklad se používá aktivita <xref:System.Activities.Statements.Assign>.

3. Klikněte na levý Editor výrazů v Návrháři aktivit pro aktivitu <xref:System.Activities.Statements.Assign>.

     Šedé řetězce vodoznaku **\<To >** a **\<Enter > výrazu VB** jsou výchozí textové řetězce pro Editor výrazů v aktivitě <xref:System.Activities.Statements.Assign>.

4. Zadejte svůj výraz. Pokud zadáte řetězec, nezapomeňte kolem řetězce vložit uvozovky. Pokud se rozhodnete vytvořit vazbu argumentu výrazu na proměnnou, ponechte uvozovky vypnuté.

     Až budete hotovi, vyberte oblast nebo oblast mimo editor výrazů, abyste posunuli fokus na jinou část návrháře. Tím dojde k tomu, že kompilátor ověří výraz, jak je popsáno výše.

     Alternativním způsobem, jak zadat nebo upravit výraz, je kliknout na tři tečky vedle názvu vlastnosti v mřížce vlastností. Otevře se **Editor výrazů** jako dialogové okno.

## <a name="see-also"></a>Viz také
 <xref:System.Activities.Presentation.View.ExpressionTextBox>