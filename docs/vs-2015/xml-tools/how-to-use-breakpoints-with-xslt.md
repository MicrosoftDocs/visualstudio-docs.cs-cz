---
title: 'Postupy: použití zarážek s XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656298"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Postupy: použití zarážek s XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nastavit zarážky v šabloně stylů XSLT nebo ve zdrojovém dokumentu XML. Pokud nastavíte zarážku na značku, při spuštění se zarážka přesune k dalšímu příkazu, který obsahuje informace o řádku zdroje.

 Další informace najdete v tématu [základy ladění: zarážky](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Nastavení zarážky v šabloně stylů
 Zarážky lze nastavit u počátečních značek, koncových značek a textových uzlů šablony stylů XSLT. Zarážky lze také nastavit pro kód v bloku skriptu.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Nastavení zarážky v šabloně stylů

1. Otevřete šablonu stylů v editoru XML.

2. Umístěte kurzor na umístění zarážky, klikněte pravým tlačítkem myši, přejděte na **zarážku**a klikněte na **Vložit zarážku**.

3. Klikněte na tlačítko Procházet procházením ( **...** ) v poli **input** okna vlastností dokumentu.

4. Vyhledejte zdrojový dokument XML a klikněte na **otevřít**.

     Tím se nastaví zdrojový soubor dokumentu, který se používá pro transformaci XSLT.

5. Klikněte na tlačítko **LADIT XSL** na panelu nástrojů editoru XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Nastavení zarážky ve zdrojovém dokumentu XML
 Zarážky lze nastavit u elementů, atributů, uzlu oboru názvů, komentářů, instrukcí pro zpracování a textových uzlů zdrojového dokumentu XML. Nelze nastavit zarážku na uzlu dokumentu nebo na uzlu oboru názvů, který je zděděn z nadřazeného elementu.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Nastavení zarážky ve zdrojovém dokumentu XML

1. Otevřete dokument XML v editoru XML.

2. Umístěte kurzor na umístění zarážky, klikněte pravým tlačítkem myši, přejděte na **zarážku**a klikněte na **Vložit zarážku**.

3. Klikněte na tlačítko Procházet procházením ( **...** ) v poli **StyleSheet** okna vlastností dokumentu.

4. Vyhledejte zdrojový dokument XML a klikněte na **otevřít**.

     Tím se nastaví zdrojový soubor dokumentu, který se používá pro transformaci XSLT.

5. Klikněte na tlačítko **LADIT XSL** na panelu nástrojů editoru XML.

## <a name="see-also"></a>Viz také
 [Návod: Ladění šablony stylů XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
