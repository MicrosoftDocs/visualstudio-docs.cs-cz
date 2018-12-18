---
title: Nalezení změn kódu a další historie pomocí Codelensu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: df4b435f791b066afda90ac9f5492a946d7e215c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825666"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Nalezení změn kódu a další historie pomocí CodeLensu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Soustředit na svou práci při můžete zjistit, co se stalo s kódu – bez opuštění editoru. Najdete odkazy a změny kódu, propojené chyby, pracovní položky, revize kódu a testy jednotek.  
  
> [!NOTE]
>  CodeLens je k dispozici pouze v edicích sady Visual Studio Enterprise a Visual Studio Professional. Není k dispozici v aplikaci Visual Studio Community edition.  
  
 V tématu, kde a jak se ve vašem řešení používají jednotlivé části kódu:  
  
 ![Indikátory CodeLens v editoru kódu](../ide/media/codelensoverview.png "CodeLensOverview")  
  
 Obraťte se na váš tým o změny kódu bez opuštění editoru:  
  
 ![Funkce CodeLens &#45; vám poskytne tým](../ide/media/codelensovervew2.png "CodeLensOvervew2")  
  
 Zvolte indikátory, které chcete zobrazit nebo vypněte a zapněte funkci CodeLens, přejděte na **nástroje**, **možnosti**, **textový Editor**, **všechny jazyky** , **CodeLens**.  
  
##  <a name="FindReferences"></a> Najít odkazy na kód  
 Budete potřebovat:  
  
- Visual Studio Enterprise nebo Professional sady Visual Studio  
  
- Kód Visual C# .NET nebo Visual Basic .NET  
  
  Zvolte **odkazy** ukazatel (**Alt + 2**). Pokud se zobrazí **0 odkazů**, nemáte žádné odkazy z kódu jazyka Visual C# nebo Visual Basic. Nejsou obsaženy odkazy z jiných položek, jako jsou soubory XAML a ASPX.  
  
  ![Funkce CodeLens &#45; zvolit indikátor odkazů](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  
  
  Chcete-li zobrazit kód odkazující, přesuňte ukazatel myši nad odkaz.  
  
  ![Funkce CodeLens &#45; náhled odkaz](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  
  
  K otevření souboru, který obsahuje odkaz, dvakrát klikněte na odkaz.  
  
  Chcete-li zobrazit vztahy mezi tímto kódem a jeho odkazy [Vytvořte mapu kódu](../modeling/map-dependencies-across-your-solutions.md) a zvolte **zobrazit všechny odkazy** v místní nabídce mapy kódu.  
  
  ![Funkce CodeLens &#45; odkazy na mapě kódu](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  
  
##  <a name="FindCodeHistory"></a> Vyhledejte historii vašeho kódu a propojené položky  
 Zkontrolujte historii vašeho kódu a zjistěte, co se stalo se váš kód. Nebo můžete zkontrolovat změny předtím, než se sloučí do kódu to vám umožní lépe pochopit změny v další větve, jak může ovlivnit váš kód.  
  
 Budete potřebovat:  
  
- Visual Studio Enterprise nebo Professional sady Visual Studio  
  
- Team Foundation Server 2013 nebo novější, Visual Studio Team Services nebo Git  
  
- [Lync 2010 nebo novější nebo Skype pro firmy](http://technet.microsoft.com/lync), ke kontaktování týmem z editoru kódu  
  
  Pro Visual C# .NET nebo Visual Basic .NET kód, který se uloží spolu s Team Foundation – správa verzí (TFVC) nebo Git, získání podrobností funkce CodeLens na úrovni třídy a metody (*úroveň element kódu* ukazatele). Pokud v TfGit je hostitelem vašeho úložiště Git, budete mít také odkazy na pracovní položky sady TFS.  
  
  ![Prvek kódu&#45;indikátory na úrovni](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  
  
  Pro všechny ostatní typy souborů, které lze otevřít v editoru sady Visual Studio získáte podrobností funkce CodeLens pro celý soubor na jednom místě v dolní části okna (*úrovni souboru* ukazatele).  
  
  ![Soubor&#45;indikátory CodeLens na úrovni](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  
  
  Použití klávesnice k výběru ukazatele, stiskněte a podržte **ALT** klíč k zobrazení souvisejících číslicemi.  
  
  ![Stiskněte klávesu ALT, abyste viděli čísla přístup klávesnice](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  
  
### <a name="find-changes-in-your-code"></a>Vyhledat změny v kódu  
 Najdete, kdo ho změnil vašeho jazyka C# nebo Visual Basic kódu a změny, které byly provedeny v úrovni element kódu ukazatele. Je to, co se zobrazí při použití Team Foundation version control (TFVC) na serveru Team Foundation Server nebo Visual Studio Team Services.  
  
 ![CodeLens: Get změnit historii vašeho kódu v TFVC](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  
  
 Výchozí časové období se za posledních 12 měsíců. Pokud je váš kód uložen v sadě Team Foundation Server, můžete to změnit spuštěním [příkazu TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62) s [codeindex – příkaz](../ide/codeindex-command.md) a **/indexHistoryPeriod** příznak.  
  
 Chcete-li zobrazit podrobnou historii všech změn, včetně těch, které z více než rokem, zvolte **zobrazit všechny změny souborů**.  
  
 ![Zobrazit všechny změny kódu](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  
  
 Tím se otevře v okně historie sady změn.  
  
 ![Okno historie u všech změn kódu](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  
  
 Když jsou soubory v úložišti Git a zvolte indikátor změn úroveň prvek kódu, tím se zobrazí.  
  
 ![CodeLens: Get změnit historii vašeho kódu v úložišti Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  
  
 Vyhledejte změny pro celý soubor (s výjimkou souborů C# a Visual Basic) v indikátory úrovni souboru v dolní části okna.  
  
 ![CodeLens: Získat kód podrobnosti o souborech](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  
  
 Pokud chcete získat další podrobnosti o změnu, klikněte pravým tlačítkem na danou položku. V závislosti na tom, zda používáte TFVC nebo Git získáte řadu možností porovnat verze souboru, zobrazit podrobnosti a sledovat sadu změn, získat vybranou verzi souboru a e-mail autora tuto změnu. Některé z těchto podrobností se zobrazí v Průzkumníku týmových projektů.  
  
 Můžete také zobrazit, kdo ho změnil kódu v čase. To může pomoct najít vzory ve změnách vašeho týmu a posoudit jejich dopad.  
  
 ![CodeLens: Změn kódu najdete v historii jako graf](../ide/media/codelens.png "CodeLens")  
  
#### <a name="find-changes-in-your-current-branch"></a>Vyhledat změny v aktuální větvi  
 Předpokládejme, že má váš tým v několika větvích – hlavní větve a vývoj podřízený - snížit riziko rozbíjející stabilní kód:  
  
 ![CodeLens: Vyhledání, pokud byl váš kód rozvětvených](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  
  
 Kolik lidí změnilo kódu a kolik změn (**Alt + 6**) v hlavní větvi:  
  
 ![CodeLens: Vyhledání, kolik změny ve vaší větvi](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  
  
#### <a name="find-when-your-code-was-branched"></a>Najít, pokud byl váš kód rozvětvených  
 Přejděte na svůj kód v podřízená větev, například poboček dev. tady. Vyberte indikátor změn (**Alt + 6**):  
  
 ![CodeLens: Vyhledání, pokud byl váš kód rozvětvených](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  
  
#### <a name="find-incoming-changes-from-other-branches"></a>Vyhledat příchozí změny další větve  
 ![CodeLens: Vyhledat změny kódu v jiných větvích](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  
  
 .. Tato oprava chyby v vývojový větev tady takto:  
  
 ![CodeLens: Změna zapsány do jiné větve](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  
  
 Aniž byste museli opustit aktuální větvi (hlavní) můžete zkontrolovat tuto změnu:  
  
 ![CodeLens: Viz příchozí změna z jiné větve](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  
  
#### <a name="find-when-changes-got-merged"></a>Najít, když máte změny sloučit  
 Abyste viděli, jaké změny jsou zahrnuté ve vaší větvi:  
  
 ![Funkce CodeLens &#45; sloučit změny mezi větvemi](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  
  
 Například váš kód v hlavní větvi teď má oprava chyby z větve Dev:  
  
 ![Funkce CodeLens &#45; sloučit chagnes mezi větvemi](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  
  
#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Porovnání příchozí změny s vaší místní verzi (Shift + F10)  
 ![CodeLens: Porovnání příchozí změny s místní](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  
  
 Můžete také dvakrát kliknout na sadu změn.  
  
#### <a name="what-do-the-icons-mean"></a>Co znamenají ikony  
  
|**Ikona**|**Pokud změnu pocházejí z?**|  
|--------------|-----------------------------------------|  
|![CodeLens: Změnit z aktuální větve ikona](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Aktuální větev|  
|![Funkce CodeLens &#45; změnit z nadřazené větve ikony](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Nadřazená větev|  
|![CodeLens: Změna z podřízené větve ikony](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Podřízené větve|  
|![Funkce CodeLens &#45; změnit z ikony sdílené větve](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Sdílené větve|  
|![Funkce CodeLens &#45; změnit z větve další tokeny ikony](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Další větve jinam než nadřazený, podřízený nebo partnera|  
|![CodeLens: Sloučení z nadřazené ikonu](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Sloučení z větve nadřazené do podřízené větve|  
|![CodeLens: Sloučení z podřízené větve ikonu](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Sloučení z podřízené větve do nadřazené větve|  
|![CodeLens: Sloučení z větve nesouvisejících ikony](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Sloučení z nesouvisejících větve (nepodložené sloučení)|  
  
### <a name="find-linked-work-items"></a>Vyhledání propojených pracovních položek  
 ![Funkce CodeLens &#45; hledání pracovních položek pro konkrétní kód](../ide/media/codelensworkitems.png "CodeLensWorkItems")  
  
### <a name="find-linked-code-reviews"></a>Vyhledání propojeného kódu revize  
 ![Funkce CodeLens &#45; zobrazení žádosti o revizi kódu](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  
  
### <a name="find-linked-bugs"></a>Vyhledání propojených chyb  
 ![Funkce CodeLens &#45; najít chyby spojené s sady změn](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  
  
### <a name="contact-the-owner-of-an-item"></a>Kontaktovat vlastníka položky  
 ![Kontaktovat vlastníka položky](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  
  
 Otevřete místní nabídku pro položku zobrazíte možností kontaktu. Pokud už máte, Lync nebo Skype pro firmy nainstalovaný, uvidíte tyto možnosti:  
  
 ![Obraťte se na možnosti pro položku](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  
  
##  <a name="FindRunUnitTests"></a> Vyhledání testů jednotek pro kód  
 Další informace o testování částí, které existují pro váš kód bez otevření Průzkumníka testů. Budete potřebovat:  
  
-   Visual Studio Enterprise nebo Professional sady Visual Studio  
  
-   Kód Visual C# .NET nebo Visual Basic .NET  
  
-   A [projekt testu jednotek](../test/unit-test-your-code.md) , který má testování částí pro kód aplikace  
  
1.  Přejděte ke kódu aplikace, který má testování částí.  
  
2.  Zkontrolujte testů pro tento kód (**Alt + 3**).  
  
     ![Funkce CodeLens &#45; stav testu zvolte v editoru kódu](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Pokud se zobrazí výstražná ikona ![CodeLens &#45; testování částí ještě nebyl spuštěn upozornění](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), spusťte testy.  
  
     ![Funkce CodeLens &#45; zobrazení testů jednotek není ještě spuštěna](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Zkontrolujte definici testu, dvakrát klikněte na položku testů v okno indikátor CodeLens v editoru otevřete soubor kódu.  
  
     ![Funkce CodeLens &#45; přejít k definici testu jednotek](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Zkontrolujte výsledky testu. Zvolte indikátor stavu testu (![CodeLens &#45; testování částí se nezdařilo – ikona](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") nebo ![CodeLens &#45; jednotky test proběhl úspěšně ikonu](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), nebo stiskněte klávesu **Alt + 1**.  
  
     ![Funkce CodeLens &#45; zobrazit výsledky testů jednotek](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Pokud chcete zobrazit, kolik lidí změnilo tento test, kdo změnil nebo kolik změny byly provedeny s tímto testem [vyhledejte historii vašeho kódu a propojené položky](#FindCodeHistory).  
  
##  <a name="QA"></a> Q & A  
  
###  <a name="ChangeOrTurnOff"></a> Otázka: jak nebo vypnutí zapnutí funkce CodeLens? Nebo zvolte které indikátory zobrazíte?  
 **Odpověď:** posunete ukazatele nebo vypnutí, s výjimkou indikátor odkazů. Přejděte na **nástroje**, **možnosti**, **textový Editor**, **všechny jazyky**, **CodeLens**.  
  
 Když jsou indikátory zapnuté, můžete také otevřít možnosti funkce CodeLens z indikátorů.  
  
 ![Funkce CodeLens &#45; indikátory zapnutí nebo vypnutí](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Indikátory CodeLens na úrovni souborů zapněte a vypnout pomocí ikony šipky v dolní části okna editoru.  
  
 ![Změnit soubor&#45;indikátory na úrovni zapnutí a vypnutí](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a> Otázka: kde je funkce CodeLens?  
 **Odpověď:** CodeLens se zobrazí v kódu jazyka Visual C# .NET a Visual Basic .NET na úrovni metody, třídy, indexerů a vlastnost. CodeLens se zobrazí na úrovni pro všechny ostatní typy souborů.  
  
-   Ujistěte se, že je zapnutá funkce CodeLens. Přejděte na **nástroje**, **možnosti**, **textový Editor**, **všechny jazyky**, **CodeLens**.  
  
-   Pokud je váš kód uložen v sadě TFS, ujistěte se, jestli indexování kódu je zapnutá pomocí [codeindex – příkaz](../ide/codeindex-command.md) s [příkaz TFS Config](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).  
  
-   Indikátory související s aplikací TFS se zobrazí pouze v případě, že jsou pracovní položky propojeny s kódem a máte oprávnění otevírat propojené pracovní položky. [Potvrďte, že máte oprávnění člena týmu.](http://msdn.microsoft.com/en-us/f58805de-ba61-4d09-8f2d-d3ab9662ecfd)  
  
-   Pokud kód aplikace nemá testování částí, nejsou zobrazeny indikátory testu jednotek. Indikátory stavu testu se automaticky zobrazí v projektech testů. Pokud víte, že váš kód aplikace má testování částí, ale nejsou zobrazeny indikátory testu, zkuste sestavit řešení (**Ctrl + Shift + B**).  
  
### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Otázka: Proč nevidím podrobnosti pracovní položky pro potvrzení změn?  
 **Odpověď:** příčinou může být funkce CodeLens nelze najít pracovní položky v TFS. Zkontrolujte, že jste připojeni k týmovému projektu, který má ty pracovní položky a zda máte oprávnění k zobrazení pracovní položky. To může dojít, pokud se popis potvrzení obsahuje nesprávné informace o ID pracovních položek v sadě TFS.  
  
###  <a name="NoLync"></a> Otázka: Proč nevidím indikátory služby Lync nebo Skype?  
 **Odpověď:** se nezobrazí, pokud ještě nejste k Lync nebo Skype pro firmy, není k dispozici jeden z nich nainstalovaný, nebo nemáte podporovanou konfiguraci. Ale stále můžete odesílat e-mailu:  
  
 ![Funkce CodeLens &#45; vlastník sady změn kontaktujte e-mailem](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  
  
 **Které konfigurace služby Lync a Skype se podporují?**  
  
- Skype pro firmy (32bitová nebo 64bitová verze)  
  
- Lync 2010 nebo novější samostatně (32bitová verze nebo 64bitovou), ale ne Lync Basic 2013 s Windows 8.1  
  
  Funkce CodeLens nepodporuje existenci různých verzí aplikace Lync nebo Skype nainstalované. Nemusí být lokalizována pro všechny lokalizované verze sady Visual Studio.  
  
### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Otázka: Jak mohu změnit písmo a barvu funkce codelens?  
 **Odpověď:** přejít na **nástroje**, **možnosti**, **prostředí**, **písma a barvy**.  
  
 ![Funkce CodeLens &#45; změnit nastavení písem a barev](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  
  
 Použití klávesnice:  
  
1.  Stisknutím klávesy **Alt + T + O** otevřít **možnosti** pole.  
  
2.  Stisknutím klávesy **šipka nahoru** nebo **šipka dolů** přejdete **prostředí** uzlu, stiskněte klávesu **šipka vlevo** rozbalte uzel.  
  
3.  Stisknutím klávesy **šipka dolů** přejdete na **písma a barvy**.  
  
4.  Stisknutím klávesy **kartu** přejdete **zobrazit nastavení pro** seznamu a potom stiskněte klávesu **šipka dolů** vyberte **CodeLens**.  
  
### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Otázka: Lze přesunout pohotové zobrazení funkce CodeLens?  
 **Odpověď:** Ano, zvolte ![CodeLens &#45; ukotvit jako okno](../ide/media/codelensdockwindow.png "CodeLensDockWindow") k dokování CodeLens jako okna.  
  
 ![Ukotvit okno na indikátor CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  
  
 ![Ukotvené odkazy CodeLens okno](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  
  
### <a name="q-how-do-i-refresh-the-indicators"></a>Otázka: Jak mohu aktualizovat indikátory?  
 **Odpověď:** to závisí na ukazatele:  
  
-   **Odkazy na**: Tento indikátor se aktualizuje automaticky při změně kódu. Pokud máte tento ukazatel jako samostatné okno ukotveno, aktualizujte indikátoru ručně tady:  
  
     ![Funkce CodeLens &#45; ukotvit jako okno](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  
  
-   **Tým**: aktualizovat tyto indikátory ručně tady:  
  
     ![Funkce CodeLens &#45; aktualizovat indikátory](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  
  
-   **Test**: [najít testy jednotek pro kód](#FindRunUnitTests) aktualizovat tento ukazatel.  
  
###  <a name="LocalVersion"></a> Otázka: co je "Místní verze"?  
 **Odpověď:** **místní verze** šipka ukazuje na poslední sady změn ve vaší místní verzi tohoto souboru. Pokud na serveru existují novější sady změn, zobrazují se nad nebo pod **místní verze** šipku, v závislosti na pořadí použitém k řazení sady změn.  
  
### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Dotaz: lze spravovat, jak funkce CodeLens zpracovává kód k zobrazení historie a propojené položky?  
 **Odpověď:** Ano, pokud je váš kód v TFS, použijte [codeindex – příkaz](../ide/codeindex-command.md) s [příkaz TFS Config](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62).




