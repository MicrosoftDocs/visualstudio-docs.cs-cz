---
title: 'Postupy: spuštění transformace XSLT z editoru XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b305d88779603b374e5f95842d7a5271a657268
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666537"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Postupy: spuštění transformace XSLT z editoru XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML umožňuje přidružit šablonu stylů XSLT k dokumentu XML, provést transformaci a zobrazit výstup. Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.

 Vlastnost **Output** Určuje název souboru pro výstup. Pokud je vlastnost **Output** prázdná, v dočasném adresáři se vygeneruje název souboru. Přípona souboru je založena na prvku `xsl:output` v šabloně stylů a může být. XML,. txt nebo. htm.

 Pokud vlastnost **Output** Určuje název souboru s příponou. htm nebo. html, výstup XSLT je zobrazený pomocí [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer. Všechny ostatní přípony souborů jsou otevřeny pomocí výchozího editoru zvoleného [!INCLUDE[msCoName](../includes/msconame-md.md)] sady Visual Studio. Například pokud Přípona souboru je. XML, Visual Studio používá editor XML.

### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Spuštění transformace XSLT z dokumentu XML

1. Otevřete dokument XML v editoru XML.

2. Přidružte šablonu stylů XSLT k dokumentu XML.

    - Přidejte do dokumentu XML instrukci pro zpracování `xml-stylesheet`. Přidejte například následující řádek `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` do prologu dokumentu.

         -nebo-

    - Přidejte šablonu stylů XSLT pomocí okna **vlastnosti** . V **okně Vlastnosti**dokumentu klikněte na tlačítko **Procházet** pro pole **STYLESHEET** , vyberte šablonu stylů XSLT a klikněte na tlačítko **otevřít**.

3. Klikněte na tlačítko **výstup ShowXSL** na panelu nástrojů **editoru XML** .

    > [!NOTE]
    > Pokud k dokumentu XML není přidružena žádná šablona stylů, zobrazí se dialogové okno s výzvou, abyste zadali šablonu stylů, která se má použít.
    >
    >  Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.

### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Provedení transformace XSLT ze šablony stylů XSLT

1. Otevřete šablonu stylů XSLT v editoru XML.

2. Zadejte dokument XML do pole **vstup** v okně **vlastností** dokumentu.

    > [!NOTE]
    > Dokument XML je vstupní dokument, který se používá pro transformaci. Pokud při spuštění transformace XSLT není dokument zadán, zobrazí se dialogové okno **otevřít soubor** a v tomto okamžiku můžete zadat dokument.

3. Klikněte na tlačítko **výstup ShowXSLT** na panelu nástrojů **editoru XML** .

     Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.

### <a name="to-provide-a-different-output-file-name"></a>Chcete-li zadat jiný název výstupního souboru

1. V poli **výstup** v okně **vlastností** dokumentu zadejte název souboru.

2. Klikněte na tlačítko **výstup ShowXSLT** na panelu nástrojů **editoru XML** .

     Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu a editor použitý v okně výstup závisí na příponě souboru ve vlastnosti **výstupního** dokumentu.

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
