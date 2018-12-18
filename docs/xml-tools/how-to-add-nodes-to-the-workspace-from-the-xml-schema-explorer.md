---
title: 'Postupy: přidání uzlů do pracovního prostoru z Průzkumníka schématu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e1f5821d3a4207d89eb62b9344cff967c73b536
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752050"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Postupy: přidání uzlů do pracovního prostoru z Průzkumníka schématu XML

Toto téma vysvětluje, jak přidat uzly do [Návrhář schématu XML prostoru](../xml-tools/xml-schema-designer-workspace.md) z **Explorer schématu XML**. Toho lze dosáhnout pomocí přetahování uzly z **Explorer schématu XML** do zobrazení o návrháři XSD, nebo pomocí **Průzkumník schématu XML** kontextové nabídky. Můžete také přidat uzly, kteří jsou zvýrazněni v důsledku vyhledávání provádí **Explorer schématu XML**. Další informace najdete v tématu [postupy: přidání schématu sady vyhledávání výsledek uzlů do pracovního prostoru](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).

> [!NOTE]
> Pouze globální uzly mohou být přidány do [prostoru Návrhář schématu XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Chcete-li přidat uzly prostřednictvím místní nabídku Průzkumníka XML

1.  Postupujte podle kroků v [postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzlu v Průzkumníku XSD. Vyberte **zobrazit v zobrazení grafu**.

     `purchaseOrderType` Uzel se objeví na plochu návrháře zobrazení grafu.

## <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Přetáhnout uzel k zobrazení

1.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzel v zobrazení grafu. Vyberte **zobrazit v Průzkumníku schématu XML**.

     Uzel je označený na **Explorer schématu XML**.

2.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzlu **Explorer schématu XML** a vyberte **zobrazit všechny odkazy**.

     `purchaseOrder` Zvýrazní se uzel.

3.  Přetáhněte `purchaseOrder` uzel k zobrazení grafu.

     `purchaseOrder` Uzlu a `PurchaseOrderType` uzlu zobrazí vedle sebe na plochu návrháře zobrazení grafu. Protože se vztahují dva uzly ( `purchaseOrder` element je `PurchaseOrderType` typu), šipka vykreslením mezi nimi.

## <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Přidání uzlů pomocí funkce vyhledávání Explorer schématu

1.  Zadejte do vyhledávacího pole text "purchaseOrder" [XML Explorer](../xml-tools/xml-schema-explorer.md) panelu nástrojů a klikněte na tlačítko Hledat.

     ![Hledání klíčových slov Explorer schématu XML](../xml-tools/media/schemaexplorersearch.gif)

     Výsledky hledání jsou vyznačené na **Explorer schématu XML** a označeny rysky svislém posuvníku.

2.  Výsledky hledání přidat do pracovního prostoru kliknutím **přidat zvýrazněné uzly do pracovního prostoru** stisknutí tlačítka na panelu shrnutí výsledků.

     ![Výsledek hledání Explorer schématu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Uzlu a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové plochy [zobrazení grafu](../xml-tools/graph-view.md). Protože se vztahují dva uzly ( `purchaseOrder` element je `PurchaseOrderType` typu), šipka vykreslením mezi nimi.

## <a name="see-also"></a>Viz také:

- [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)