---
title: Přidat XML schématu sady vyhledávání výsledek uzly do pracovního prostoru
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 04e74057bd059c82010678b7de571ff180e7fbfe
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751907"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Postupy: přidání schématu sady vyhledávání výsledek uzlů do pracovního prostoru

Toto téma vysvětluje, jak přidat uzly, které jsou vyznačené na **Explorer schématu XML** jako výsledky hledání – klíčové slovo v pracovním prostoru.

> [!NOTE]
> Pouze globální uzly mohou být přidány do [prostoru](../xml-tools/xml-schema-designer-workspace.md).


 Tento příklad používá vzorku [zakoupit pořadí schématu](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Chcete-li přidat schématu nastavit výsledek uzly

1.  Postupujte podle kroků v [postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  Zadejte do vyhledávacího pole text "purchaseOrder" [XML Explorer](../xml-tools/xml-schema-explorer.md) panelu nástrojů a klikněte na tlačítko Hledat.

     ![Hledání klíčových slov Explorer schématu XML](../xml-tools/media/schemaexplorersearch.gif)

     Výsledky hledání jsou vyznačené na **Explorer schématu XML** a označeny rysky svislém posuvníku.

3.  Výsledky hledání přidat do pracovního prostoru kliknutím **přidat zvýrazněné uzly do pracovního prostoru** stisknutí tlačítka na panelu shrnutí výsledků.

     ![Výsledek hledání Explorer schématu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Uzlu a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové plochy [zobrazení grafu](../xml-tools/graph-view.md). Protože se vztahují dva uzly ( `purchaseOrder` element je `PurchaseOrderType` typu), šipka vykreslením mezi nimi.