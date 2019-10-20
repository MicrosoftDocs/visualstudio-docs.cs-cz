---
title: Výchozí šablony XSLT
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81a764aa45eb74ba110d8b3b5965ede1e62bdadd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607783"
---
# <a name="xslt-default-templates"></a>Výchozí šablony XSLT

Výchozí šablona se používá během zpracování XSLT, pokud v šabloně stylů neexistuje žádné vyhovující pravidlo explicitní šablony. Výchozí šablona, označovaná také jako předdefinované pravidlo šablony, je definována v oddílu 5,8 doporučení W3C XSLT 1,0. Výchozí šablona umožňuje procesoru XSLT zpracovat uzel, a to i v případě, že neexistuje žádné explicitní pravidlo šablony, které by mu odpovídalo. Vzhledem k tomu, že předdefinované pravidlo šablony není explicitně definováno v šabloně stylů, může to vést k neočekávaným nebo matoucím výsledkům transformace XSLT.

Ladicí program XSLT nyní zobrazuje kód výchozích šablon XSLT. Při procházení transformace XSLT, pokud je použita výchozí šablona, ladicí program zobrazí výchozí šablonu v okně. To umožňuje procházet kód výchozí šablony a nastavit zarážky podle pokynů.

## <a name="see-also"></a>Viz také:

- [Ladění XSLT](../xml-tools/debugging-xslt.md)