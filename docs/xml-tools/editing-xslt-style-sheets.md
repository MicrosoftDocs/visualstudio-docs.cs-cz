---
title: Úpravy XSLT šablony stylů
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 72f224e91f72d2fa751ddc8b170f78b8859c43f4
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548447"
---
# <a name="edit-xslt-style-sheets"></a>Upravit XSLT šablony stylů

Editor souborů XML lze také upravit XSLT šablony stylů. Můžete využít výhod výchozí funkce editoru, jako je technologie IntelliSense, osnovy, fragmenty kódu XML a tak dále. Kromě toho existují také nové funkce, které usnadňují vývoj v XSLT.

## <a name="xslt-features"></a>Funkce XSLT
 Následující tabulka popisuje funkce, které jsou specifické pro práci s XSLT šablony stylů.

 **Barevné zvýrazňování syntaxe**

 Klíčová slova XSLT, například `template`, `match`a tak dále se zobrazují v barvu – klíčové slovo XSLT určeného **písma a barev** nastavení.

 **Podtržení vlnovkami**

 Editor souborů XML používá nainstalovaného *xslt.xsd* soubor pro ověření XSLT šablony stylů. Jako modré podtržení vlnovkami zobrazí chyby ověření. Editor souborů XML také zkompiluje šablony stylů v pozadí a sestavy kompilátoru chyby nebo upozornění s příslušnou podtržení vlnovkami.

 **Podpora pro blocích skriptu**

 Ladicí program XSLT podporuje kódu v blocích skriptu, můžete nastavit zarážky a krokovat kód bloku skriptu.

 **Zobrazit výstup XSLT**

 Můžete provést transformace XSL a zobrazte výstup z editoru XML. Další informace najdete v tématu [postup: provedení transformace XSLT z editoru XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **Ladění XSLT**

 Můžete spustit ladicí program XSLT ze souboru XSLT v editoru XML. Ladicí program podporuje nastavení zarážek v souboru XSLT, zobrazení stavu spuštění XSLT a tak dále. Ukazatele myši na proměnnou XSLT zobrazí popisek s hodnotou proměnné. Ladicí program slouží k ladění šablony stylů a ladit kompilované transformace XSL vyvolat z jiné aplikace. Další informace najdete v tématu [ladění XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)