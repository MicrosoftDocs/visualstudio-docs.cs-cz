---
title: Úpravy šablon stylů XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 080bed0f-0ca9-4be7-aecd-6bdaebc04007
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e1669affa89c91ca3ae1958c22ff3ec4d56bb8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670958"
---
# <a name="editing-xslt-style-sheets"></a>Úpravy šablon stylů XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML lze také použít pro úpravu šablon stylů XSLT. Můžete využít výhody výchozích funkcí editoru, jako je například IntelliSense, sbalení, fragmenty kódu XML a tak dále. Kromě toho existují také nové funkce, které usnadňují vývoj v jazyce XSLT.

## <a name="xslt-features"></a>Funkce XSLT
 Následující tabulka popisuje funkce specifické pro práci s šablonami stylů XSLT.

 **Barevné zvýrazňování syntaxe** Klíčová slova XSLT, jako jsou `template` , `match` a tak dále, se zobrazí v barvě klíčového slova XSLT určené nastavením **písma a barvy** .

 **Podtržení vlnovkou** Editor XML používá nainstalovaný soubor XSLT. xsd k ověření šablon stylů XSLT. Chyby ověřování se zobrazují modře podtržení vlnovkou. Editor XML také zkompiluje šablonu stylů na pozadí a sestavuje chyby nebo upozornění kompilátoru pomocí příslušných podtržení vlnovkou.

 **Podpora bloků skriptu** Ladicí program XSLT podporuje kód v blocích skriptu, takže můžete nastavit zarážky a krokovat kód bloku skriptu.

 **Zobrazit výstup XSLT** Můžete spustit transformaci XSL a zobrazit výstup z editoru XML. Další informace naleznete v tématu [How to: Execute Transform XSLT z editoru XML](../xml-tools/how-to-execute-an-xslt-transformation-from-the-xml-editor.md).

 **LADIT XSLT** Ladicí program XSLT můžete spustit ze souboru XSLT v editoru XML. Ladicí program podporuje nastavení zarážek v souboru XSLT, zobrazení stavu spuštění XSLT atd. Najetí myší na proměnnou XSLT přinese popis tlačítka s hodnotou proměnné. Ladicí program lze použít k ladění šablony stylů nebo k ladění zkompilované transformace XSL vyvolané z jiné aplikace. Další informace naleznete v tématu [ladění XSLT](../xml-tools/debugging-xslt.md).

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
