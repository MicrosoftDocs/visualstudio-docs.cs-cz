---
title: 'Postupy: používání zarážek v XSLT | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b01553075115ce953b499f722a254b5a2b9f20ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233451"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Postupy: používání zarážek v XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit zarážky v šabloně stylů XSLT, nebo ve zdrojovém dokumentu XML. Pokud nastavíte zarážku na značku, při spuštění zarážce přejde k další příkaz, který obsahuje informace o řádku zdroje.  
  
 Další informace najdete v tématu [základní informace o ladění: zarážky](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## <a name="set-a-breakpoint-in-a-style-sheet"></a>Nastavte zarážku v šabloně stylů  
 Zarážky lze nastavit na počáteční značky, koncovými značkami a textové uzly šablony stylů XSLT. Zarážky můžete také nastavit na kód v bloku skriptu.  
  
#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Chcete-li nastavit zarážku v šabloně stylů  
  
1.  Otevření šablony stylů v editoru XML.  
  
2.  Umístěte kurzor myši v místě zarážky, klikněte pravým tlačítkem, přejděte na **zarážku**a klikněte na tlačítko **vložit zarážku**.  
  
3.  Klikněte na tlačítko Procházet na tlačítko Procházet (**...** ) na **vstup** pole v okně Vlastnosti dokumentu.  
  
4.  Vyhledejte zdrojový dokument XML a klikněte na tlačítko **otevřít**.  
  
     Tím se nastaví zdrojový soubor dokumentu, který slouží k transformaci XSLT.  
  
5.  Klikněte na tlačítko **ladění XSL** tlačítko na panelu nástrojů editoru XML.  
  
## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Nastavit zarážku ve zdrojovém dokumentu XML  
 Zarážky lze nastavit na elementy, atributy, uzel oboru názvů, komentáře, instrukce pro zpracování a textové uzly zdrojovém dokumentu XML. Nelze nastavit zarážku na uzel dokumentu nebo na uzel oboru názvů, který je zděděn z nadřazeného elementu.  
  
#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Chcete-li nastavit zarážku ve zdrojovém dokumentu XML  
  
1.  Otevřete dokument XML v editoru XML.  
  
2.  Umístěte kurzor myši v místě zarážky, klikněte pravým tlačítkem, přejděte na **zarážku**a klikněte na tlačítko **vložit zarážku**.  
  
3.  Klikněte na tlačítko Procházet na tlačítko Procházet (**...** ) na **šablony stylů** pole v okně Vlastnosti dokumentu.  
  
4.  Vyhledejte zdrojový dokument XML a klikněte na tlačítko **otevřít**.  
  
     Tím se nastaví zdrojový soubor dokumentu, který slouží k transformaci XSLT.  
  
5.  Klikněte na tlačítko **ladění XSL** tlačítko na panelu nástrojů editoru XML.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Ladění šablony stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)

