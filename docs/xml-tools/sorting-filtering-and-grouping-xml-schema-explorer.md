---
title: Řazení a filtrování, seskupování v Průzkumníku schématu XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a3e281f8e3995cf22100d328089f1993110f756
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693666"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Řazení, filtrování a seskupení (Explorer schématu XML)

Toto téma popisuje možnosti, které jsou k dispozici prostřednictvím **možnosti seskupení, filtrování a řazení** nabídce **Explorer schématu XML** panelu nástrojů.

## <a name="filter-options"></a>Možnosti filtru.

 Jsou k dispozici následující možnosti filtru. Ve výchozím nastavení **zobrazit obory názvů** a **zobrazit soubory schématu** jsou vybrané možnosti.

-   **Zobrazit obory názvů**.

-   **Zobrazit soubory schématu**.

-   **Zobrazit Compositors (pořadí/volba/vše)**.

## <a name="sorting-options"></a>Řazení možnosti

 Jsou k dispozici následující možnosti řazení. Výchozí hodnota je **seřadit podle typu**. **Seřadit podle** možnosti se nevztahují k souborům a obory názvů.

-   **Řazení podle typu**.

-   **Řazení podle názvu**.

-   **Zdokumentujte pořadí**.

### <a name="sort-by-type"></a>Řazení podle typu

 Když **seřadit podle typu** je vybraná možnost, globální uzly jsou seřazeny v uvedeném pořadí. Uzly se potom řadí abecedně v rámci jednotlivých skupin.

1.  `import` uzly.

2.  `include` uzly.

3.  `redefine` uzly.

4.  `attribute` uzly.

5.  `attributeGroup` uzly.

6.  `complexType` uzly.

7.  `simpleType` uzly.

8.  `element` uzly.

9. `group` uzly.

### <a name="sort-by-name"></a>Řazení podle názvu

 Když **řazení podle názvu** je vybraná možnost, globální uzly jsou seřazeny v následujícím pořadí:

1.  `import` uzly (v abecedním pořadí oborů názvů).

2.  `include` uzly (v abecedním pořadí podle `schemaLocation` atributy).

3.  `redefine` uzly (v abecedním pořadí podle `schemaLocation` atributy).

4.  Jiné globální uzly v abecedním pořadí.

### <a name="document-order"></a>Pořadí dokumentů

 **Pořadí dokumentů** možnost je dostupná, když **zobrazit soubory schématu** je vybraná možnost. Když **pořadí dokumentů** je vybraná globální uzly jsou zobrazeny v pořadí, ve kterém se zobrazí v souboru schématu.

## <a name="persisting-sortfilter-options"></a>Zachování možnosti řazení nebo filtrování

 Řazení, filtrování a možnosti seskupení se uloží do registru pro každého uživatele, bez ohledu na to, která řešení nebo soubory byly otevřeny při změně tohoto nastavení.