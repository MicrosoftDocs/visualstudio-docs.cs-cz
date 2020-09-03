---
title: Hledání změn kódu a další historie pomocí CodeLens | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f697d7b4-704e-4cac-b13a-bc57d2ff8318
caps.latest.revision: 134
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8876a0a3c2b978443ee4bc74097dbc9fdd410b8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656005"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Nalezení změn kódu a další historie pomocí CodeLensu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sledujte svou práci a zjistěte, co se stalo s vaším kódem – bez nutnosti opustit Editor. Vyhledá odkazy a změny kódu, propojených chyb, pracovních položek, revizí kódu a testování částí.

> [!NOTE]
> CodeLens je k dispozici pouze v edicích Visual Studio Enterprise a Visual Studio Professional. Není k dispozici v edici Visual Studio Community Edition.

 Podívejte se, kde a jak se jednotlivé části kódu používají ve vašem řešení:

 ![Indikátory CodeLens v editoru kódu](../ide/media/codelensoverview.png "CodeLensOverview")

 Kontaktujte svůj tým o změnách kódu bez nutnosti opustit Editor:

 ![CodeLens &#45; kontaktujte tým.](../ide/media/codelensovervew2.png "CodeLensOvervew2")

 Chcete-li vybrat indikátory, které chcete zobrazit, nebo vypnout a zapnout CodeLens, přejděte do části **nástroje**, **Možnosti**, **textový editor**, **všechny jazyky**, **CodeLens**.

## <a name="find-references-to-your-code"></a><a name="FindReferences"></a> Vyhledat odkazy na váš kód
 Budete potřebovat:

- Visual Studio Enterprise nebo Visual Studio Professional

- Kód jazyka Visual C# .NET nebo Visual Basic .NET

  Vyberte indikátor **odkazů** (**ALT + 2**). Pokud vidíte **0 odkazů**, nemáte žádné odkazy z kódu jazyka Visual C# ani Visual Basic. To nezahrnuje odkazy z jiných položek, jako jsou soubory XAML a ASPX.

  ![CodeLens &#45; zvolit ukazatel na odkazy](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")

  Chcete-li zobrazit odkazující kód, přesuňte ukazatel myši nad odkaz.

  ![CodeLens &#45; náhledu – Referenční informace](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")

  Chcete-li otevřít soubor obsahující odkaz, dvakrát klikněte na odkaz.

  Chcete-li zobrazit vztahy mezi tímto kódem a jeho odkazy, [vytvořte mapu kódu](../modeling/map-dependencies-across-your-solutions.md) a v místní nabídce mapa kódu vyberte možnost **Zobrazit všechny odkazy** .

  ![CodeLens &#45; odkazy na mapu kódu](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")

## <a name="find-your-codes-history-and-linked-items"></a><a name="FindCodeHistory"></a> Vyhledání historie kódu a propojených položek
 Podívejte se na historii kódu a zjistěte, co se stalo s vaším kódem. Nebo můžete zkontrolovat změny před jejich sloučením do kódu, abyste lépe pochopili, jakým způsobem mohou změny v jiných větvích ovlivnit váš kód.

 Budete potřebovat:

- Visual Studio Enterprise nebo Visual Studio Professional

- Team Foundation Server 2013 nebo novější, Visual Studio Team Services nebo Git

- [Lync 2010 nebo novější nebo Skype pro firmy](https://technet.microsoft.com/lync)pro kontaktování týmu z editoru kódu

  Pro kód jazyka Visual C# .NET nebo Visual Basic .NET, který je uložený s nástrojem Team Foundation – správa verzí (TFVC) nebo Git, získáte CodeLens podrobnosti na úrovni třídy a metody (indikátory*na úrovni kódu-elementu* ). Pokud je vaše úložiště Git hostované v TfGit, získáte také odkazy na pracovní položky sady TFS.

  ![Prvek kódu&#45;indikátory úrovně](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")

  Pro všechny ostatní typy souborů, které můžete otevřít v editoru sady Visual Studio, získáte CodeLens podrobnosti o celém souboru na jednom místě v dolní části okna (indikátory na*úrovni souborů* ).

  ![Indikátory CodeLens&#45;úrovně souboru](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")

  Chcete-li použít klávesnici k výběru indikátorů, stiskněte a podržte klávesu **ALT** pro zobrazení souvisejících číselných klíčů.

  ![Stisknutím klávesy ALT zobrazíte čísla pro přístup k klávesnicím.](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")

### <a name="find-changes-in-your-code"></a>Hledání změn v kódu
 Zjistěte, kdo změnil kód v jazyce C# nebo Visual Basic a změny provedené v indikátorech na úrovni kódu prvku. To je to, co vidíte při použití správy verzí Team Foundation (TFVC) v Team Foundation Server nebo Visual Studio Team Services.

 ![CodeLens: Získá historii změn kódu v TFVC.](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")

 Výchozí časové období je posledních 12 měsíců. Pokud je váš kód uložen v Team Foundation Server, můžete to změnit spuštěním [příkazu TFSConfig](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) pomocí [příkazu CodeIndex –](../ide/codeindex-command.md) a příznaku **/indexHistoryPeriod** .

 Chcete-li zobrazit podrobné informace o všech změnách, včetně těch, které jsou před více než rokem, vyberte možnost **Zobrazit všechny změny souborů**.

 ![Zobrazit všechny změny kódu](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")

 Tím se otevře okno historie pro sady změn.

 ![Okno historie pro všechny změny kódu](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")

 Když jsou soubory v úložišti Git a Vy zvolíte indikátor změny na úrovni kódu prvku, zobrazí se to, co vidíte.

 ![CodeLens: Získá historii změn kódu v Gitu.](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")

 Vyhledá změny celého souboru (kromě C# a Visual Basic souborů) v indikátorech na úrovni souboru v dolní části okna.

 ![CodeLens: Získání podrobností souboru s kódem](../ide/media/codelensfilelevel.png "CodeLensFileLevel")

 Chcete-li získat další informace o změně, klikněte pravým tlačítkem myši na danou položku. V závislosti na tom, jestli používáte TFVC nebo Git získáte řadu možností, jak porovnat verze souboru, zobrazit podrobnosti a sledovat sadu změn, získat vybranou verzi souboru a poslat e-mail autorovi této změny. Některé z těchto podrobností se zobrazí v Team Explorer.

 Můžete také zjistit, kdo změnil kód v průběhu času. To vám může pomáhat najít vzorce ve změnách týmu a posoudit jejich dopad.

 ![CodeLens: Zobrazení historie změn kódu jako grafu](../ide/media/codelens.png "CodeLens")

#### <a name="find-changes-in-your-current-branch"></a>Vyhledat změny v aktuální větvi
 Předpokládejme, že váš tým má více větví – hlavní větev a podřízený vývoj – ke snížení rizika poškození stabilního kódu:

 ![CodeLens: najít, kdy byl kód v větve](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")

 Zjistěte, kolik lidí změnil váš kód a kolik změn bylo provedeno (**ALT + 6**) ve vaší hlavní větvi:

 ![CodeLens: najít počet změn ve větvi](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")

#### <a name="find-when-your-code-was-branched"></a>Najít, kdy byl kód v větvení
 Přejít k vašemu kódu v podřízené větvi, například do vývojové větve. Vyberte indikátor změn (**ALT + 6**):

 ![CodeLens: najít, kdy byl kód v větve](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")

#### <a name="find-incoming-changes-from-other-branches"></a>Najít příchozí změny z jiných větví
 ![CodeLens: najít změny kódu v dalších větvích](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")

 ... Líbí se vám tato oprava chyby ve větvi pro vývojáře:

 ![CodeLens: Změna kontrolovaného na jinou větev](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")

 Tuto změnu můžete zkontrolovat bez nutnosti opustit aktuální větev (hlavní):

 ![CodeLens: viz příchozí změna z jiné větve](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")

#### <a name="find-when-changes-got-merged"></a>Najít, kdy byly změny sloučeny
 Takže uvidíte, které změny jsou ve vaší větvi zahrnuty:

 ![CodeLens &#45; sloučily změny mezi větvemi.](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")

 Například váš kód v hlavní větvi teď obsahuje opravu chyby z vývojové větve:

 ![CodeLens &#45; sloučil chagnes mezi větvemi](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Porovnání příchozí změny s místní verzí (Shift + F10)
 ![CodeLens: porovná příchozí změnu s místními](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")

 Můžete také dvakrát kliknout na sadu změn.

#### <a name="what-do-the-icons-mean"></a>Co znamenají ikony?

|**Ikona**|**Kde tato změna pocházela?**|
|--------------|-----------------------------------------|
|![CodeLens: ikona změnit z aktuální větve](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Aktuální větev|
|![Ikona změny CodeLens &#45; z nadřazené větve](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Nadřazená větev|
|![CodeLens: ikona změnit z podřízené větve](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Podřízená větev|
|![Ikona změny CodeLens &#45; z partnerské větve](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Rovnocenná větev|
|![Ikona změny CodeLens &#45; z větve dál](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Větev, která je dále volná, podřízená nebo rovnocenná|
|![CodeLens: ikona sloučení z nadřazené položky](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Sloučení z nadřazené větve do podřízené větve|
|![CodeLens: ikona sloučení z podřízené větve](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Sloučení z podřízené větve do nadřazené větve|
|![CodeLens: ikona sloučení z nesouvisející větve](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Sloučení z nesouvisející větve (sloučení neopodstatněné)|

### <a name="find-linked-work-items"></a>Hledání propojených pracovních položek
 ![CodeLens &#45; najít pracovní položky pro konkrétní kód](../ide/media/codelensworkitems.png "CodeLensWorkItems")

### <a name="find-linked-code-reviews"></a>Hledání propojených revizí kódu
 ![CodeLens &#45; zobrazit žádosti o revizi kódu](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")

### <a name="find-linked-bugs"></a>Najít propojené chyby
 ![CodeLens &#45; nalezení chyb propojených se sadami změn](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")

### <a name="contact-the-owner-of-an-item"></a>Obraťte se na vlastníka položky.
 ![Obraťte se na vlastníka položky.](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")

 Otevřete místní nabídku pro položku, abyste viděli možnosti kontaktů. Pokud máte nainstalovaný Lync nebo Skype pro firmy, zobrazí se tyto možnosti:

 ![Možnosti kontaktu pro položku](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")

## <a name="find-unit-tests-for-your-code"></a><a name="FindRunUnitTests"></a> Najde testy jednotek pro váš kód.
 Přečtěte si další informace o testech jednotek, které existují pro váš kód bez otevření Průzkumníka testů. Budete potřebovat:

- Visual Studio Enterprise nebo Visual Studio Professional

- Kód jazyka Visual C# .NET nebo Visual Basic .NET

- [Projekt testování částí](../test/unit-test-your-code.md) , který obsahuje jednotkové testy pro kód aplikace

1. Přejděte ke kódu aplikace, který má testování částí.

2. Zkontrolujte testy pro daný kód (**ALT + 3**).

     ![CodeLens &#45; zvolit stav testu v editoru kódu](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")

3. Pokud se zobrazí výstražná ikona ![CodeLens &#45; testy jednotek ještě neběžely](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), spusťte testy.

     ![CodeLens &#45; zobrazení testů jednotek ještě neběželo](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")

4. Chcete-li zkontrolovat definici testu, dvakrát klikněte na položku Test v okně indikátor CodeLens a otevřete soubor kódu v editoru.

     ![CodeLens &#45; přejít k definici testování částí](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")

5. Zkontrolujte výsledky testu. Zvolte indikátor stavu testu (![CodeLens &#45; ikona neúspěšného testu jednotky](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") nebo ![předaná ikona &#45; CodeLens testu jednotky](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")) nebo stiskněte **kombinaci kláves ALT + 1**.

     ![CodeLens &#45; zobrazit výsledek testu jednotek](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")

6. Chcete-li zjistit, kolik lidí změnilo tento test, kdo tento test změnil nebo kolik změn bylo provedeno v tomto testu, [Najděte historii kódu a propojené položky](#FindCodeHistory).

## <a name="q--a"></a><a name="QA"></a> OTÁZKA & A

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a><a name="ChangeOrTurnOff"></a> Otázka: Návody vypnout nebo zapnout CodeLens? Nebo vyberte, které indikátory chcete zobrazit?
 **A:**  Můžete zapnout nebo vypnout indikátory, s výjimkou indikátoru odkazů. V **nabídce nástroje**, **Možnosti**, **textový editor**, **všechny jazyky**, **CodeLens**.

 Když jsou indikátory zapnuté, můžete také otevřít možnosti CodeLens z indikátorů.

 ![CodeLens &#45; zapnout nebo vypnout indikátory](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")

 Zapne nebo vypne indikátory CodeLens na úrovni souboru pomocí ikon dvojitých šipek v dolní části okna editoru.

 ![Zapnout a vypnout indikátory na úrovni souboru&#45;](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")

### <a name="q-where-is-codelens"></a><a name="NoIndicators"></a> Otázka: kde je CodeLens?
 **A:** CodeLens se zobrazí v kódu Visual C# .NET a Visual Basic .NET na úrovni metody, třídy, indexeru a vlastnosti. CodeLens se zobrazí na úrovni souboru pro všechny ostatní typy souborů.

- Ujistěte se, že je zapnutá funkce CodeLens. V **nabídce nástroje**, **Možnosti**, **textový editor**, **všechny jazyky**, **CodeLens**.

- Pokud je váš kód uložen na serveru TFS, ujistěte se, že je zapnuto indexování kódu pomocí [příkazu CodeIndex –](../ide/codeindex-command.md) s [příkazem konfigurace serveru TFS](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).

- Indikátory související s aplikací TFS se zobrazí pouze v případě, že jsou pracovní položky propojeny s kódem a máte oprávnění otevírat propojené pracovní položky. [Potvrďte, že máte oprávnění člena týmu.](/azure/devops/organizations/security/view-permissions)

- Indikátory testu jednotek se nezobrazí, pokud kód aplikace nemá testy jednotek. Indikátory stavu testu se automaticky zobrazí v projektech testů. Pokud víte, že váš kód aplikace má testy jednotek, ale nezobrazují se indikátory testu, zkuste sestavit řešení (**CTRL + SHIFT + B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Otázka: Proč se mi nezobrazuje podrobnosti o pracovní položce pro potvrzení?
 **A:** K tomu může dojít, protože CodeLens nemůže najít pracovní položky v TFS. Zkontrolujte, zda jste připojeni k týmovému projektu, který obsahuje tyto pracovní položky a zda máte oprávnění k zobrazení pracovních položek. K tomu může dojít také v případě, že popis potvrzení obsahuje nesprávné informace o ID pracovní položky v TFS.

### <a name="q-why-dont-i-see-the-lync-or-skype-indicators"></a><a name="NoLync"></a> Otázka: Proč nevidím indikátory pro Lync nebo Skype?
 **A:** Neobjeví se, pokud nejste přihlášení do služby Lync nebo Skypu pro firmy, nemáte žádnou z těchto nainstalovaných nebo nemáte podporovanou konfiguraci. I když ale můžete poslat e-mail:

 ![CodeLens &#45; kontaktování vlastníka sady změn e-mailem](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")

 **Které konfigurace pro Lync a Skype jsou podporované?**

- Skype pro firmy (32-bit nebo 64)

- Lync 2010 nebo novější (32-bit nebo 64-bit), ale ne Lync Basic 2013 s Windows 8.1

  CodeLens nepodporuje nainstalovanou jinou verzi Lyncu nebo Skype. Nemusí být lokalizovány pro všechny lokalizované verze sady Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Otázka: Návody změnit písmo a barvu pro CodeLens?
 **A:** V **nabídce nástroje**, **Možnosti**, **prostředí**, **písma a barvy**.

 ![CodeLens &#45; změnit nastavení písma a barev](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")

 Použití klávesnice:

1. Stisknutím **kombinace kláves ALT + T + O** otevřete pole **Možnosti** .

2. Stisknutím klávesy **šipka nahoru** nebo **šipka dolů** přejděte k uzlu **prostředí** a stisknutím klávesy **šipka vlevo** rozbalte uzel.

3. Stisknutím klávesy **šipka dolů** přejděte na **písma a barvy**.

4. Stisknutím klávesy **TAB** přejděte do seznamu **Zobrazit nastavení pro** a potom stisknutím klávesy **šipka dolů** vyberte možnost **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Otázka: Lze přesunout pohotové zobrazení funkce CodeLens?
 **A:** Ano, vyberte ![CodeLens &#45; Dock jako okno](../ide/media/codelensdockwindow.png "CodeLensDockWindow") pro ukotvení CodeLens jako okna.

 ![Ukotvit okno indikátoru CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")

 ![Okno s odkazy na ukotvené CodeLens](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")

### <a name="q-how-do-i-refresh-the-indicators"></a>Otázka: Jak mohu aktualizovat indikátory?
 **A:** To závisí na indikátoru:

- **Odkazy**: Tento indikátor se automaticky aktualizuje při změně kódu. Pokud je tento indikátor ukotven jako samostatné okno, aktualizujte indikátor ručně tady:

     ![CodeLens &#45; Dock jako okno](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")

- **Tým**: aktualizujte tyto indikátory ručně tady:

     ![Indikátory aktualizace CodeLens &#45;](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")

- **Test**: [vyhledejte testy jednotek kódu](#FindRunUnitTests) pro aktualizaci tohoto indikátoru.

### <a name="q-whats-local-version"></a><a name="LocalVersion"></a> Otázka: co je místní verze?
 **A:** Šipka **místní verze** ukazuje na nejnovější sadu změn v místní verzi tohoto souboru. Pokud má server novější sady změn, zobrazí se nad nebo pod šipkou **místní verze** v závislosti na pořadí použitém k řazení sad změn.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Otázka: mohu spravovat způsob, jakým CodeLens zpracovává kód pro zobrazení historie a propojených položek?
 **A:** Ano, pokud je váš kód v TFS, použijte [příkaz CodeIndex –](../ide/codeindex-command.md) pomocí [příkazu TFS config](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62).
