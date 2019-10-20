---
title: 'Postupy: získání přehledu o sadě schémat pomocí zobrazení grafu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670893"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Postupy: získání přehledu o sadě schémat pomocí zobrazení grafu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak použít [zobrazení grafu](../xml-tools/graph-view.md) k zobrazení vysokého zobrazení uzlů v sadě schémat a vztahů mezi uzly.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvoření nového souboru XSD a zobrazení kořenového prvku v zobrazení modelu obsahu

1. Vytvořte nový soubor schématu XML a uložte soubor jako Relationships. xsd.

2. Kliknutím na **použít editor XML zobrazíte a upravíte odkaz základní soubor XML schématu** v zobrazení Start.

3. Zkopírujte ukázkový kód schématu XML z [ukázkového schématu XML: relace](../xml-tools/sample-xsd-file-relationships.md) a vložte jej pro nahrazení kódu, který byl přidán do nového souboru XSD ve výchozím nastavení.

4. Klikněte pravým tlačítkem na libovolné místo v editoru XML a vyberte **zobrazení Návrhář**.

5. Vyberte zobrazení grafu z panelu nástrojů XSD.

6. V Průzkumníku schémat XML vyberte uzel **sada schémat** a přetáhněte uzel pro návrh suface zobrazení grafu. Měli byste vidět všechny globální uzly a šipky připojující uzly, které mají relace.

     ![Zobrazení grafu](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Klikněte na libovolný uzel na návrhové ploše a podívejte se na panel s popisem cesty a zjistěte, kde se vybraný uzel nachází v sadě schémat.

8. Rick – klikněte na libovolný uzel elementu na povrchu desing a vyberte **vytvořit ukázkový kód XML** pro zobrazení dokumentu instance XML.
