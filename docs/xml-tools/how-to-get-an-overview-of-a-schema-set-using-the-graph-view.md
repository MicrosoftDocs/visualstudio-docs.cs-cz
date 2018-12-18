---
title: 'Postupy: získání přehledu o sadě schémat pomocí zobrazení grafu ve schématu XML návrháře'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 004d40992e24f0df651d93b43761add1d2efa673
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381417"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Postupy: Získejte přehled o schéma, nastavte pomocí zobrazení grafu

Toto téma popisuje způsob použití [zobrazení grafu](../xml-tools/graph-view.md) zobrazíte souhrnný přehled uzly v sadě schémat a vztahy mezi uzly.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvořte nový soubor XSD a zobrazte kořenový element v zobrazení modelu obsahu

1.  Vytvořte nový soubor XML schéma a soubor uložte jako *Relationships.xsd*.

2.  Klikněte na tlačítko **pomocí editoru XML k zobrazení a úpravě základního souboru schématu XML** odkaz na zobrazení spuštění.

3.  Zkopírujte ukázkový kód XML schéma z [ukázky XML schématu: relace](../xml-tools/sample-xsd-file-relationships.md) a vložte ji nahradit kód, který byl přidán do nového souboru XSD ve výchozím nastavení.

4.  Klikněte pravým tlačítkem na libovolné místo v editoru XML a vyberte **Návrhář zobrazení**.

5.  Vyberte zobrazení grafu z **XSD nástrojů**.

6.  Vyberte **schématu nastavení** uzlu **Průzkumníka schémat XML** a přetáhněte uzel na návrhové ploše zobrazení grafu. Měli byste vidět všechny globální uzly a šipky spojující uzly, které mají relace.

     ![Zobrazení grafu](../xml-tools/media/relationshipingraphview.gif)

7.  Klikněte na libovolný uzel na návrhové ploše a podívejte se na panelu s popisem cesty chcete zobrazit, kde se nachází na vybraný uzel v sadě schémat.

8.  Rick klepněte na žádný uzel prvku na návrhové ploše a vyberte **generovat ukázkové XML** zobrazíte instance dokumentu XML.