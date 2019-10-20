---
title: Úpravy šablon stylů XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7fc987f8362d5daf435b7e9de860cc13f16a1aaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646062"
---
# <a name="edit-xslt-style-sheets"></a>Upravit šablony stylů XSLT

Editor XML lze také použít pro úpravu šablon stylů XSLT. Můžete využít výhody výchozích funkcí editoru, jako je například IntelliSense, sbalení, fragmenty kódu XML a tak dále. Kromě toho existují také nové funkce, které usnadňují vývoj v jazyce XSLT.

## <a name="xslt-features"></a>Funkce XSLT

Následující tabulka popisuje funkce specifické pro práci s šablonami stylů XSLT.

**Barevné zvýrazňování syntaxe**

Klíčová slova XSLT, například `template` a `match`, se zobrazí v barvě klíčového slova XSLT určené nastaveními **písma a barvy** .

**Podtržení vlnovkou**

Editor XML používá nainstalovaný soubor *XSLT. xsd* k ověření šablon stylů XSLT. Chyby ověřování se zobrazují modře podtržení vlnovkou. Editor XML také zkompiluje šablonu stylů na pozadí a sestavuje chyby nebo upozornění kompilátoru pomocí příslušných podtržení vlnovkou.

**Podpora bloků skriptu**

Ladicí program XSLT podporuje kód v blocích skriptu, takže můžete nastavit zarážky a krokovat kód bloku skriptu.

**Zobrazit výstup XSLT**

Můžete spustit transformaci XSL a zobrazit výstup z editoru XML. Další informace naleznete v tématu [How to: Execute Transform XSLT z editoru XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Ladit XSLT**

Ladicí program XSLT můžete spustit ze souboru XSLT v editoru XML. Ladicí program podporuje nastavení zarážek v souboru XSLT, zobrazení stavu spuštění XSLT atd. Najetí myší na proměnnou XSLT přinese popis tlačítka s hodnotou proměnné. Ladicí program lze použít k ladění šablony stylů nebo k ladění zkompilované transformace XSL vyvolané z jiné aplikace. Další informace naleznete v tématu [ladění XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Viz také:

- [Editor XML](../xml-tools/xml-editor.md)