---
title: 'Postupy: Zobrazení existujících typů (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04b109bfa5741a5d4349f2d503bd1c821e19029d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588704"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Postup: Zobrazení existujících typů v Návrháři tříd

Chcete-li zobrazit existující typ a jeho členy, přidejte jeho obrazec do diagramu třídy.

Můžete vidět místní a odkazované typy. V aktuálně otevřeném projektu existuje místní typ a je pro čtení i zápis. Odkazovaný typ existuje v jiném projektu nebo v odkazovaném sestavení a je jen pro čtení.

Pokud chcete navrhnout nové typy v diagramech tříd, [přečtěte si postup: Vytvoření typů pomocí Návrháře tříd](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Zobrazení typů v projektu v diagramu tříd

1. Z projektu v **Průzkumníku řešení**otevřete existující soubor diagramu tříd (.cd). Nebo pokud neexistuje žádný diagram tříd, přidejte do projektu nový diagram tříd. Postup: [Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md).

2. Z projektu v **Průzkumníku řešení**přetáhněte soubor zdrojového kódu do diagramu třídy.

    > [!NOTE]
    > Pokud vaše řešení obsahuje projekt, který sdílí kód mezi více aplikacemi, můžete přetáhnout soubory nebo kód do diagramu třídy pouze z těchto zdrojů:
    >
    > - Projekt aplikace, který obsahuje diagram
    > - Sdílený projekt, který byl importován projektem aplikace
    > - Odkazovaný projekt
    > - Sestavení

    Tvary, které představují typy definované v souboru zdrojového kódu, se zobrazí v diagramu na pozici, kam jste soubor přetáhli.

Typy v projektu můžete také zobrazit přetažením jednoho nebo více typů z uzlu projektu v **zobrazení třídy** do diagramu třídy.

> [!TIP]
> Pokud **zobrazení tříd** není otevřené, otevřete zobrazení tříd **z** nabídky **Zobrazení.**

Chcete-li zobrazit typy ve výchozích umístěních v diagramu, vyberte jeden nebo více typů v **zobrazení tříd ,** klepněte pravým tlačítkem myši na vybrané typy a zvolte Zobrazit diagram **tříd**.

> [!NOTE]
> Pokud v projektu existuje zavřený diagram tříd obsahující daný typ, diagram tříd se otevře a zobrazí tvar typu. Pokud však v projektu neexistuje žádný diagram třídy obsahující typ, **Návrhář třídy** vytvoří v projektu nový diagram třídy a otevře jej pro zobrazení typu.

Při prvním zobrazení typu v diagramu se jeho tvar ve výchozím nastavení zobrazí sbalený. Tvar můžete rozbalit a zobrazit jeho obsah.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Zobrazení obsahu projektu v diagramu třídy

V **Průzkumníku řešení** nebo **zobrazení tříd**klepněte pravým tlačítkem myši na projekt a zvolte **Zobrazit**a pak zvolte Zobrazit **diagram tříd**. Vytvoří se automaticky vyplněný diagram tříd.

## <a name="see-also"></a>Viz také

- [Postup: Zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Postup: Přizpůsobení diagramů tříd](how-to-customize-class-diagrams.md)
- [Zobrazování typů a vztahů](designing-and-viewing-classes-and-types.md)
