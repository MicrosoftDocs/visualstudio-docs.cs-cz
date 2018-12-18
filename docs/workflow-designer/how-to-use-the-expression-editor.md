---
title: 'Návrhář postupu provádění - postupy: použití editoru výraz'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1f2ab9cad6f54b8d1106fd68eb017434cf5cfef
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756139"
---
# <a name="how-to-use-the-expression-editor"></a>Postupy: použití editoru výraz

Editor výrazů je ovládací prvek Návrháře pracovního postupu, který slouží k zadání a vyhodnocení výrazů v mnoha aktivit pracovního postupu. Plnohodnotný IDE úpravy prostředí, včetně technologii IntelliSense, zabarvení nabízí Editor výraz ParamInfo podtržení vlnovkou chyba mezi dalších funkcí. Kompilátor ověří výraz poté, co je zadána. Pokud ve výrazu je neplatná, zobrazí se ikona chyby. Editor můžete otevřít také jako **Editor výrazů** dialogové okno.

Výrazy jsou literálových hodnot nebo kód jazyka Visual Basic svázané se argumenty nebo vlastnosti. Obsahují hodnotu elementy (například proměnné, konstanty, literály, vlastnosti), které jsou spojené s operací yield novou hodnotu. Výrazy jsou zapsány pomocí syntaxe VB.NET i v případě, že aplikace bude v programu pomocí jazyka C#. To znamená, malá a velká písmena, nezáleží, porovnání se provádí pomocí jednoho rovná přihlásit ("=" místo "=="), jsou logické operátory slova "a" a "nebo" místo symboly "& &" a "||", a **nic** slouží místo **null**. Další informace o výrazy a operátory v jazyce Visual Basic a některé vzorky najdete v části [operátory a výrazy v jazyce Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

**Editor výrazů** chová následovně:

- Pokud fokus není v editoru výrazu, vypadá jako regulární TextBlock ovládacího prvku.

- Jakmile je zaměřená na editoru výrazu, vzhled a chování jako ovládací prvek Editor výrazů. Po jeho ztratí fokus, editoru výraz znovu vypadá jako regulární TextBlock.

- Pokud byste se zaměřit na Editor výrazů v Návrháři opětovné hostování nástroje pracovního postupu, pak se chová jako textové pole. Pokud je fokus ztratili v Návrháři pracovních postupů opětovné hostování nástroje, editoru výraz znovu vypadá jako regulární TextBlock.

> [!NOTE]
> IntelliSense pro Editor výrazu je k dispozici pouze v aplikaci Visual Studio. V sadě Visual Studio a opětovné hostování nástroje scénáře kompilátor ověří výraz po zadání se a editoru výraz zobrazuje ikonu chyby, pokud výraz je neplatný.

## <a name="use-the-expression-editor"></a>Použití editoru výraz

1.  V sadě Visual Studio otevřete projekt nového nebo stávajícího pracovního postupu.

2.  Přidání, například <xref:System.Activities.Statements.Assign> aktivitu do pracovního postupu.

    > [!NOTE]
    > Více aktivit pracovního postupu mít editory výraz. Objekty TextBlock výraz se zobrazí také v Návrháři proměnné, argument designer a návrháři dynamické argument. <xref:System.Activities.Statements.Assign> Aktivita se používá jako příklad.

3.  Klikněte na levý výraz editor v Návrhář aktivity pro <xref:System.Activities.Statements.Assign> aktivity.

     Šedé vodoznak řetězce  **\<k >** a  **\<zadejte výraz jazyka Visual Basic >** jsou výchozí textové řetězce pro výraz editory v <xref:System.Activities.Statements.Assign> aktivity.

4.  Zadejte výraz. Pokud zadáte řetězec, ujistěte se, že jste put řetězec v uvozovkách. Pokud se rozhodnete vázat argument výrazu proměnné, nechte uvozovek.

     Až budete hotoví, vyberte oblast nebo oblasti mimo Editor výraz přesune fokus na jinou část návrháře. Fokus s posunem způsobí, že kompilátor ověření výrazu, jak je popsáno výše.

     Alternativní způsob zadání nebo úpravě výrazu je klikněte na tlačítko se třemi tečkami vedle názvu vlastnosti v tabulce vlastností. Otevře se výběr se třemi tečkami **Editor výrazů** jako dialogové okno.

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.View.ExpressionTextBox>