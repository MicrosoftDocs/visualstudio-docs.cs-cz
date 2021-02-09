---
title: Výchozí šablony XSLT
description: Přečtěte si o výchozích šablonách XSLT, které se používají během zpracování XSLT, pokud v šabloně stylů neexistuje odpovídající explicitní pravidlo šablony.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874753"
---
# <a name="xslt-default-templates"></a>Výchozí šablony XSLT

Výchozí šablona se používá během zpracování XSLT, pokud v šabloně stylů neexistuje žádné vyhovující pravidlo explicitní šablony. Výchozí šablona, označovaná také jako předdefinované pravidlo šablony, je definována v oddílu 5,8 doporučení W3C XSLT 1,0. Výchozí šablona umožňuje procesoru XSLT zpracovat uzel, a to i v případě, že neexistuje žádné explicitní pravidlo šablony, které by mu odpovídalo. Vzhledem k tomu, že předdefinované pravidlo šablony není explicitně definováno v šabloně stylů, může to vést k neočekávaným nebo matoucím výsledkům transformace XSLT.

Ladicí program XSLT nyní zobrazuje kód výchozích šablon XSLT. Při procházení transformace XSLT, pokud je použita výchozí šablona, ladicí program zobrazí výchozí šablonu v okně. To umožňuje procházet kód výchozí šablony a nastavit zarážky podle pokynů.

## <a name="see-also"></a>Viz také

- [Ladění XSLT](../xml-tools/debugging-xslt.md)
