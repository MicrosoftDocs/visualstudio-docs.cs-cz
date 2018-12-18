---
title: Výchozí šablony XSLT
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b50a7457ddbae24f2a00e4c631371cb2aeb1169
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693952"
---
# <a name="xslt-default-templates"></a>Výchozí šablony XSLT

Výchozí šablona služby se používá během XSLT zpracováním, když není odpovídající pravidlo explicitní šablony v šabloně stylů. Výchozí šablony, také označovaná jako pravidlo předdefinované šablony, je definovaný v oddílu 5.8 doporučení W3C XSLT 1.0. Výchozí šablony umožňuje XSLT procesor pro zpracování uzlu, i když neexistuje žádné explicitní šablony pravidlo, které odpovídá ho. Ale vzhledem k tomu, že pravidlo předdefinované šablony nejsou výslovně definované v šabloně stylů, to může vést k neočekávané nebo matoucí výsledky transformace XSLT.

Ladicí program XSLT teď zobrazuje kód XSLT výchozí šablony. Když je krok prostřednictvím transformace XSLT, pokud je použita výchozí šablona, ladicí program zobrazí výchozí šablony v okně. To vám umožňuje procházet kód výchozí šablony a nastavte zarážky v jeho pokyny.

## <a name="see-also"></a>Viz také:

- [Ladění XSLT](../xml-tools/debugging-xslt.md)