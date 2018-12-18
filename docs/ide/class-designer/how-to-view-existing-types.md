---
title: 'Postupy: Zobrazení existujících typů (návrhář tříd)'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f477f64188c9592db65d0a82c8a1b8b3ec5b776
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33956650"
---
# <a name="how-to-view-existing-types-in-class-designer"></a>Postupy: zobrazení existujících typů v Návrháři tříd

Pokud chcete zobrazit stávající typ a její členy, přidejte do diagramu tříd jeho tvaru.

Můžete vidět místní a odkazované typy. V aktuálně otevřeném projektu existuje místní typ a je pro čtení i zápis. Odkazovaný typ existuje v jiném projektu nebo v odkazovaném sestavení a je jen pro čtení.

Postup návrhu nové typy v diagramech tříd, najdete v [postupy: vytváření typů pomocí návrháře tříd](how-to-create-types.md).

## <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Zobrazení typů v projektu v diagramu tříd

1.  Z projektu v **Průzkumníku**, otevřete soubor, diagram (.cd) třída. Nebo pokud neexistuje žádný diagram tříd, přidejte do projektu nový diagram tříd. V tématu [postupy: Přidání diagramů tříd do projektů](how-to-add-class-diagrams-to-projects.md).

2.  Z projektu v **Průzkumníku**, přetáhněte soubor zdrojového kódu do diagramu tříd.

    > [!NOTE]
    > Pokud má vaše řešení projekt, který sdílí kód mezi více aplikacemi, můžete přetáhnout soubory nebo kód na diagramu tříd pouze z těchto zdrojů:
    >
    > - Projekt aplikace, který obsahuje diagram
    > - Sdílený projekt, který byl importován pomocí projekt aplikace
    > - Odkazovaný projekt
    > - Sestavení

    Tvary, které představují typy definované v souboru zdrojového kódu, se zobrazí v diagramu na pozici, kam jste soubor přetáhli.

Můžete také zobrazit typy v projektu přetáhněte jeden nebo více typů v uzlu projektu **zobrazení tříd** na diagramu tříd.

> [!TIP]
> Pokud **zobrazení tříd** není otevřený, otevřete **zobrazení tříd** z **zobrazení** nabídky.

Chcete-li zobrazit typy v výchozí umístění v diagramu, vyberte jeden nebo více typů v **zobrazení tříd**, klikněte pravým tlačítkem na vybrané typy a zvolit **zobrazení diagramu tříd**.

> [!NOTE]
> Pokud v projektu existuje zavřený diagram tříd obsahující daný typ, diagram tříd se otevře a zobrazí tvar typu. Pokud ale diagram žádná třída obsahující typ existuje v projektu **návrhář tříd** vytvoří nový diagram – třída v projektu a otevře ji zobrazíte typu.

Při prvním zobrazení typu v diagramu se jeho tvar ve výchozím nastavení zobrazí sbalený. Tvar můžete rozbalit a zobrazit jeho obsah.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>K zobrazení obsahu projektu v diagramu tříd

V **Průzkumníku řešení** nebo **zobrazení tříd**, klikněte pravým tlačítkem na projekt a vyberte možnost **zobrazení**, zvolte **zobrazení diagramu tříd**. Vytvoří se automaticky vyplněný diagram tříd.

## <a name="see-also"></a>Viz také

- [Postupy: zobrazení dědičnosti mezi typy](how-to-view-inheritance-between-types.md)
- [Postupy: přizpůsobení diagramů tříd](how-to-customize-class-diagrams.md)
- [Zobrazování typů a vztahů](viewing-types-and-relationships.md)