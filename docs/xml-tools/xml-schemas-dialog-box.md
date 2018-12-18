---
title: Dialogové okno Schémata XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5357f762d2a7027db92ad1916acb279abdf23157
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693637"
---
# <a name="xml-schemas-dialog-box"></a>Dialogové okno schémat XML

**Schémat XML** dialogové okno slouží k výběru které schématu XML schéma definice jazyka (XSD). Chcete přidružit k dokumentu XML. Můžete vybrat schéma z mezipaměti schématu, nebo zadejte schéma, které se nenachází v mezipaměti. Vybrané schématech jsou považovány za součást sadu schématu. Sada schématu se používá technologie IntelliSense a také ověření dokumentu XML.

Dostanete **schémat XML** dialogové okno kliknutím buď **schémata** tlačítka v okně vlastností dokumentu nebo výběrem **schémata** z **XML** nabídky.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 **Použití**

 Vyberte, jakým způsobem má být použita schématu XML.

-   **Automatické**. Toto schéma není používán aktuální dokumentu, ale je k dispozici pro automatické přidružení. Pokud v dokumentu XML deklaruje obor názvů, který odpovídá `targetNamespace` tohoto schématu budou automaticky přidruženy schéma a je součástí sady schématu.

-   **Toto schéma používají**. Toto schéma je stále používán aktuálním dokumentu. Uživatel má explicitně požadována, že toto schéma použít kliknutím na tento sloupec nebo schématu se automaticky přidruží podle odpovídající `targetNamespace`.

-   **Nepoužívejte vybrané schémata**. Toto schéma není používán aktuální dokument i v případě, že schéma má odpovídající `targetNamespace`. Toto nastavení může být užitečné při řešení konfliktů při více než jedna verze stejné schéma v mezipaměti schématu nebo řešení.

**Namespace cíl**

Zobrazí cílový obor názvů související s schématu XML.

**Název souboru**

Zobrazuje název souboru schématu XML.

**Přidat**

Otevře se **otevřete schématu XSD** dialog, který vám umožní vybrat další schémata přidat do sady schématu. Při přidávání schématu do schématu nastavit, **použití** hodnota sloupce je nastavena na **toto schéma používají**.

**Odebrat**

Odebere aktuálně vybrané schéma ze sady schématu. Schéma budou odebrány z mezipaměti v paměti schématu, ale není ze systému souborů.

## <a name="see-also"></a>Viz také:

- [Součásti editoru XML](../xml-tools/xml-editor-components.md)
- [Postupy: Výběr schémat XML používat](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Mezipaměti schématu](../xml-tools/schema-cache.md)