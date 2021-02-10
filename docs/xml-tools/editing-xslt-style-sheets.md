---
title: Úpravy šablon stylů XSLT
description: Přečtěte si o funkcích v editoru XML pro úpravu šablon stylů XSLT, včetně barevného zbarvení, podtržení a spuštění ladicího programu XSLT z editoru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: df9bff28e68b373bb932f33ff8fb34439f0b4e7c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969085"
---
# <a name="edit-xslt-style-sheets"></a>Upravit šablony stylů XSLT

Editor XML lze také použít pro úpravu šablon stylů XSLT. Můžete využít výhody výchozích funkcí editoru, jako je například IntelliSense, sbalení, fragmenty kódu XML a tak dále. Kromě toho existují také nové funkce, které usnadňují vývoj v jazyce XSLT.

## <a name="xslt-features"></a>Funkce XSLT

Následující tabulka popisuje funkce specifické pro práci s šablonami stylů XSLT.

**Barevné zvýrazňování syntaxe**

Klíčová slova XSLT, `template` jako `match` jsou a, se zobrazí v barvě klíčového slova XSLT určené nastaveními **písma a barvy** .

**Podtržení vlnovkou**

Editor XML používá nainstalovaný soubor *XSLT. xsd* k ověření šablon stylů XSLT. Chyby ověřování se zobrazují modře podtržení vlnovkou. Editor XML také zkompiluje šablonu stylů na pozadí a sestavuje chyby nebo upozornění kompilátoru pomocí příslušných podtržení vlnovkou.

**Podpora bloků skriptu**

Ladicí program XSLT podporuje kód v blocích skriptu, takže můžete nastavit zarážky a krokovat kód bloku skriptu.

**Zobrazit výstup XSLT**

Můžete spustit transformaci XSL a zobrazit výstup z editoru XML. Další informace naleznete v tématu [How to: Execute Transform XSLT z editoru XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

**Ladění XSLT**

Ladicí program XSLT můžete spustit ze souboru XSLT v editoru XML. Ladicí program podporuje nastavení zarážek v souboru XSLT, zobrazení stavu spuštění XSLT atd. Najetí myší na proměnnou XSLT přinese popis tlačítka s hodnotou proměnné. Ladicí program lze použít k ladění šablony stylů nebo k ladění zkompilované transformace XSL vyvolané z jiné aplikace. Další informace naleznete v tématu [ladění XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Viz také

- [Editor XML](../xml-tools/xml-editor.md)
