---
title: 'Postupy: přidání uzlů do pracovního prostoru z Průzkumníka schémat XML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b5a5749-9693-4b29-b0c2-8e07e0e55514
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6ef4e4e019406d9c317ccd90eabcb89e25a6f36
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220100"
---
# <a name="how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer"></a>Postupy: přidání uzlů do pracovního prostoru z Průzkumníka schémat XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Toto téma vysvětluje, jak přidat uzly do [pracovní prostor návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md) z Průzkumníka schémat XML. Toho lze dosáhnout pomocí přetahování uzlů z Průzkumníka schémat XML do zobrazení o návrháři XSD nebo pomocí místní nabídky Průzkumníka schémat XML. Můžete také přidat uzly, kteří jsou zvýrazněni v důsledku vyhledávání prováděné Průzkumníka schémat XML. Další informace najdete v tématu [postupy: přidání nastavení uzlů výsledků hledání schémat do pracovního prostoru](../xml-tools/how-to-add-schema-set-search-result-nodes-to-the-workspace.md).  
  
> [!NOTE]
>  Lze přidat pouze globální uzly [pracovní prostor návrháře schémat XML](../xml-tools/xml-schema-designer-workspace.md).  
  
### <a name="to-add-nodes-through-the-xml-explorer-context-menu"></a>Přidání uzlů do místní nabídky Průzkumníka XML  
  
1.  Postupujte podle kroků v [postupy: vytvoření a úprava souboru schématu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzlu XSD Explorer. Vyberte **zobrazit v zobrazení grafu**.  
  
     `purchaseOrderType` Uzel se objeví na návrhové ploše zobrazení grafu.  
  
### <a name="to-drag-and-drop-a-node-on-to-a-view"></a>Můžete přetáhnout uzel k zobrazení  
  
1.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzel v zobrazení grafu. Vyberte **zobrazit v Průzkumníkovi schémat XML**.  
  
     Uzel je zvýrazněn v Průzkumník schémat XML.  
  
2.  Klikněte pravým tlačítkem na `PurchaseOrderType` uzlu Průzkumníka schémat XML a vyberte **zobrazit všechny odkazy**.  
  
     `purchaseOrder` Je zvýrazněn uzel.  
  
3.  Přetáhněte `purchaseOrder` uzel k zobrazení grafu.  
  
     `purchaseOrder` Uzlu a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové ploše zobrazení grafu. Protože rizikoví jsou dva uzly ( `purchaseOrder` element má `PurchaseOrderType` typu), šipka vykreslením mezi nimi.  
  
### <a name="to-add-nodes-using-the-schema-explorer-search-capability"></a>Chcete-li přidat uzly pomocí možnosti vyhledávání Průzkumník schémat  
  
1.  Do textového pole hledání zadejte "purchaseOrder" [Průzkumník XML](../xml-tools/xml-schema-explorer.md) nástrojů a klikněte na tlačítko Hledat.  
  
     ![Hledání klíčových slov Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
     Výsledky hledání jsou zvýrazněné Průzkumníka schémat XML a označeny dílků na svislý posuvník.  
  
2.  Výsledky hledání do pracovního prostoru přidat kliknutím **přidá zvýrazněné uzly do pracovního prostoru** tlačítko na panelu souhrnu výsledků.  
  
     ![Výsledek hledání Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
     `purchaseOrder` Uzlu a `PurchaseOrderType` uzel se zobrazí vedle sebe na návrhové ploše [zobrazení grafu](../xml-tools/graph-view.md). Protože se týkají dva uzly ( `purchaseOrder` element má `PurchaseOrderType` typu), šipka vykreslením mezi nimi.  
  
## <a name="see-also"></a>Viz také  
 [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)



