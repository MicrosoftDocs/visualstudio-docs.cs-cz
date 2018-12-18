---
title: 'Postupy: provedení transformace XSLT z editoru XML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 358c799c0ef6cd6ab90f64e5025376141ff534c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245281"
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Postupy: provedení transformace XSLT z editoru XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Editor lze přidružit k dokumentu XML, šablony stylů XSLT provedení transformace a zobrazte výstup. Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.  
  
 **Výstup** vlastnost určuje název souboru pro výstup. Pokud **výstup** je vlastnost prázdná, jejichž název souboru se vygeneruje v dočasném adresáři. Přípona souboru je založen na `xsl:output` prvek vašemu stylu listů a může být XML, txt nebo htm.  
  
 Pokud **výstup** vlastnost určuje název souboru .htm nebo .html rozšíření, výstup XSLT je zobrazen náhled pomocí [!INCLUDE[msCoName](../includes/msconame-md.md)] aplikace Internet Explorer. Jiné přípony souborů jsou otevřené pomocí výchozího editoru zvolené [!INCLUDE[msCoName](../includes/msconame-md.md)] sady Visual Studio. Například pokud je přípona souboru .xml, Visual Studio používá editoru XML.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>K provedení transformace XSLT z dokumentu XML  
  
1.  Otevřete dokument XML v editoru XML.  
  
2.  Šablony stylů XSLT přidružte k dokumentu XML.  
  
    -   Přidat `xml-stylesheet` zpracování instrukcí v dokumentu XML. Například přidejte následující řádek `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` do kódu prologu dokumentu.  
  
         -nebo-  
  
    -   Přidat list Styl XSLT pomocí **vlastnosti** okna. V dokumentu **okno vlastností**, klikněte na tlačítko **Procházet** tlačítko pro **šablony stylů** pole, vyberte šablony stylů XSLT a klikněte na tlačítko **otevřete**.  
  
3.  Klikněte na tlačítko **ShowXSL výstup** tlačítko **editoru XML** nástrojů.  
  
    > [!NOTE]
    >  Pokud není k dispozici žádné šablony stylů přidružené k dokumentu XML, dialogové okno zobrazí výzvu k zadání šablony stylů k použití.  
    >   
    >  Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>K provedení transformace XSLT z šablony stylů XSLT  
  
1.  Otevření šablony stylů XSLT v editoru XML.  
  
2.  Zadejte v dokumentu XML **vstup** pole dokumentu **vlastnosti** okna.  
  
    > [!NOTE]
    >  Dokument XML je vstupní dokument použitý pro transformaci. Pokud dokument není zadán při spuštění transformace XSLT **otevřít soubor** zobrazí se dialogové okno a zadáte dokumentu v daném čase.  
  
3.  Klikněte na tlačítko **ShowXSLT výstup** tlačítko **editoru XML** nástrojů.  
  
     Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu.  
  
### <a name="to-provide-a-different-output-file-name"></a>Jako název jiný výstupní soubor  
  
1.  Zadejte název souboru v **výstup** pole dokumentu **vlastnosti** okna.  
  
2.  Klikněte na tlačítko **ShowXSLT výstup** tlačítko **editoru XML** nástrojů.  
  
     Výsledný výstup z transformace XSLT se zobrazí v novém okně dokumentu a editor používaný v okně výstupu závisí na příponu souboru vaší **výstup** vlastnost dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Editor XML](../xml-tools/xml-editor.md)



