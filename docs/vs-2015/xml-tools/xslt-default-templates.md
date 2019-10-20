---
title: Výchozí šablony XSLT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bb4351d6b95c7aee929274135454ecf7aa91574
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669329"
---
# <a name="xslt-default-templates"></a>Výchozí šablony XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Výchozí šablona se používá během zpracování XSLT, pokud v šabloně stylů neexistuje žádné vyhovující pravidlo explicitní šablony. Výchozí šablona, označovaná také jako předdefinované pravidlo šablony, je definována v oddílu 5,8 doporučení W3C XSLT 1,0. Výchozí šablona umožňuje procesoru XSLT zpracovat uzel, a to i v případě, že neexistuje žádné explicitní pravidlo šablony, které by mu odpovídalo. Vzhledem k tomu, že předdefinované pravidlo šablony není explicitně definováno v šabloně stylů, může to vést k neočekávaným nebo matoucím výsledkům transformace XSLT.

 Ladicí program XSLT nyní zobrazuje kód výchozích šablon XSLT. Při procházení transformace XSLT, pokud je použita výchozí šablona, ladicí program zobrazí výchozí šablonu v okně. To umožňuje procházet kód výchozí šablony a nastavit zarážky podle pokynů.

## <a name="see-also"></a>Viz také
 [Ladění XSLT](../xml-tools/debugging-xslt.md)
