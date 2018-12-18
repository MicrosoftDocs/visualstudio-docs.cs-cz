---
title: Průzkumník schémat XML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32116de7bb88fe937980b02e1789830a27ca36b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845872"
---
# <a name="xml-schema-explorer"></a>Průzkumník schémat XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Průzkumníka schémat XML je součástí sady Microsoft Visual Studio a Editor souborů XML umožňují pracovat s schémat schématu XML definice jazyk (XSD). Když otevřete soubor schématu XML **schéma nastaveno** uzel se zobrazí v Průzkumník schémat XML. Všech součástí, importované nebo Předefinovaná schémata pro cílový soubor, stejně jako všechny soubory, které jsou odkazovány prostřednictvím `include` nebo `import` příkazu se zobrazí také v Průzkumník schémat XML.  
  
 Průzkumníka schémat XML lze provádět následující akce:  
  
- Získejte rychlý přehled o sadě schémat.  
  
- Procházení a přejděte strom.  
  
- Proveďte – klíčové slovo a specifické pro schéma vyhledávání. Další informace najdete v tématu [hledání sady schématu](../xml-tools/searching-the-schema-set.md).  
  
- Přidat do zobrazení grafu nebo zobrazení obsahu Modle výsledky hledání  
  
- Seřaďte podle pořadí dokumentů, typ nebo název stromu. Další informace najdete v tématu [řazení, filtrování a seskupování](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
- Otevření editoru XML a přejděte do umístění kódu v souboru XSD. Další informace najdete v tématu [integrace s editorem XML](../xml-tools/integration-with-xml-editor.md).  
  
- Generovat ukázkový soubor XML pro globální prvky.  
  
  Průzkumníka schémat XML poskytuje hierarchická zobrazení schématu nastavit pomocí stromového zobrazení. Průzkumníka schémat XML také poskytuje vyhledávání, filtrování, navigace a řazení. Pro přístup k Průzkumníka schémat XML, proveďte jednu z následujících akcí:  
  
- Pokud používáte [zobrazení Start](../xml-tools/start-view.md), klikněte na tlačítko **Průzkumníka schémat XML** odkaz.  
  
- Pokud používáte [zobrazení grafu](../xml-tools/graph-view.md) nebo [zobrazení modelu obsahu](../xml-tools/content-model-view.md) a uzlů ve vašem pracovním prostoru, použijte v místní nabídce vyberte Průzkumníka schémat XML.  
  
- Můžete také vybrat Explorerfrom schématu XML **zobrazení** nabídky.  
  
- Můžete přistupovat Explorerfrom schématu XML soubor .vb, který má literál XML Visual Basic přidružené k souboru XSD. Abychom viděli toto schéma, nastavte v Průzkumník schémat XML, klikněte pravým tlačítkem na uzel XML v literálu XML nebo import oboru názvů XML a vyberte **zobrazit v Průzkumníkovi schémat** příkazu. Další informace najdete v tématu [integrace z literálů XML s Průzkumníkem schémat XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Stromové zobrazení  
 Průzkumníka schémat XML zobrazí informace o sadě předem kompilovaných schématu ve stromové struktuře. Stromové struktury je uspořádaný následujícím způsobem:  
  
- Na nejvyšší úrovni je schéma, nastavte uzel.  
  
- Na druhé úrovni obsahuje obory názvů.  
  
- Na třetí úrovni obsahuje soubory.  
  
- Čtvrtý úrovni obsahuje globální uzly. To může zahrnovat prvky, skupiny, komplexní typy, jednoduché typy, atributy, skupiny atributů a `include`, `import`, a `redefine` příkazy.  
  
  Následuje příklad stromové struktury:  
  
  ![Průzkumník schémat XML](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Výběr a aktivace  
 Pokud chcete zvýraznit a vyberte uzel, klikněte na jednou Průzkumník schémat.  
  
 Pokud chcete aktivovat uzel, poklepejte na něj nebo stiskněte klávesu **Enter** při výběru uzlu.  
  
-   Aktivace uzel otevře soubor, ve kterém je definována tento uzel (Pokud soubor ještě není otevřený) a vybere uzel v souboru.  
  
-   Aktivace uzel souboru (Pokud není již otevřený), otevře se vybraný soubor a zvýrazní `<schema>` uzlu.  
  
-   Aktivace SchemaSet nebo uzel oboru názvů nemá žádný účinek.  
  
## <a name="draging-and-dropping-nodes"></a>Draging a vyřazení uzlů  
 Můžete přetáhnout a globální uzly, uzly souborových a uzly oboru názvů do zobrazení o návrháři XSD. Pokud je aktuální zobrazení nastaveno [zobrazení Start](../xml-tools/start-view.md), tažení uzlu k zobrazení se otevře [zobrazení grafu](../xml-tools/graph-view.md). Pokud je aktuální zobrazení nastaveno [zobrazení modelu obsahu](../xml-tools/content-model-view.md) nebo zobrazení grafu, zobrazení se nezmění, pokud je vyřadit uzel problém napravit.  
  
 Odstranit soubory v zobrazení přidá všechny globální uzly v souboru, který má [pracovní prostor návrháře XSD](../xml-tools/xml-schema-designer-workspace.md). Vyřazení obory názvů pro zobrazení přidá všechny globální uzly v oboru názvů do pracovního prostoru. Pracovní prostor se sdílí mezi všech zobrazení.  
  
 Je nelze přetáhnout myší místní uzly nebo importy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Hledání v sadě schémat](../xml-tools/searching-the-schema-set.md)  
  
-   [Řazení, filtrování a seskupování](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Místní nabídky](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integrace literálů XML s Průzkumníkem schémat XML](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání uzlů do pracovního prostoru z Průzkumníka schémat XML](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)







