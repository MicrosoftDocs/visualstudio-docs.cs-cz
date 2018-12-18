---
title: Nalezení změn kódu a další historie pomocí CodeLensu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e11b7458c5d26d56252b228522c53b00ebadb35b
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220297"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Nalezení změn kódu a další historie pomocí CodeLensu

CodeLens vám umožňuje soustředit se na svou práci při můžete zjistit, co se stalo se váš kód&ndash;bez opuštění editoru. Můžete najít odkazy na část kódu, změny kódu, propojené chyby, pracovní položky, revize kódu a testy jednotek.

> [!NOTE]
> CodeLens je k dispozici pouze v edicích sady Visual Studio Enterprise a Visual Studio Professional. Není k dispozici v aplikaci Visual Studio Community edition.

V tématu, kde a jak se ve vašem řešení používají jednotlivé části kódu:

![Indikátory CodeLens v editoru kódu](../ide/media/codelens-overview.png)

Obraťte se na váš tým o změny kódu bez opuštění editoru:

![Funkce CodeLens - vám poskytne tým](../ide/media/codelens-contact-info.png)

Zvolte indikátory, které chcete zobrazit nebo vypněte a zapněte funkci CodeLens, přejděte na **nástroje** > **možnosti** > **textový Editor**  >  **Všechny jazyky** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Najít odkazy na kód

Najít odkazy v jazyce C# nebo kódu jazyka Visual Basic.

1. Zvolte **odkazy** ukazatel nebo stisknutím klávesy **Alt**+**2**.

   ![Odkazy na funkce CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Pokud se indikátor zobrazuje **0 odkazů**, nemáte žádné odkazy z kódu jazyka C# nebo Visual Basic. Však nemusí některé odkazy v jiné položky, jako *.xaml* a *.aspx* soubory.

2. Chcete-li zobrazit kód odkazující myši nad odkaz v seznamu.

   ![CodeLens - náhledu odkazu](../ide/media/codelens-peek-reference.png)

3. K otevření souboru, který obsahuje odkaz na, dvakrát klikněte na odkaz.

### <a name="code-maps"></a>Mapy kódu

Chcete-li zobrazit vztahy mezi kódem a jeho odkazy [Vytvořte mapu kódu](../modeling/map-dependencies-across-your-solutions.md). V místní nabídce mapy kódu vyberte **zobrazit všechny odkazy**.

![Funkce CodeLens – odkazy na mapě kódu](../ide/media/codelensmappedreferences.png)

## <a name="a-namefind-code-historyfind-changes-in-your-code"></a><a name="find-code-history"/>Vyhledat změny v kódu

Prozkoumejte historii vašeho kódu a zjistěte, co se stalo se váš kód. Nebo můžete zkontrolovat změny předtím, než se sloučí do kódu to vám umožní lépe pochopit změny v další větve, jak může ovlivnit váš kód.

Potřebuješ:

- Visual Studio Enterprise nebo Professional sady Visual Studio

- Team Foundation Server 2013 nebo novější, Azure DevOps Services nebo Git

- [Skype pro firmy](/skypeforbusiness/) kontaktovat týmem z editoru kódu

Pro kód jazyka C# nebo Visual Basic, který se uloží spolu s Team Foundation verze ovládacího prvku (TFVC) nebo Git, získání podrobností funkce CodeLens na úrovni třídy a metody (*úrovni element kódu* ukazatele). Pokud v TfGit je hostitelem vašeho úložiště Git, budete mít také odkazy na pracovní položky sady TFS.

![Indikátory na úrovni element Code](../ide/media/codelens-element-level-indicators.png)

Pro soubor typy jiné než *.cs* nebo *.vb*, získání podrobností funkce CodeLens pro celý soubor na jednom místě v dolní části okna (*úrovni souboru* ukazatele).

![Indikátory CodeLens na úrovni souborů](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indikátory na úrovni element Code

Kód indikátory na úrovni prvku vám umožní vidět, kdo ho změnil kód a jaké změny byly provedeny. Indikátory na úrovni prvku kódu jsou k dispozici pro kód jazyka C# a Visual Basic.

Je to, co se zobrazí při použití Team Foundation verze ovládacího prvku (TFVC) v Team Foundation Server nebo ve službách Azure DevOps:

![CodeLens: Získat historii změn pro svůj kód v TFVC](../ide/media/codelens-code-changes.png)

Výchozí časové období se za posledních 12 měsíců. Pokud je váš kód uložen v sadě Team Foundation Server, můžete změnit časové období spuštěním [příkazu TFSConfig](/tfs/server/ref/command-line/tfsconfig-cmd) s [codeindex – příkaz](../ide/codeindex-command.md) a **/indexHistoryPeriod**příznak.

Chcete-li zobrazit podrobnou historii všech změn, včetně těch, které z více než rokem, zvolte **zobrazit všechny změny souborů**:

![Zobrazit všechny změny kódu](../ide/media/codelens-show-all-file-changes.png)

**Historie** otevře se okno:

![Okno historie u všech změn kódu](../ide/media/codelenscodechangeshistory.png)

Když jsou soubory v úložišti Git a zvolte indikátor změn na úrovni prvku kódu, tím se zobrazí:

![CodeLens: Získat historii změn pro svůj kód v Gitu](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indikátory na úrovni souboru

Vyhledejte změny pro celý soubor v indikátory úrovni souboru v dolní části okna:

![CodeLens: Podrobnosti o souborech získat kód](../ide/media/codelens-file-level.png)

> [!NOTE]
> Indikátory na úrovni souboru nejsou k dispozici pro soubory C# a Visual Basic.

Pokud chcete získat další podrobnosti o změnu, klikněte pravým tlačítkem na danou položku. V závislosti na tom, jestli používáte TFVC nebo Git jsou možnosti, jak porovnat verze souboru, zobrazit podrobnosti a sledovat sadu změn, získat vybranou verzi souboru a e-mail autora tuto změnu. Některé z těchto podrobností se zobrazují v **Team Exploreru**.

Můžete také zobrazit, kdo ho změnil kódu v čase. To může pomoct najít vzory ve změnách vašeho týmu a posoudit jejich dopad.

![CodeLens: Zobrazit historii změn kódu jako graf](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Vyhledat změny v aktuální větvi

Váš tým může mít několik větví, například hlavní větev i podřízené větvení vývoje, aby se snížilo riziko narušení stabilní kód.

![CodeLens: Vyhledání, pokud byl váš kód rozvětvených](../ide/media/codelensfirstbranchconceptual.png)

Můžete zjistit, kolik lidí změnilo kódu a kolik změny byly provedeny v hlavní větvi stisknutím kombinace kláves **Alt**+**6**:

![CodeLens: Najdete kolik změn ve větvi](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Najít, pokud byl váš kód rozvětvených

K vyhledání, pokud byl váš kód rozvětvených, přejděte na svůj kód v podřízené větve. Vyberte **změny** ukazatel nebo stisknutím klávesy **Alt**+**6**:

![CodeLens: Vyhledání, pokud byl váš kód rozvětvených](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Vyhledat příchozí změny další větve

![CodeLens: Vyhledat změny kódu v jiných větvích](../ide/media/codelensbranchchangecheckinconceptual.png)

Příchozí změny si můžete prohlédnout. Na následujícím snímku obrazovky oprava chyby proběhla ve větvi "Dev":

![CodeLens: Změna zapsány do jiné větve](../ide/media/codelens-branch-changes-dev.png)

Aniž byste museli opustit aktuální větvi ("hlavní") můžete zkontrolovat změny:

![CodeLens: Viz příchozí změna z jiné větve](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Najít, když máte změny sloučit

Můžete zobrazit, když máte změny sloučit, aby mohl určit, jaké změny jsou zahrnuté ve vaší větvi:

![CodeLens - sloučení změn mezi větvemi](../ide/media/codelensbranchmergedconceptual.png)

Například váš kód v hlavní větvi teď má oprava chyby z větve "Dev":

![CodeLens - sloučení změn mezi větvemi](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porovnání příchozí změny s místní verzí

Porovnání příchozí změny s místní verzí stisknutím kombinace kláves **Shift**+**F10**, nebo na něj poklikejte sadu změn.

![CodeLens: Porovnání příchozí změny s místní](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony větve

Na ikonu **větev** sloupec vám říká, jak se vztahuje větev do větve, ve které pracujete.

|**Ikona**|**Tato změna pochází:**|
|--------------| - |
|![CodeLens: Změna z aktuální větve ikony](../ide/media/codelensbranchcurrenticon.png)|Aktuální větev|
|![CodeLens: Změna z nadřazené větve ikony](../ide/media/codelensbranchparenticon.png)|Nadřazená větev|
|![CodeLens: Změna z podřízené větve ikony](../ide/media/codelensbranchchildicon.png)|Podřízené větve|
|![CodeLens: Změna z ikony sdílené větve](../ide/media/codelensbranchpeericon.png)|Sdílené větve|
|![CodeLens: Změn z větve další tokeny ikony](../ide/media/codelensbranchfurtherawayicon.png)|Další větve jinam než nadřazený, podřízený nebo partnera|
|![CodeLens: Sloučení z nadřazené ikony](../ide/media/codelensbranchmergefromparenticon.png)|Sloučení z větve nadřazené do podřízené větve|
|![CodeLens: Sloučení z podřízené větve ikony](../ide/media/codelensbranchmergefromchildicon.png)|Sloučení z podřízené větve do nadřazené větve|
|![CodeLens: Sloučení z větve nesouvisejících ikony](../ide/media/codelensbranchmergefromunrelatedicon.png)|Sloučení z nesouvisejících větve (nepodložené sloučení)|

## <a name="linked-work-items"></a>Propojené pracovní položky

Vyhledání propojených pracovních položek tak, že vyberete **pracovní položky** ukazatele nebo stisknutím klávesy **Alt**+**8**.

![Funkce CodeLens – hledání pracovních položek pro konkrétní kód](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Revize kódu propojené

Vyhledání propojeného kódu kontroly tak, že vyberete **kontroly** indikátoru. Použití klávesnice, podržte stisknutou **Alt** klíče a potom stiskněte klávesu **šipku vlevo** nebo **šipku vpravo** přejděte na možnosti indikátoru.

![Kontrola žádostí o funkce CodeLens - zobrazení kódu](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Propojené chyby

Vyhledání propojených chyb tak, že vyberete **chyby** ukazatele nebo stisknutím klávesy **Alt**+**7**.

![CodeLens - najít chyby spojené s sady změn](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Kontaktovat vlastníka položky

Najděte autora položky výběrem indikátoru **autorů** nebo stisknutím klávesy **Alt**+**5**.

![Kontaktovat vlastníka položky](../ide/media/codelens-contact-item-owner.png)

Otevřete místní nabídku pro položku zobrazíte možností kontaktu. Pokud už máte, Lync nebo Skype pro firmy nainstalovaný, uvidíte tyto možnosti:

![Obraťte se na možnosti pro položku](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Testy přidružených jednotek

Může zjišťovat testy jednotek, které existují bez spuštění kódu jazyka C# nebo Visual Basic **Průzkumník testů**.

1. Přejděte do aplikace kód, který je spojen [kód testu jednotek](../test/unit-test-your-code.md).

2. Pokud nemáte, sestavení aplikace načíst indikátory CodeLens na test. Ujistěte se, že [zjišťování z vytvořených sestavení](../test/test-explorer-faq.md#assembly-based-discovery) zapnutý.

3. Zkontrolujte testy Code stisknutím kombinace kláves **Alt**+**3**.

     ![Zvolte CodeLens – stav testu v editoru kódu](../ide/media/codelens-choose-test-indicator.png)

4. Pokud se zobrazí výstražná ikona ![Ikona upozornění](../ide/media/codelenstestwarningicon.png), testy nebyly spustit ještě tak jejich spuštění.

     ![CodeLens – zobrazení testů jednotek není ještě spuštěna](../ide/media/codelens-tests-not-yet-run.png)

5. Zkontrolujte definici testu, dvakrát klikněte na položku testů v okno indikátor CodeLens v editoru otevřete soubor kódu.

     ![Funkce CodeLens - přejít k definici testu jednotek](../ide/media/codelens-unit-test-definition.png)

6. Chcete-li zobrazit výsledky testu, zvolte indikátor stavu testu (![ikona selhání testu](../ide/media/codelenstestfailedicon.png) nebo ![test prošel ikonu](../ide/media/codelenstestpassedicon.png)), nebo stiskněte klávesu **Alt**+**1**.

     ![Funkce CodeLens – viz výsledky testů jednotek](../ide/media/codelens-unit-test-result.png)

7. Pokud chcete zobrazit, kolik lidí změnilo tento test, kdo změnil nebo kolik změny byly provedeny s tímto testem [najít historii vašeho kódu](#find-code-history) a propojené položky.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Chcete-li vybrat ukazatele pomocí klávesnice, stiskněte a podržte **Alt** klíč k zobrazení souvisejících počet klíčů a potom stiskněte klávesu číslo, které odpovídá ukazatele, které chcete vybrat.

![Čísla přístup klávesnice](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Vyberte **kontroly** ukazatel, podržte stisknutou klávesu **Alt** při použití klávesy šipka doleva a doprava pro navigaci.

## <a name="q--a"></a>Dotazy a odpovědi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Otázka: jak funkce CodeLens zapnutí nebo vypnutí, nebo zvolte které indikátory zobrazíte?

**Odpověď:** posunete ukazatele nebo vypnutí, s výjimkou indikátor odkazů. Přejděte na **nástroje** > **možnosti** > **textový Editor** > **všechny jazyky**  >  **CodeLens**.

Když jsou indikátory zapnuté, můžete také otevřít možnosti funkce CodeLens z indikátorů.

![CodeLens - indikátory zapnutí nebo vypnutí](../ide/media/codelensturnoffonindicatorsfromcode.png)

Indikátory CodeLens na úrovni souborů zapněte a vypnout pomocí ikony šipky v dolní části okna editoru.

![Zapnutí a vypnutí indikátory na úrovni souboru](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>Otázka: kde je funkce CodeLens?

**Odpověď:** CodeLens se zobrazí v kódu jazyka C# a Visual Basic na úrovni metody, třídy, indexerů a vlastnost. CodeLens se zobrazí na úrovni pro všechny ostatní typy souborů.

- Ujistěte se, že je zapnutá funkce CodeLens. Přejděte na **nástroje** > **možnosti** > **textový Editor** > **všechny jazyky**  >  **CodeLens**.

- Pokud je váš kód uložen v sadě TFS, ujistěte se, jestli indexování kódu je zapnutá pomocí [codeindex – příkaz](../ide/codeindex-command.md) s [příkaz TFS Config](/tfs/server/ref/command-line/tfsconfig-cmd).

- Indikátory související s DevOps aplikací zobrazí pouze v případě, že jsou pracovní položky propojeny s kódem a v případě, že máte oprávnění k otevření propojené pracovní položky. Potvrďte, že máte [oprávnění člena týmu](/azure/devops/organizations/security/view-permissions?view=vsts).

- Pokud kód aplikace nemá testování částí, nejsou zobrazeny indikátory testu jednotek. Indikátory stavu testu se automaticky zobrazí v projektech testů. Pokud víte, že váš kód aplikace má testování částí, ale nejsou zobrazeny indikátory testu, zkuste sestavit řešení (**Ctrl**+**Shift**+**B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Otázka: Proč nevidím podrobnosti pracovní položky pro potvrzení změn?

**Odpověď:** příčinou může být funkce CodeLens nelze najít pracovní položky v panely Azure nebo v sadě TFS. Zkontrolujte, že jste připojeni k projektu, který má ty pracovní položky, a zda máte oprávnění k zobrazení ty pracovní položky. Podrobnosti o pracovní položce nemusí také zobrazit, pokud popis potvrzení obsahuje nesprávné informace o ID v Azure tabulí nebo TFS pracovních položek.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>Otázka: Proč nevidím indikátory Skype?

**Odpověď:** nejsou zobrazeny indikátory Skype, jestliže nejste přihlášeni ke Skypu pro firmy, nemáte ji nainstalovánu nebo nemáte podporovanou konfiguraci. Stále však můžete odesílat e-mailu:

![Funkce CodeLens – vlastník sady změn kontaktujte e-mailem](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Které konfigurace Skypu a Lync jsou podporovány?**

- Skype pro firmy (32bitová nebo 64bitová verze)

- Lync 2010 nebo novější samostatně (32bitová verze nebo 64bitovou), ale ne Lync Basic 2013 s Windows 8.1

Funkce CodeLens nepodporuje existenci různých verzí aplikace Lync nebo Skype nainstalované. Nemusí být lokalizována pro všechny lokalizované verze sady Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Otázka: Jak mohu změnit písmo a barvu funkce codelens?

**Odpověď:** přejít na **nástroje** > **možnosti** > **prostředí** > **písma a barvy**.

![Funkce CodeLens - změnit nastavení písma a barvy](../ide/media/codelensoptionsfontscolorssettings.png)

Použití klávesnice:

1. Stisknutím klávesy **Alt**+**T**+**O** otevřít **možnosti** dialogové okno.

2. Stisknutím klávesy **šipka nahoru** nebo **šipka dolů** přejdete **prostředí** uzlu, stiskněte klávesu **šipka vlevo** rozbalte uzel.

3. Stisknutím klávesy **šipka dolů** přejdete na **písma a barvy**.

4. Stisknutím klávesy **kartu** přejdete **zobrazit nastavení pro** seznamu a potom stiskněte klávesu **šipka dolů** vyberte **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Otázka: Lze přesunout pohotové zobrazení funkce CodeLens?

**O:** Ano, zvolte ![Dock ikonu](../ide/media/codelensdockwindow.png) k dokování CodeLens jako okna.

![Ukotvit tlačítka v okně indikátor CodeLens](../ide/media/codelensselectdockwindow.png)

![Ukotvené odkazy CodeLens okno](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Otázka: Jak mohu aktualizovat indikátory?

**Odpověď:** to závisí na ukazatele:

- **Odkazy na**: Tento indikátor se aktualizuje automaticky při změně kódu. Pokud **odkazy** indikátor je ukotven jako samostatné okno, aktualizovat tak, že vyberete indikátoru **aktualizovat**:

     ![Aktualizovat odkazy CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Tým**: tyto indikátory aktualizovat tak, že vyberete **aktualizovat indikátory týmu funkce CodeLens** v místní nabídce:

     ![Aktualizujte indikátory týmu funkce CodeLens položky nabídky](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [najít testy jednotek pro kód](#associated-unit-tests) aktualizovat **Test** indikátoru.

### <a name="q-whats-local-version"></a>Otázka: co je "Místní verze"?

**Odpověď:** **místní verze** šipka ukazuje na poslední sady změn ve vaší místní verzi souboru. Pokud na serveru existují novější sady změn, zobrazují se nad nebo pod **místní verze** šipku, v závislosti na pořadí použitém k řazení sady změn.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Dotaz: lze spravovat, jak funkce CodeLens zpracovává kód k zobrazení historie a propojené položky?

**Odpověď:** Ano. Pokud je váš kód v TFS, použijte [codeindex – příkaz](../ide/codeindex-command.md) s [příkaz TFS Config](/tfs/server/ref/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>Otázka: Moje funkce CodeLens zobrazeny indikátory testu už v souboru při prvním otevření Moje řešení. Jak je můžete je načíst?

**Odpověď:** znovu sestavit projekt získat indikátory CodeLens testu načíst v souboru. Ujistěte se, že [zjišťování z vytvořených sestavení](../test/test-explorer-faq.md#assembly-based-discovery
) zapnutý. Kvůli zvýšení výkonu se Visual Studio už načítá informace o zdroji pro indikátory testu, když jsou načteny soubory s kódem. Indikátory testu jsou načteny po sestavení nebo přejděte na test na něj poklikejte na něj v **Průzkumníka testů**.

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
