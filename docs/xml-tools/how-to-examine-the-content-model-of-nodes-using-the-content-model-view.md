---
title: Kontrola uzlů pomocí zobrazení modelu obsahu v Návrháři schématu XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5a7e6e311a4fbd02973edf94c6eb117f69d6cea
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592708"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Postupy: prohlédnutí modelu obsahu uzlů pomocí zobrazení modelu obsahu

Toto téma popisuje, jak prozkoumat uzly pomocí [zobrazení modelu obsahu](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvoření nového souboru XSD a zobrazení kořenového prvku v zobrazení modelu obsahu

1. Vytvoří nový soubor schématu XML.

2. Klikněte na **použít editor XML k zobrazení a úpravě základního souboru schématu XML** v zobrazení Start.

3. Zkopírujte ukázkový kód schématu XML z [ukázkového schématu XML: schéma nákupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) a vložte jej pro nahrazení kódu, který byl přidán do nového souboru XSD ve výchozím nastavení.

4. Vyberte prvek `purchaseOrder` v Průzkumníku schémat tak, že kliknete pravým tlačítkem myši na prvek `purchaseOrder` v editoru XML a vyberete **Zobrazit v PRŮZKUMNÍKOVI XML**.

5. V Průzkumníku XML klikněte pravým tlačítkem na `purchaseOrder` a vyberte **Zobrazit v zobrazení modelu obsahu**.

     Zobrazení Content model zobrazuje `purchaseOrder` element na jeho návrhové ploše.

6. Rozbalte uzly `shipTo`, `billTo`a `items` buď Poklikáním na jednotlivé uzly, nebo kliknutím na dvojitou šipku napravo od každého uzlu.

     Uzly prvku `purchaseOrder` jsou nyní rozbaleny a můžete zobrazit model obsahu elementu.

7. V rámci `purchaseOrder` elementu klikněte na libovolný uzel a podívejte se na panel s popisem cesty, kde se zobrazí informace o tom, kde se v sadě schémat nachází vybraný uzel.

8. Kliknutím na tlačítko **zobrazit dokumentaci** na panelu nástrojů XSD přepnete dokumentaci. Můžete také kliknout pravým tlačítkem na návrhovou plochu a přepínat dokumentaci.

9. Klikněte pravým tlačítkem myši na uzel `purchaseOrder` a vyberte **vytvořit ukázkový kód XML** . tím se zobrazí dokument instance XML.
