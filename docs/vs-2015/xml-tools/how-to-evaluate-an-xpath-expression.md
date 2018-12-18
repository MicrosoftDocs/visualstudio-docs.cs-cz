---
title: 'Postupy: vyhodnocení výrazu XPath | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05758034c0228f0efd7fb3ae63bd3b7e0d5e3095
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210428"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Postupy: vyhodnocení výrazu XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete si vyzkoušet výrazy XPath s **QuickWatch** dialogové okno. Výraz XPath musí být platný podle doporučení W3C XPath 1.0. Aktuální kontext XSLT – to znamená, `self::node()` uzlu v **lokální** okno – poskytuje kontext vyhodnocení výrazu XPath.  
  
 Následující seznam popisuje, jaké funkce jsou podporovány při vyhodnocování výrazu XPath:  
  
-   Podporují se předdefinované funkce XPath.  
  
-   Integrované funkce XSLT nejsou podporovány.  
  
-   Uživatelem definované funkce nejsou podporovány.  
  
> [!NOTE]
>  Následující postup používá belowAvg.xsl a books.xml soubory z [návod: ladění šablony stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) tématu.  
  
### <a name="to-evaluate-an-xpath-expression"></a>Vyhodnocení výrazu XPath  
  
1.  Vložit zarážku na `xsl:if` počáteční značka.  
  
2.  Klikněte na tlačítko **ladění XSL** tlačítko na panelu nástrojů editoru XML.  
  
     Ladicí program se spustí a dojde k porušení `xsl:if` značky.  
  
3.  Klikněte pravým tlačítkem a vyberte **QuickWatch**.  
  
     **QuickWatch** se zobrazí dialogové okno.  
  
4.  Zadejte `./price/text()` v **výraz** pole **QuickWatch** dialogové okno a klikněte na tlačítko **přehodnotit**.  
  
     Ceny pro aktuální uzel knihy se zobrazí v **hodnotu** pole.  
  
5.  Změnit výraz XPath, který má `./price/text() < $bookAverage` a klikněte na tlačítko **přehodnotit**.  
  
     **Hodnotu** poli se zobrazí, že vyhodnocení výrazu XPath má `true`.  
  
## <a name="see-also"></a>Viz také  
 [Ladění XSLT](../xml-tools/debugging-xslt.md)

