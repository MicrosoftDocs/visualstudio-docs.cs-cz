---
title: 'Návrhář postupu provádění-postupy: použití editoru výrazů'
description: Přečtěte si, jak je editor výrazů Návrhář postupu provádění ovládacím prvkem, který můžete použít v mnoha aktivitách pracovního postupu pro zadávání a vyhodnocení výrazů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 192418439bc25e6ac1b969483c0c48a030caa024
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894072"
---
# <a name="how-to-use-the-expression-editor"></a>Postupy: Používání editoru výrazů

Editor výrazů je Návrhář postupu provádění ovládací prvek, který se používá v mnoha aktivitách pracovního postupu pro zadávání a vyhodnocení výrazů. Editor výrazů poskytuje prostředí pro úpravu podrobnějším integrovaného vývojového prostředí (IDE), včetně IntelliSense, barev, ParamInfo, chybových vlnovek, mimo jiné funkce. Kompilátor po jeho zadání ověří výraz. Pokud je výraz neplatný, zobrazí se ikona chyby. Editor lze také otevřít jako dialogové okno **Editor výrazů** .

Výrazy jsou hodnoty literálu nebo Visual Basic kód vázaný na argumenty nebo vlastnosti. Obsahují prvky hodnoty (například proměnné, konstanty, literály, vlastnosti), které jsou kombinovány s operacemi, aby zadávaly novou hodnotu. Výrazy jsou zapisovány pomocí syntaxe VB.NET, i když je aplikace v programu pomocí jazyka C#. To znamená, že při použití velkých a malých písmen je porovnávání provedeno pomocí jednoho znaménka rovná se (=) místo "= ="), logické operátory jsou slova "a" a "nebo" namísto symbolů "&&" a "| |" a namísto **hodnoty null** nejsou použity **žádné** údaje. Další informace o výrazech a operátorech v Visual Basic a některých ukázkách naleznete v tématu [operátory a výrazy v Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Editor výrazů** se chová takto:

- Pokud fokus není v editoru výrazů, vypadá to jako pravidelný ovládací prvek TextBlock.

- Jakmile je fokus v editoru výrazů, vypadá a chová se jako ovládací prvek editor výrazů. Po ztrátě fokusu bude editor výrazů vypadat jako regulární TextBlock znovu.

- Pokud se zaměříte na Editor výrazů v rámci přehostovaného návrháře pracovního postupu, chová se jako textové pole. Když dojde ke ztrátě fokusu v Návrháři pracovního postupu pro opětovné hostování, Editor výrazů vypadá jako regulární TextBlock znovu.

> [!NOTE]
> IntelliSense pro Editor výrazů je k dispozici pouze uvnitř sady Visual Studio. V rámci sady Visual Studio i v případě znovu hostovaných scénářů kompilátor po jeho zadání ověří výraz a v případě, že je výraz neplatný, zobrazí v editoru výrazů chybovou ikonu.

## <a name="use-the-expression-editor"></a>Používání editoru výrazů

1. V aplikaci Visual Studio otevřete nový nebo existující projekt pracovního postupu.

2. Přidejte například <xref:System.Activities.Statements.Assign> aktivitu do pracovního postupu.

    > [!NOTE]
    > Několik aktivit pracovního postupu má editory výrazů. Výraz TextBlocks se také zobrazí v Návrháři proměnných, v Návrháři argumentů a v Návrháři dynamického argumentu. <xref:System.Activities.Statements.Assign>Aktivita se používá jako příklad.

3. Klikněte na levý Editor výrazů v Návrháři aktivit pro <xref:System.Activities.Statements.Assign> aktivitu.

     Šedé řetězce vodoznaku **\<To>** a **\<Enter a VB Expression>** jsou výchozí textové řetězce pro Editor výrazů v <xref:System.Activities.Statements.Assign> aktivitě.

4. Zadejte svůj výraz. Pokud zadáte řetězec, nezapomeňte kolem řetězce vložit uvozovky. Pokud se rozhodnete vytvořit vazbu argumentu výrazu na proměnnou, ponechte uvozovky vypnuté.

     Až budete hotovi, vyberte oblast nebo oblast mimo editor výrazů, abyste posunuli fokus na jinou část návrháře. Posunutí fokusu způsobí, že kompilátor ověří výraz, jak je popsáno výše.

     Alternativním způsobem, jak zadat nebo upravit výraz, je kliknout na tři tečky vedle názvu vlastnosti v mřížce vlastností. Výběr tří teček otevře **Editor výrazů** jako dialogové okno.

## <a name="see-also"></a>Viz také

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
