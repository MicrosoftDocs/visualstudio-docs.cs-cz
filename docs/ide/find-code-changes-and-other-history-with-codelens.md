---
title: Nalezení změn kódu a další historie pomocí CodeLensu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10a325c75179ed6917e1772bb9e17f2237e4ee17
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74538959"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Nalezení změn kódu a další historie pomocí CodeLensu

CodeLens vám umožňuje soustředit se na práci, zatímco zjistíte, co se stalo s vaším kódem&ndash;bez nutnosti opustit Editor. Můžete najít odkazy na část kódu, změny kódu, propojené chyby, pracovní položky, revize kódu a testování částí.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens je k dispozici v edici Visual Studio Community Edition, ale indikátory *správy zdrojů* nejsou v této edici k dispozici.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens je k dispozici pouze v edicích Visual Studio Enterprise a Professional. Není k dispozici v edici Visual Studio Community Edition.

::: moniker-end

Podívejte se, kde a jak se jednotlivé části kódu používají ve vašem řešení:

![Indikátory CodeLens v editoru kódu](../ide/media/codelens-overview.png)

Kontaktujte svůj tým o změnách kódu bez nutnosti opustit Editor:

![CodeLens – kontaktujte tým](../ide/media/codelens-contact-info.png)

Chcete-li vybrat indikátory, které chcete zobrazit, nebo CodeLens vypnout a zapnout, přejděte do části **nástroje** > **Možnosti** > **textový editor** > **všechny jazyky** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Vyhledat odkazy na váš kód

Můžete najít odkazy v C# kódu nebo Visual Basic kódu.

1. Zvolte indikátor **odkazů** nebo stiskněte klávesu **ALT**+**2**.

   ![Odkazy na CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Pokud indikátor zobrazuje **0 odkazů**, nebudete mít žádné odkazy C# z nebo Visual Basic kódu. Mohou však existovat odkazy na jiné položky, například soubory *. XAML* a *. aspx* .

2. Chcete-li zobrazit referenční kód, přesměrujte ukazatel myši na odkaz v seznamu.

   ![CodeLens – náhled – referenční informace](../ide/media/codelens-peek-reference.png)

3. Chcete-li otevřít soubor, který obsahuje odkaz, dvakrát klikněte na odkaz.

### <a name="code-maps"></a>Mapy kódu

Chcete-li zobrazit vztahy mezi kódem a jeho odkazy, [vytvořte mapu kódu](../modeling/map-dependencies-across-your-solutions.md). V místní nabídce mapa kódu vyberte možnost **Zobrazit všechny odkazy**.

![CodeLens – odkazy na mapu kódu](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Hledání změn v kódu

Podívejte se na historii kódu a zjistěte, co se stalo s vaším kódem. Nebo můžete zkontrolovat změny před jejich sloučením do kódu, abyste lépe pochopili, jakým způsobem mohou změny v jiných větvích ovlivnit váš kód.

Potřebuješ:

- Visual Studio Enterprise nebo Professional Edition

- Azure DevOps Services, Team Foundation Server 2013 nebo novější nebo Git

- [Skype pro firmy](/skypeforbusiness/) , aby se kontaktoval váš tým z editoru kódu

Pro C# nebo Visual Basic kód uložený pomocí Správa verzí Team Foundation (TFVC) nebo Git získáte podrobnosti CodeLens na úrovni třídy a metody (indikátory*na úrovni elementu kódu* ). Pokud je vaše úložiště Git hostované v TfGit, získáte také odkazy na pracovní položky sady TFS.

![Indikátory na úrovni elementu kódu](../ide/media/codelens-element-level-indicators.png)

Pro jiné typy souborů než *. cs* nebo *. vb*získáte CodeLens podrobnosti o celém souboru na jednom místě v dolní části okna (indikátory na*úrovni souborů* ).

![Indikátory CodeLens na úrovni souboru](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indikátory na úrovni elementu kódu

Indikátory na úrovni elementu kódu umožňují zobrazit, kdo změnil váš kód a jaké změny byly provedeny. Indikátory na úrovni elementu kódu jsou k C# dispozici pro a Visual Basic kód.

To je to, co se vám zobrazuje při použití Správa verzí Team Foundation (TFVC) v Team Foundation Server nebo Azure DevOps Services:

![CodeLens: Získá historii změn kódu v TFVC.](../ide/media/codelens-code-changes.png)

Výchozí časové období je posledních 12 měsíců. Pokud je váš kód uložen v Team Foundation Server, můžete změnit časové období spuštěním [příkazu TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) pomocí [příkazu CodeIndex –](../ide/codeindex-command.md) a příznaku **/indexHistoryPeriod** .

Chcete-li zobrazit podrobné informace o všech změnách, včetně těch, které jsou před více než rokem, vyberte možnost **Zobrazit všechny změny souborů**:

![Zobrazit všechny změny kódu](../ide/media/codelens-show-all-file-changes.png)

Otevře se okno **Historie** :

![Okno historie pro všechny změny kódu](../ide/media/codelenscodechangeshistory.png)

Pokud jsou soubory v úložišti Git a zvolíte indikátor změny úrovně prvku kódu, zobrazí se toto:

![CodeLens: Získá historii změn kódu v Gitu.](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indikátory na úrovni souboru

V indikátorech na úrovni souborů v dolní části okna Najděte změny pro celý soubor:

![CodeLens: Získání podrobností souboru s kódem](../ide/media/codelens-file-level.png)

> [!NOTE]
> Indikátory na úrovni souboru nejsou k dispozici pro C# a Visual Basic soubory.

Chcete-li získat další informace o změně, klikněte pravým tlačítkem myši na danou položku. V závislosti na tom, zda používáte TFVC nebo Git, existují možnosti pro porovnání verzí souboru, zobrazení podrobností a sledování sady změn, získání vybrané verze souboru a odeslání e-mailu autorovi této změny. Některé z těchto podrobností se zobrazí v **Team Explorer**.

Můžete také zjistit, kdo změnil kód v průběhu času. To může pomoct najít vzory ve změnách vašeho týmu a posoudit jejich dopad.

![CodeLens: Zobrazení historie změn kódu jako grafu](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Vyhledat změny v aktuální větvi

Váš tým může mít více větví, například hlavní větev a podřízenou vývojovou větev pro snížení rizika poškození stabilního kódu.

![CodeLens: najít, kdy byl kód v větve](../ide/media/codelensfirstbranchconceptual.png)

Stisknutím klávesy **Alt**+**6**zjistíte, kolik lidí změnilo váš kód a kolik změn bylo provedeno v hlavní větvi.

![CodeLens: najít počet změn ve větvi](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Najít, kdy byl kód v větvení

Chcete-li zjistit, kdy byl kód vytvořen, přejděte do kódu v podřízené větvi. Pak vyberte indikátor **změn** nebo stiskněte klávesu **ALT**+**6**:

![CodeLens: najít, kdy byl kód v větve](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Najít příchozí změny z jiných větví

![CodeLens: najít změny kódu v dalších větvích](../ide/media/codelensbranchchangecheckinconceptual.png)

Můžete zobrazit příchozí změny. Na následujícím snímku obrazovky byla opravena chyba ve větvi "vývoj":

![CodeLens: Změna kontrolovaného na jinou větev](../ide/media/codelens-branch-changes-dev.png)

Změnu můžete zkontrolovat bez nutnosti opustit aktuální větev ("Main"):

![CodeLens: viz příchozí změna z jiné větve](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Najít, kdy byly změny sloučeny

Můžete vidět, kdy byly změny sloučeny, abyste mohli určit, které změny budou zahrnuty do vaší větve:

![CodeLens – sloučení změn mezi větvemi](../ide/media/codelensbranchmergedconceptual.png)

Například váš kód v hlavní větvi teď obsahuje opravu chyby z větve pro vývoj:

![CodeLens – sloučení změn mezi větvemi](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porovnání příchozí změny s místní verzí

Porovnejte příchozí změnu s místní verzí stisknutím klávesy **Shift**+**F10**nebo Poklikáním na sadu změn.

![CodeLens: porovná příchozí změnu s místními](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony větví

Ikona ve sloupci **větev** obsahuje informace o tom, jak se větev vztahuje ke větvi, se kterou pracujete.

|**Ikona**|**Změna byla přijata z:**|
|--------------| - |
|![CodeLens: ikona změnit z aktuální větve](../ide/media/codelensbranchcurrenticon.png)|Aktuální větev|
|![CodeLens: ikona změnit z nadřazené větve](../ide/media/codelensbranchparenticon.png)|Nadřazená větev|
|![CodeLens: ikona změnit z podřízené větve](../ide/media/codelensbranchchildicon.png)|Podřízená větev|
|![CodeLens: ikona změnit z partnerské větve](../ide/media/codelensbranchpeericon.png)|Rovnocenná větev|
|![CodeLens: ikona změny z větve dál](../ide/media/codelensbranchfurtherawayicon.png)|Větev, která je dále volná, podřízená nebo rovnocenná|
|![CodeLens: ikona sloučení z nadřazené položky](../ide/media/codelensbranchmergefromparenticon.png)|Sloučení z nadřazené větve do podřízené větve|
|![CodeLens: ikona sloučení z podřízené větve](../ide/media/codelensbranchmergefromchildicon.png)|Sloučení z podřízené větve do nadřazené větve|
|![CodeLens: ikona sloučení z nesouvisející větve](../ide/media/codelensbranchmergefromunrelatedicon.png)|Sloučení z nesouvisející větve (sloučení neopodstatněné)|

## <a name="linked-work-items"></a>Propojené pracovní položky

Vyhledejte propojené pracovní položky výběrem indikátoru **pracovních položek** nebo stisknutím **kombinace kláves ALT**+**8**.

![CodeLens – vyhledání pracovních položek pro konkrétní kód](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Revize propojených kódů

Pomocí **indikátoru** kontroly vyhledejte propojené revize kódu. Chcete-li použít klávesnici, podržte stisknutou klávesu **ALT** a stisknutím klávesy **šipka vlevo** nebo **vpravo** přejděte na možnosti indikátoru.

![CodeLens-zobrazit žádosti o revizi kódu](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Propojené chyby

Vyhledejte propojené chyby tak, že vyberete indikátor **chyb** nebo stisknete **ALT**+**7**.

![CodeLens – vyhledání chyb propojených se sadami změn](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Obraťte se na vlastníka položky.

Vyhledejte autora položky výběrem indikátoru **autorů** nebo stisknutím klávesy **ALT**+**5**.

![Obraťte se na vlastníka položky.](../ide/media/codelens-contact-item-owner.png)

Otevřete místní nabídku pro položku, abyste viděli možnosti kontaktů. Pokud máte nainstalovaný Lync nebo Skype pro firmy, zobrazí se tyto možnosti:

![Možnosti kontaktu pro položku](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Přidružené testy jednotek

Můžete zjistit testy jednotek, které existují pro váš C# kód nebo Visual Basic bez nutnosti otevřít **Průzkumníka testů**.

1. Přejít na kód aplikace, který má přidružený [kód pro testování částí](../test/unit-test-your-code.md).

2. Pokud jste to ještě neučinili, sestavte aplikaci tak, aby se načetly indikátory testu CodeLens. 

3. Zkontrolujte testy kódu stisknutím klávesy **Alt**+**3**.

     ![CodeLens – zvolit stav testu v editoru kódu](../ide/media/codelens-choose-test-indicator.png)

4. Pokud se zobrazí výstražná ikona ![Ikona upozornění](../ide/media/codelenstestwarningicon.png), testy se ještě nespouštěly, proto je spusťte.

     ![CodeLens – zobrazení testů jednotek ještě není spuštěno](../ide/media/codelens-tests-not-yet-run.png)

5. Chcete-li zkontrolovat definici testu, dvakrát klikněte na položku Test v okně indikátor CodeLens a otevřete soubor kódu v editoru.

     ![CodeLens – přejít k definici testování částí](../ide/media/codelens-unit-test-definition.png)

6. Chcete-li zkontrolovat výsledky testu, zvolte indikátor stavu testu (![ikonu neúspěšných testů](../ide/media/codelenstestfailedicon.png) nebo ![test prošel](../ide/media/codelenstestpassedicon.png)) nebo stiskněte klávesu **Alt**+**1**.

     ![CodeLens – viz výsledek testu jednotek](../ide/media/codelens-unit-test-result.png)

7. Chcete-li zjistit, kolik lidí změnilo tento test, kdo tento test změnil nebo kolik změn bylo provedeno v tomto testu, [Najděte historii kódu](#find-changes-in-your-code) a propojené položky.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Chcete-li použít klávesnici k výběru indikátorů, stiskněte a podržte klávesu **ALT** k zobrazení souvisejících klávesových zkratek a potom stiskněte číslo, které odpovídá indikátoru, který chcete vybrat.

![Přístupová čísla klávesnice](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Chcete **-li vybrat indikátor kontrol** , stiskněte klávesu **ALT** a použijte klávesu šipka vlevo a vpravo k navigaci.

## <a name="q--a"></a>Dotazy a odpovědi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Otázka: Návody CodeLens vypnout nebo zapnout nebo vyberte indikátory, které chcete zobrazit?

**A:**  Můžete zapnout nebo vypnout indikátory, s výjimkou indikátoru odkazů. V **nabídce nástroje** > **Možnosti** > **textový editor** > **všechny jazyky** > **CodeLens**.

Když jsou indikátory zapnuté, můžete také otevřít možnosti CodeLens z indikátorů.

![CodeLens – zapnout nebo vypnout indikátory](../ide/media/codelensturnoffonindicatorsfromcode.png)

Zapne nebo vypne indikátory CodeLens na úrovni souboru pomocí ikon dvojitých šipek v dolní části okna editoru.

![Zapnout a vypnout indikátory na úrovni souboru](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>Otázka: kde je CodeLens?

**A:** CodeLens se zobrazí C# v a Visual Basic kódu na úrovni metody, třídy, indexeru a vlastnosti. CodeLens se zobrazí na úrovni souboru pro všechny ostatní typy souborů.

- Ujistěte se, že je zapnutá funkce CodeLens. V **nabídce nástroje** > **Možnosti** > **textový editor** > **všechny jazyky** > **CodeLens**.

- Pokud je váš kód uložen na serveru TFS, ujistěte se, že je zapnuto indexování kódu pomocí [příkazu CodeIndex –](../ide/codeindex-command.md) s [příkazem konfigurace serveru TFS](/azure/devops/server/command-line/tfsconfig-cmd).

- Indikátory související s DevOps se zobrazí pouze v případě, že jsou pracovní položky propojeny s kódem a máte oprávnění k otevření propojených pracovních položek. Potvrďte, že máte [oprávnění člena týmu](/azure/devops/organizations/security/view-permissions?view=vsts).

- Indikátory testu jednotek se nezobrazí, pokud kód aplikace nemá testy jednotek. Indikátory stavu testu se automaticky zobrazí v projektech testů. Pokud víte, že váš kód aplikace má testy jednotek, ale nezobrazují se indikátory testu, zkuste sestavit řešení (**Ctrl**+**SHIFT**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens je k dispozici v edici Visual Studio Community Edition, ale indikátory *správy zdrojů* nejsou v této edici k dispozici.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens není v edici Visual Studio Community Edition k dispozici.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Otázka: Proč se mi nezobrazuje podrobnosti o pracovní položce pro potvrzení?

**A:** K tomu může dojít, protože CodeLens nemůže najít pracovní položky v Azure Boards nebo TFS. Zkontrolujte, zda jste připojeni k projektu, který obsahuje tyto pracovní položky a zda máte oprávnění k zobrazení pracovních položek. Podrobnosti o pracovní položce se také nemusí zobrazit, pokud popis potvrzení obsahuje nesprávné informace o ID pracovní položky v Azure Boards nebo TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>Otázka: Proč nevidím indikátory Skype?

**A:** Pokud nejste přihlášení ke Skypu pro firmy, nemusíte se indikátory Skype nainstalovat, nebo nemáte podporovanou konfiguraci. Pořád ale můžete posílat e-maily:

![CodeLens – vlastník sady změn kontaktuje e-mailem](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Které konfigurace Skype a Lyncu se podporují?**

- Skype pro firmy (32-bit nebo 64)

- Lync 2010 nebo novější (32-bit nebo 64-bit), ale ne Lync Basic 2013 s Windows 8.1

CodeLens nepodporuje nainstalovanou jinou verzi Lyncu nebo Skype. Nemusí být lokalizovány pro všechny lokalizované verze sady Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Otázka: Návody změnit písmo a barvu pro CodeLens?

**A:** V **nabídce nástroje** > **možnosti** > **prostředí** > **písma a barvy**.

![CodeLens – Změna nastavení písma a barvy](../ide/media/codelensoptionsfontscolorssettings.png)

Použití klávesnice:

1. Stisknutím **kombinace kláves Alt**+**t**+**O** otevřete dialogové okno **Možnosti** .

2. Stisknutím klávesy **šipka nahoru** nebo **šipka dolů** přejděte k uzlu **prostředí** a stisknutím klávesy **šipka vlevo** rozbalte uzel.

3. Stisknutím klávesy **šipka dolů** přejděte na **písma a barvy**.

4. Stisknutím klávesy **TAB** přejděte do seznamu **Zobrazit nastavení pro** a potom stisknutím klávesy **šipka dolů** vyberte možnost **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Otázka: Lze přesunout pohotové zobrazení funkce CodeLens?

**A:** Ano, vyberte ikonu ![Dock](../ide/media/codelensdockwindow.png) a ukotvěte CodeLens jako okno.

![Ukotvit tlačítko v okně indikátoru CodeLens](../ide/media/codelensselectdockwindow.png)

![Okno odkazů na ukotvené CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Otázka: Jak mohu aktualizovat indikátory?

**A:** To závisí na indikátoru:

- **Odkazy**: Tento indikátor se automaticky aktualizuje při změně kódu. Pokud je indikátor **odkazů** ukotven jako samostatné okno, aktualizujte indikátor výběrem možnosti **aktualizovat**:

   ![Tlačítko Aktualizovat v odkazech na CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Tým**: aktualizujte tyto indikátory tak, že v místní nabídce kliknete na tlačítko **aktualizovat CodeLens týmu** :

   ![Položka nabídky pro aktualizaci ukazatelů týmu CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [vyhledejte testy jednotek kódu](#associated-unit-tests) pro aktualizaci indikátoru **testu** .

### <a name="q-whats-local-version"></a>Otázka: co je místní verze?

**A:** Šipka **místní verze** ukazuje na nejnovější sadu změn v místní verzi souboru. Pokud má server novější sady změn, zobrazí se nad nebo pod šipkou **místní verze** v závislosti na pořadí použitém k řazení sad změn.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Otázka: mohu spravovat způsob, jakým CodeLens zpracovává kód pro zobrazení historie a propojených položek?

**A:** Ano. Pokud je váš kód v TFS, použijte [příkaz CodeIndex –](../ide/codeindex-command.md) pomocí [příkazu TFS config](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>Otázka: moje indikátory testu CodeLens se při prvním otevření mého řešení již neobjevují v souboru my. Jak je můžu načíst?

**A:** Znovu sestavte projekt, abyste získali indikátory CodeLens testů, které se mají načíst do souboru. Pro zlepšení výkonu Visual Studio již nenačítá zdrojové informace pro testovací indikátory, když jsou načteny soubory kódu. Testovací indikátory jsou načteny po sestavení nebo při přechodu na test dvojitým kliknutím na něj v **Průzkumníku testů**.

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
