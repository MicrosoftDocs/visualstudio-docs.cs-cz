---
title: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 751e291188e6357343936d61d56f07bd86f97eaf
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816394"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Postupy: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML

Toto téma vysvětluje, jak přidat uzly do [pracovního prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md) z **Průzkumníka schémat XML**. Toho lze dosáhnout přetažením uzlů z **Průzkumníka schémat XML** do zobrazení návrháře XSD nebo pomocí místní nabídky **Průzkumníka schémat XML** . Můžete také přidat uzly zvýrazněné jako výsledek hledání provedeného **průzkumníkem schémat XML**. Další informace najdete v tématu [Postup: Přidání uzlů výsledků hledání sad schémat do pracovního prostoru](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Do [pracovního prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md)lze přidat pouze globální uzly.

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Přidání uzlů pomocí místní nabídky Průzkumníka XML

1. Postupujte podle kroků v tématu [Postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. Klikněte pravým tlačítkem na `PurchaseOrderType` uzel v PRŮZKUMNÍKU XSD. **V zobrazení grafu vyberte Zobrazit**.

     `purchaseOrderType`Uzel se zobrazí na návrhové ploše zobrazení grafu.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Přetažení uzlu do zobrazení

1. V zobrazení grafu klikněte pravým tlačítkem myši na `PurchaseOrderType` uzel. **V Průzkumníku schémat XML vyberte Zobrazit**.

     Uzel je zvýrazněn v **Průzkumníku schémat XML**.

2. Klikněte pravým tlačítkem na `PurchaseOrderType` uzel v **Průzkumníku schémat XML** a vyberte **Zobrazit všechny odkazy**.

     `purchaseOrder`Uzel je zvýrazněný.

3. Přetáhněte `purchaseOrder` uzel na zobrazení grafu.

     `purchaseOrder`Uzel a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové ploše zobrazení grafu. Vzhledem k tomu, že oba uzly jsou související ( `purchaseOrder` element je `PurchaseOrderType` typu), je mezi nimi vykreslena šipka.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Přidání uzlů pomocí možnosti vyhledávání v Průzkumníku schémat

1. Do textového pole Hledat na panelu nástrojů v [Průzkumníkovi XML](../xml-tools/xml-schema-explorer.md) zadejte "PurchaseOrder" a klikněte na tlačítko Hledat.

     ![Hledání klíčového slova Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearch.gif)

     Výsledky hledání jsou zvýrazněny v **Průzkumníku schémat XML** a označené značkami na svislém posuvníku.

2. Do pracovního prostoru přidejte výsledky hledání kliknutím na tlačítko **Přidat zvýrazněné uzly do pracovního prostoru** v podokně souhrnné výsledky.

     ![Výsledek hledání v Průzkumníkovi schémat XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder`Uzel a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové ploše [zobrazení grafu](../xml-tools/graph-view.md). Vzhledem k tomu, že oba uzly jsou související ( `purchaseOrder` element je `PurchaseOrderType` typu), je mezi nimi vykreslena šipka.

## <a name="see-also"></a>Viz také:

- [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)
