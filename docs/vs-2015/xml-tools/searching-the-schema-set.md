---
title: Hledání sady schémat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ec1395e0-d03c-4130-810d-f2db656937bd
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e3a8563d5e2cd29c9c521761498d7ef87b7cbab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656161"
---
# <a name="searching-the-schema-set"></a>Hledání v sadě schémat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Průzkumník schémat XML umožňuje vyhledat sadu schémat následujícími způsoby:

- Hledání klíčových slov

- Hledání specifické pro schéma.

## <a name="keyword-search"></a>Hledání klíčových slov
 Hledání klíčových slov provedete tak, že do textového pole **Hledat schemaSet** v panelu nástrojů Průzkumníka schémat XML zadáte podřetězec.

 ![Hledání klíčového slova Průzkumníka schémat XML](../xml-tools/media/schemaexplorersearch.gif "SchemaExplorerSearch")

 Průzkumník schémat XML prohledává sadu schémat pro následující:

- Všechny atributy `name` nebo `ref`, které odpovídají zadanému klíčovému slovu. To umožňuje najít prvky, atributy, typy a tak dále podle názvu.

- Atributy `schemaLocation` příkazů include.

- Atributy `namespace` příkazů importu.

## <a name="schema-specific-search"></a>Hledání specifické pro schéma
 Průzkumník schémat XML také obsahuje Vestavěná hledání, ke kterým můžete přistupovat pomocí místní nabídky Průzkumníka schémat XML. Další informace o dostupných kontextových nabídkách naleznete v tématu [kontextové nabídky](../xml-tools/context-menus-xml-schema-explorer.md). Můžete také provést hledání specifické pro schéma v zobrazení Start; Další informace najdete v části Podrobnosti o sadě schémat v tématu [spuštění zobrazení](../xml-tools/start-view.md) .

## <a name="displaying-and-navigating-search-results"></a>Zobrazení a navigace ve výsledcích hledání
 Po dokončení hledání se podokno souhrnné výsledky přidá na panel nástrojů s výsledky hledání. Výsledky hledání jsou také zvýrazněny v Průzkumníku schémat XML a označeny značkami na svislém posuvníku. Výsledky hledání můžete procházet pomocí možnosti **Přejít na další výsledek hledání** a **Přejít na předchozí** tlačítka výsledků hledání v podokně souhrnné výsledky hledání na panelu nástrojů Průzkumníka schémat XML. pomocí kláves klávesnice F3 a SHIFT + F3; nebo kliknutím na značky zaškrtnutí na posuvníku.

 Výsledky hledání můžete přidat do pracovního prostoru kliknutím na tlačítko **Přidat zvýrazněné uzly do pracovního prostoru** v podokně souhrnné výsledky.

 ![Výsledek hledání v Průzkumníkovi schémat XML](../xml-tools/media/schemaexplorersearchresult.gif "SchemaExplorerSearchResult")

## <a name="clearing-search-results"></a>Vymazání výsledků hledání
 Chcete-li vymazat výsledky hledání, klikněte na tlačítko **x** v podokně souhrnné výsledky na panelu nástrojů hledání v PRŮZKUMNÍKOVI schémat XML.

## <a name="see-also"></a>Viz také
 [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)
