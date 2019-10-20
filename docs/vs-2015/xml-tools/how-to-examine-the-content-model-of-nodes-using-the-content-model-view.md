---
title: 'Postupy: prohlédnutí modelu obsahu uzlů pomocí zobrazení modelu obsahu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670859"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Postupy: prohlédnutí modelu obsahu uzlů pomocí zobrazení modelu obsahu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje, jak prozkoumat uzly pomocí [zobrazení modelu obsahu](../xml-tools/content-model-view.md).

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>Vytvoření nového souboru XSD a zobrazení kořenového prvku v zobrazení modelu obsahu

1. Vytvoří nový soubor schématu XML.

2. Klikněte na **použít editor XML k zobrazení a úpravě základního souboru schématu XML** v zobrazení Start.

3. Zkopírujte ukázkový kód schématu XML z [ukázkového schématu XML: schéma nákupu](../xml-tools/sample-xsd-file-purchase-order-schema.md) a vložte jej pro nahrazení kódu, který byl přidán do nového souboru XSD ve výchozím nastavení.

4. Vyberte prvek `purchaseOrder` v Průzkumníku schémat tak, že kliknete pravým tlačítkem myši na prvek `purchaseOrder` v editoru XML a vyberete **Zobrazit v PRŮZKUMNÍKOVI XML**.

5. V Průzkumníku XML klikněte pravým tlačítkem na `purchaseOrder` a vyberte **Zobrazit v zobrazení modelu obsahu**.

     Zobrazení Content model zobrazuje `purchaseOrder` element na jeho návrhové ploše.

6. Rozbalte uzly `shipTo`, `billTo` a `items` buď Poklikáním na jednotlivé uzly, nebo kliknutím na dvojitou šipku napravo od každého uzlu.

     Uzly prvku `purchaseOrder` jsou nyní rozbaleny a můžete zobrazit model obsahu elementu.

7. V rámci `purchaseOrder` elementu klikněte na libovolný uzel a podívejte se na panel s popisem cesty, kde se zobrazí informace o tom, kde se v sadě schémat nachází vybraný uzel.

8. Klikněte na tlačítko **zobrazit dokumentaci** na panelu nástrojů XSD a přepněte documenation. Můžete také kliknout pravým tlačítkem na návrhovou plochu a přepínat dokumentaci.

9. Rick – klikněte na uzel `purchaseOrder` a vyberte **vytvořit ukázkový kód XML** pro zobrazení dokumentu instance XML.
