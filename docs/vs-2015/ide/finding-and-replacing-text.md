---
title: Hledání a nahrazení textu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e4bbe1456632b2707ca548582bb278f7646ec540
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49273439"
---
# <a name="finding-and-replacing-text"></a>Hledání a nahrazení textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete najít a nahradit text v editoru kódu sady Visual Studio a některých výstupních windows, jako **výsledky hledání** windows pomocí **najít a nahradit** ovládací prvek nebo **najít / Nahradit v souborech**. Můžete také hledat a nahradit v některých oknech návrháře, jako je například Návrhář XAML a Návrhář formulářů Windows a okna nástrojů  
  
 Můžete nastavit obor hledání na aktuální dokument, aktuální řešení nebo vlastní sadu složek. Můžete také zadat sadu přípon názvů souborů pro vyhledávání s více soubory. Syntaxi vyhledávání můžete přizpůsobit pomocí regulárních výrazů .NET.  
  
 Vyhledání a nahrazení regulárních výrazů, naleznete v tématu [pomocí regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  **Najít/příkaz** pole je stále k dispozici jako ovládací prvek panelu nástrojů, ale už není ve výchozím nastavení viditelný. Můžete zobrazit **najít/příkaz** pole výběrem **přidat nebo odebrat tlačítka** na **standardní** nástrojů a následným výběrem možnosti **najít**. Další informace najdete v tématu [pole najít/příkaz](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Najít a nahradit řídící prvek  
 **Najít a nahradit** ovládací prvek se zobrazí v pravém horním rohu okna editoru kódu. **Najít a nahradit** ovládací prvek okamžitě zvýrazní všechny výskyty daného hledaného řetězce v aktuálním dokumentu. Můžete přecházet z jednoho výskytu na jiný výběrem **najít další** tlačítko nebo **najít předchozí** tlačítka na ovládacím prvku hledání.  
  
 Možnostem výměny můžete přejít kliknutím na tlačítko vedle **najít** textového pole. Chcete-li nahrazovat po jednom čas, zvolte **nahradit další** vedle **nahradit** textového pole. Chcete-li nahradit všechny shody, zvolte **Nahradit vše** tlačítko.  
  
 Chcete-li změnit barvu zvýraznění shody, zvolte **nástroje** nabídce vyberte možnost **možnosti**a klikněte na tlačítko **prostředí**a vyberte **písma a barvy** . V **zobrazit nastavení pro** seznamu vyberte **textový Editor**a pak v **zobrazení položek** seznamu vyberte **najít zvýraznění (rozšíření)**.  
  
### <a name="searching-tool-windows"></a>Hledání nástroj Windows  
 Můžete použít **najít** v ovládacím prvku kódu nebo textových oknech, jako například **výstup** windows, a **výsledky hledání** výběrem **najít a nahradit**na **upravit** nabídky nebo (CTRL + F).  
  
 Verze ovládacího prvku najít je k dispozici také v některých oknech nástrojů. Například teď můžete filtrovat seznam ovládacích prvků v **nástrojů** okna tak, že zadáte text do vyhledávacího pole. Zahrnout ostatním oknům nástrojů, které nyní umožňují prohledávat jejich obsah **Průzkumníku řešení**, **vlastnosti** okně a **Team Exploreru**, mimo jiné.  
  
## <a name="findreplace-in-files"></a>Najít/nahradit v souborech  
 **Najít/nahradit v souborech** funguje jako **najít a nahradit** řídit, s tím rozdílem, že můžete definovat rozsah hledání. Nejenže můžete vyhledávat v aktuálně otevřeném souboru v editoru, ale můžete také vyhledat všech otevřených dokumentech, celém řešení, aktuálním projektu a vybrané sadě složek. Můžete také vyhledat pomocí přípony názvu souboru. Pro přístup **najít/nahradit v souborech** dialogového okna zvolte **najít a nahradit** na **upravit** nabídce (nebo CTRL + SHIFT + F).  
  
 Pokud zvolíte **najít všechny**, **výsledky hledání** okno se otevře a zobrazí seznam odpovídajících položek pro hledání. Výběr výsledku v seznamu zobrazí přidružený soubor a zvýrazní shodu. Pokud soubor ještě není otevřený pro úpravy, bude otevřen v kartě preview na pravé straně karty dobře. Můžete použít **najít** ovládací prvek prohledávat **výsledky hledání** seznamu.  
  
### <a name="creating-custom-search-folder-sets"></a>Vytvoření sad složek pro vlastní vyhledávání  
 Můžete definovat obor hledání výběrem **zvolit složky pro hledání** tlačítko (vypadá jako **...** ) vedle položky **Hledat v** pole. V **zvolit složky pro hledání** dialogové okno, můžete určit sadu složek, ve kterých chcete hledat a specifikaci můžete uložit tak, aby jej můžete znovu použít později. Pouze v případě, že budete mít je jednotka namapována v místním počítači, můžete určit složky ve vzdáleném počítači.  
  
### <a name="creating-custom-component-sets"></a>Vytvoření vlastních sad součástí  
 Součást sady můžete definovat jako obor hledání výběrem **upravit sadu vlastních komponent** vedle **Hledat v** pole. Můžete určit nainstalované součásti .NET nebo COM, projekty aplikace Visual Studio, které jsou součástí vašeho řešení nebo libovolné sestavení nebo typ knihovny (.dll, .tlb, .olb, .exe nebo .ocx). Chcete-li prohledat odkazy, vyberte **Hledat v odkazech** pole.  
  
## <a name="see-also"></a>Viz také  
 [Používání regulárních výrazů v sadě Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)



