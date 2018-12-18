---
title: Hledání v sadě schémat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 885797e319652aaf9573b0c171318506518f82df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204201"
---
# <a name="searching-the-schema-set"></a>Hledání v sadě schémat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Průzkumníka schémat XML umožňuje hledat schéma nastavit následujícími způsoby:  
  
-   Hledání klíčových slov.  
  
-   Hledání podle schématu.  
  
## <a name="keyword-search"></a>Hledání klíčových slov  
 Provádět vyhledávání – klíčové slovo tak, že zadáte podřetězce v **hledání SchemaSet** textového pole panelu nástrojů Průzkumník schémat XML.  
  
 ![Hledání klíčových slov Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")  
  
 Průzkumníka schémat XML vyhledá schéma, nastavte následující:  
  
-   Žádné `name` nebo `ref` atributy, které odpovídají zadané klíčové slovo. To umožňuje najít prvky, atributy, typy, a tak dále podle názvu.  
  
-   `schemaLocation` Atributy #include.  
  
-   `namespace` Atributy příkazy pro import.  
  
## <a name="schema-specific-search"></a>Konkrétní schéma vyhledávání  
 Průzkumníka schémat XML také zahrnuje integrované hledání, kterým můžete přistupovat pomocí místní nabídky Průzkumníka schémat XML. Další informace o dostupných kontextové nabídky, naleznete v tématu [kontextové nabídky](../xml-tools/context-menus-xml-schema-explorer.md). Můžete také provádět konkrétní schéma vyhledávání ze zobrazení spuštění; Další informace najdete v části "Nastavit informace o schématu" v [zobrazení Start](../xml-tools/start-view.md) tématu.  
  
## <a name="displaying-and-navigating-search-results"></a>Zobrazení a navigaci výsledky hledání  
 Po dokončení hledání v podokně souhrnných výsledků se přidá na panel nástrojů s výsledky hledání. Výsledky hledání jsou také zvýrazněna v Průzkumník schémat XML a označeny dílků na svislý posuvník. Výsledky hledání můžete Navigovat pomocí **přejít k další výsledek hledání** a **přejít na předchozí výsledky hledání** tlačítka na panelu souhrnných výsledků z panelu nástrojů Průzkumník schémat XML; pomocí klávesových zkratek F3 a Shift + F3 nebo kliknutím značek na posuvníku.  
  
 Výsledky hledání do pracovního prostoru můžete přidat kliknutím **přidá zvýrazněné uzly do pracovního prostoru** tlačítko na panelu souhrnu výsledků.  
  
 ![Výsledek hledání Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")  
  
## <a name="clearing-search-results"></a>Výsledky hledání vymazání  
 Vymazat výsledky hledání, klikněte na tlačítko **x** stisknutí tlačítka na panelu souhrnných výsledků z panelu hledání v Průzkumníkovi schémat XML.  
  
## <a name="see-also"></a>Viz také  
 [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)



