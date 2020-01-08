---
title: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2049b8da1caa4e0af0afc52aec6e75f499d85b8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592812"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Postupy: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML

Toto téma vysvětluje, jak přidat uzly do [pracovního prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md) z **Průzkumníka schémat XML**. Toho lze dosáhnout přetažením uzlů z **Průzkumníka schémat XML** do zobrazení návrháře XSD nebo pomocí místní nabídky **Průzkumníka schémat XML** . Můžete také přidat uzly zvýrazněné jako výsledek hledání provedeného **průzkumníkem schémat XML**. Další informace najdete v tématu [Postup: Přidání uzlů výsledků hledání sad schémat do pracovního prostoru](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Do [pracovního prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md)lze přidat pouze globální uzly.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Přidání uzlů pomocí místní nabídky Průzkumníka XML

1. Postupujte podle kroků v tématu [Postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klikněte pravým tlačítkem na uzel `PurchaseOrderType` v Průzkumníku XSD. **V zobrazení grafu vyberte Zobrazit**.

     Uzel `purchaseOrderType` se zobrazí na návrhové ploše zobrazení grafu.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Přetažení uzlu do zobrazení

1. V zobrazení grafu klikněte pravým tlačítkem myši na uzel `PurchaseOrderType`. **V Průzkumníku schémat XML vyberte Zobrazit**.

     Uzel je zvýrazněn v **Průzkumníku schémat XML**.

2. Klikněte pravým tlačítkem na uzel `PurchaseOrderType` v **Průzkumníku schémat XML** a vyberte **Zobrazit všechny odkazy**.

     Uzel `purchaseOrder` je zvýrazněný.

3. Přetáhněte uzel `purchaseOrder` do zobrazení grafu.

     Uzel `purchaseOrder` a uzel `PurchaseOrderType` se zobrazí vedle sebe na návrhové ploše zobrazení grafu. Vzhledem k tomu, že se tyto dva uzly vztahují (`purchaseOrder` prvek je typu `PurchaseOrderType`), je mezi nimi vykreslena šipka.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Přidání uzlů pomocí možnosti vyhledávání v Průzkumníku schémat

1. Do textového pole Hledat na panelu nástrojů v [Průzkumníkovi XML](../xml-tools/xml-schema-explorer.md) zadejte "PurchaseOrder" a klikněte na tlačítko Hledat.

     ![Hledání klíčového slova Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearch.gif)

     Výsledky hledání jsou zvýrazněny v **Průzkumníku schémat XML** a označené značkami na svislém posuvníku.

2. Do pracovního prostoru přidejte výsledky hledání kliknutím na tlačítko **Přidat zvýrazněné uzly do pracovního prostoru** v podokně souhrnné výsledky.

     ![Výsledek hledání v Průzkumníkovi schémat XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Uzel `purchaseOrder` a uzel `PurchaseOrderType` se zobrazí vedle sebe na návrhové ploše [zobrazení grafu](../xml-tools/graph-view.md). Vzhledem k tomu, že se tyto dva uzly vztahují (`purchaseOrder` prvek je typu `PurchaseOrderType`), je mezi nimi vykreslena šipka.

## <a name="see-also"></a>Viz také:

- [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)
