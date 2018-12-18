---
title: 'Postupy: zobrazení a úpravy kódu s použitím funkce Náhled definice (Alt + F12) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: cc99602fe1ca2003995594f75736d581fa37e0d0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254472"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Postupy: Zobrazení a úpravy kódu s použitím funkce Náhled definice (ALT+F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **definice operace Peek** příkaz k zobrazení a úpravám kódu bez přepnutí mimo kód, který píšete. **Náhled definice** a **přejít k definici** obsahují stejné informace, ale **definice operace Peek** zobrazí v místním okně a **přejít k definici** ukazuje kód v samostatném okně s kódem. **Přejít k definici** způsobí, že váš kontext (tedy okno s aktivním kódem, aktuální řádek a pozice kurzoru) přejděte do okna Definice kódu. S použitím **definice operace Peek**, můžete zobrazit a upravit definici a pohyb uvnitř souboru definice při zachování svého místa v původním souboru kódu.  
  
 Můžete použít **definice operace Peek** s kódem jazyka C#, Visual Basic a C++. V jazyce Visual Basic **definice operace Peek** zobrazuje odkaz **prohlížeče objektů** pro symboly, které neobsahují metadata definice (například typy rozhraní .NET Framework, které jsou integrované v).  
  
> [!IMPORTANT]
>  Tento příkaz nelze použít v žádné verzi Express sady Visual Studio 2013.  
  
## <a name="working-with-peek-definition"></a>Práce s náhledem definice  
  
#### <a name="to-open-a-peek-definition-window"></a>Otevření okna Náhled definice  
  
1.  Můžete najít **definice operace Peek** tak, že otevřete místní nabídku pro metodu, která chcete prozkoumat. (Klávesnice: Alt+F12)  
  
     Tento obrázek ukazuje **definice operace Peek** okna pro metodu s názvem `Print()`:  
  
     ![Operace Peek okno](../ide/media/peekwindow.png "PeekWindow")  
  
     Zobrazí se okno Definice pod `printer.Print(“Hello World!”)` řádku v původním souboru. Okno neskryje žádný kód v původním souboru. Řádky, které následují `printer.Print(“Hello World!”)` volání se zobrazí pod oknem definice.  
  
2.  Kurzor můžete přesunout na jiné místo v okně definice kódu. Můžete se i nadále pohybovat v původním okně kódu nad nebo pod oknem definice.  
  
3.  Můžete zkopírovat řetězec v okně definice a vložit ho do původního kódu. Můžete také přetáhnout řetězec z okna definice do původního kódu, aniž by byl v okně definice odstraněn.  
  
4.  Můžete zavřít okno Definice výběrem klávesy Esc nebo **zavřete** tlačítko na kartě okna definice.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Otevření okna Náhled definice z okna Náhled definice  
  
-   Pokud už máte **definice operace Peek** otevřené okno, můžete volat **definice operace Peek** znovu na kód v tomto okně. Otevře se jiné okno definice. Vedle karty okna definice se zobrazí sada teček s popisem cesty, která slouží k navigaci mezi okny definice. Popisek tlačítka na každé tečce zobrazuje název souboru a cestu k souboru definice, který tečka přestavuje.  
  
     ![Náhled okna nejvyšší úrovně v okně Náhled](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Použití náhledu definice s více výsledky  
  
-   Pokud používáte **definice operace Peek** na kód, který obsahuje více než jednu definici (například částečné třídy), seznam výsledků se zobrazí napravo od zobrazení definice kódu. Můžete zvolit některý z výsledků v seznamu k zobrazení jeho definice.  
  
     ![Okno náhledu z více výsledků](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Provádění úprav v okně Náhled definice  
  
-   Při zahájení úprav v **definice operace Peek** okna, soubor, který modifikujte, automaticky se otevře jako samostatná karta v editoru kódu a odráží změny, které jste již provedli. Ujistěte se, rušit a ukládat změny v můžete pokračovat **definice operace Peek** okně a na kartě budou odrážet provedené změny. I když toto okno zavřete bez uložení změn, lze na této kartě provádět, rušit a ukládat změny, což vás přenese přesně tam, kde jste v tomto okně skončili.  
  
     ![Úpravy v rámci okna Náhled](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Použití klávesových zkratek pro náhled definice  
  
-   Můžete použít tyto klávesové zkratky v **definice operace Peek** okno:  
  
    |Funkce|Klávesová zkratka|  
    |-------------------|-----------------------|  
    |Otevřít okno definice|Alt+F12|  
    |Zavřít okno definice|Esc|  
    |Povýšit okno definice na běžnou kartu dokumentu|Shift+Alt+Home|  
    |Navigace mezi okny definice|Ctrl+Alt+- a Ctrl+Alt+=|  
    |Navigace mezi několika výsledky|F8 a Shift+F8|  
    |Přepnout mezi oknem editoru kódu a oknem definice|Shift+Esc|  
  
    > [!NOTE]
    >  Můžete také použít stejné klávesové zkratky pro úpravu kódu v **definice operace Peek** okno jako můžete použít na jiném místě v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Tipy pro vyšší produktivitu](../ide/productivity-tips-for-visual-studio.md)



