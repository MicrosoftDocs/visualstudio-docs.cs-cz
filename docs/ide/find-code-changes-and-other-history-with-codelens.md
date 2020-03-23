---
title: Nalezení změn kódu a další historie pomocí CodeLensu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.CodeLens
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9859366f6e4b9a0d1c219adc2080e6415b1e44a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588652"
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Nalezení změn kódu a další historie pomocí CodeLensu

CodeLens vám umožní soustředit se na svou práci, zatímco&ndash;zjistíte, co se stalo s vaším kódem, aniž byste opustili editor. Můžete najít odkazy na část kódu, změny kódu, propojené chyby, pracovní položky, revize kódu a testy částí.

::: moniker range=">=vs-2019"

> [!NOTE]
> CodeLens je k dispozici v edici Visual Studio Community, ale indikátory *ovládacího prvku zdroj* nejsou k dispozici v tomto vydání.

::: moniker-end

::: moniker range="vs-2017"

> [!NOTE]
> CodeLens je k dispozici pouze v edicích Visual Studio Enterprise a Professional. Není k dispozici v edici Visual Studio Community.

::: moniker-end

Podívejte se, kde a jak se jednotlivé části kódu používají ve vašem řešení:

![Indikátory CodeLens v editoru kódu](../ide/media/codelens-overview.png)

Obraťte se na svůj tým o změnách kódu bez opuštění editoru:

![CodeLens - Kontaktujte svůj tým](../ide/media/codelens-contact-info.png)

Chcete-li vybrat indikátory, které chcete vidět, nebo vypnout a zapnout CodeLens, přejděte na **nástroje** > **Možnosti** > **Textový editor** > **Všechny jazyky** > **CodeLens**.

## <a name="find-references-to-your-code"></a>Vyhledání odkazů na váš kód

Odkazy najdete v kódu jazyka C# nebo Visual Basic.

1. Zvolte **indikátor odkazů** nebo stiskněte **klávesu Alt**+**2**.

   ![Odkazy CodeLens](../ide/media/codelens-view-references.png)

   > [!NOTE]
   > Pokud indikátor zobrazuje **0 odkazů**, nemáte žádné odkazy z kódu jazyka C# nebo Visual Basic. V jiných položkách, například *soubory XAML* a *ASPX,* však mohou být odkazy.

2. Chcete-li zobrazit odkazující kód, najeďte myší na odkaz v seznamu.

   ![CodeLens - Odkaz na náhled](../ide/media/codelens-peek-reference.png)

3. Chcete-li otevřít soubor obsahující odkaz, poklepejte na odkaz.

### <a name="code-maps"></a>Mapy kódu

Chcete-li zobrazit vztahy mezi kódem a jeho odkazy, [vytvořte mapu kódu](../modeling/map-dependencies-across-your-solutions.md). V místní nabídce mapy kódu vyberte **Zobrazit všechny odkazy**.

![CodeLens - Reference na mapě kódu](../ide/media/codelensmappedreferences.png)

## <a name="find-changes-in-your-code"></a>Vyhledání změn v kódu

Zkontrolujte historii kódu a zjistěte, co se s vaším kódem stalo. Nebo zkontrolujte změny před jejich sloučením do kódu, abyste lépe pochopili, jak změny v jiných větvích mohou ovlivnit váš kód.

Budete potřebovat:

- Visual Studio Enterprise nebo Professional edition

- Azure DevOps Services, Team Foundation Server 2013 nebo novější nebo Git

- [Skype pro firmy,](/skypeforbusiness/) který vám poskytne kontakt z editoru kódu

Pro kód Jazyka C# nebo Visual Basic, který je uložen s Team Foundation Version Control (TFVC) nebo Git, získáte CodeLens podrobnosti na úrovni třídy a metody (indikátory*na úrovni prvku kódu).* Pokud vaše úložiště Git je hostované v TfGit, získáte také odkazy na pracovní položky TFS.

![Indikátory na úrovni prvků kódu](../ide/media/codelens-element-level-indicators.png)

Pro jiné typy souborů než *.cs* nebo *.vb*získáte podrobnosti CodeLens pro celý soubor na jednom místě v dolní části okna (indikátory*na úrovni souboru).*

![Indikátory CodeLens na úrovni souboru](../ide/media/almcodelensfilelevelindicators.png)

### <a name="code-element-level-indicators"></a>Indikátory na úrovni prvků kódu

Indikátory na úrovni elementu kódu umožňují zobrazit, kdo změnil váš kód a jaké změny provedli. Indikátory úrovně elementu kódu jsou k dispozici pro kód Jazyka C# a Visual Basic.

To je to, co se zobrazí při použití správy verzí Team Foundation (TFVC) v Team Foundation Server nebo Azure DevOps Services:

![CodeLens: Získat historii změn pro váš kód v TFVC](../ide/media/codelens-code-changes.png)

Výchozí časové období je posledních 12 měsíců. Pokud je váš kód uložen v Team Foundation Server, můžete změnit časové období spuštěním [příkazu TFSConfig](/azure/devops/server/command-line/tfsconfig-cmd) pomocí [příkazu CodeIndex](../ide/codeindex-command.md) a příznaku **/indexHistoryPeriod.**

Chcete-li zobrazit podrobnou historii všech změn, včetně těch z doby před více než rokem, zvolte **Zobrazit všechny změny souborů**:

![Zobrazit všechny změny kódu](../ide/media/codelens-show-all-file-changes.png)

Otevře se okno **Historie:**

![Okno Historie pro všechny změny kódu](../ide/media/codelenscodechangeshistory.png)

Když jsou vaše soubory v úložišti Git a zvolíte indikátor změn na úrovni prvku kódu, uvidíte toto:

![CodeLens: Získejte historii změn pro svůj kód v Gitu](../ide/media/codelens-code-changes-git.png)

### <a name="file-level-indicators"></a>Indikátory na úrovni souborů

V indikátorech na úrovni souboru v dolní části okna najdete změny pro celý soubor:

![CodeLens: Získat podrobnosti o souboru kódu](../ide/media/codelens-file-level.png)

> [!NOTE]
> Indikátory na úrovni souborů nejsou k dispozici pro soubory jazyka C# a Visual Basic.

Chcete-li získat další podrobnosti o změně, klikněte na ni pravým tlačítkem myši. V závislosti na tom, zda používáte TFVC nebo Git, existují možnosti porovnat verze souboru, zobrazit podrobnosti a sledovat sadu změn, získat vybranou verzi souboru a odeslat e-mail autorovi této změny. Některé z těchto podrobností se zobrazí v **Průzkumníkovi týmu**.

Můžete také zjistit, kdo změnil váš kód v průběhu času. To vám pomůže najít vzory v týmu změny a posoudit jejich dopad.

![CodeLens: Zobrazení historie změn kódu jako grafu](../ide/media/codelens.png)

### <a name="find-changes-in-your-current-branch"></a>Vyhledání změn v aktuální pobočce

Váš tým může mít více větví, například hlavní větev a podřízenou vývojovou větev, aby se snížilo riziko porušení stabilního kódu.

![CodeLens: Najít, kdy byl váš kód rozvětvený](../ide/media/codelensfirstbranchconceptual.png)

Pomocí klávesy **Alt**+**6**můžete zjistit, kolik lidí změnilo váš kód a kolik změn bylo v hlavní větvi provedeno :

![CodeLens: Zjistěte, kolik změn ve vaší pobočce](../ide/media/codelens-branch-changes.png)

### <a name="find-when-your-code-was-branched"></a>Zjistit, kdy byl váš kód rozvětvený

Chcete-li zjistit, kdy byl váš kód rozvětvený, přejděte na kód v podřízené větvi. Poté vyberte indikátor **změn** nebo stiskněte **klávesu Alt**+**6**:

![CodeLens: Najít, kdy byl váš kód rozvětvený](../ide/media/codelens-first-branch.png)

### <a name="find-incoming-changes-from-other-branches"></a>Hledání příchozích změn z jiných větví

![CodeLens: Najít změny kódu v jiných větvích](../ide/media/codelensbranchchangecheckinconceptual.png)

Můžete zobrazit příchozí změny. Na následujícím snímku obrazovky byla provedena oprava chyby ve větvi "Dev":

![CodeLens: Změna se změna mise do jiné větve](../ide/media/codelens-branch-changes-dev.png)

Změnu můžete zkontrolovat, aniž byste opustili aktuální větev ("Hlavní"):

![CodeLens: Podívejte se na příchozí změny z jiné větve](../ide/media/codelens-branch-changes-main.png)

### <a name="find-when-changes-got-merged"></a>Najít, kdy došlo ke sloučení změn

Můžete vidět, kdy se změny sloučí, takže můžete určit, které změny jsou zahrnuty ve vaší větvi:

![CodeLens - Sloučené změny mezi větvemi](../ide/media/codelensbranchmergedconceptual.png)

Například váš kód v hlavní větvi má nyní opravu chyby z větve "Dev":

![CodeLens - Sloučené změny mezi větvemi](../ide/media/codelens-branch-merged.png)

### <a name="compare-an-incoming-change-with-your-local-version"></a>Porovnání příchozí změny s místní verzí

Porovnejte příchozí změnu s místní verzí stisknutím **klávesy Shift**+**F10**nebo poklepáním na sadu změn.

![CodeLens: Porovnat příchozí změny s místními](../ide/media/codelens-branch-incoming-change-menu.png)

### <a name="branch-icons"></a>Ikony větví

Ikona ve sloupci **Větev** vám řekne, jak větev souvisí s větev, ve které pracujete.

|**Ikona:**|**Změna přišla z:**|
|--------------| - |
|![CodeLens: Změna z aktuální větve ikona](../ide/media/codelensbranchcurrenticon.png)|Aktuální pobočka|
|![CodeLens: Ikona změnit z nadřazené větve](../ide/media/codelensbranchparenticon.png)|Nadřazená větev|
|![CodeLens: Ikona změnit z podřízené větve](../ide/media/codelensbranchchildicon.png)|Podřízená větev|
|![CodeLens: Ikona změnit z větve partnera](../ide/media/codelensbranchpeericon.png)|Větev partnera|
|![CodeLens: Změna z větve dále ikona](../ide/media/codelensbranchfurtherawayicon.png)|Větev vzdálenější než rodič, podřízený nebo druhá klitova|
|![CodeLens: Sloučit z nadřazené ikony](../ide/media/codelensbranchmergefromparenticon.png)|Sloučení z nadřazené větve do podřízené větve|
|![CodeLens: Ikona sloučení z podřízené větve](../ide/media/codelensbranchmergefromchildicon.png)|Sloučení z podřízené větve do nadřazené větve|
|![CodeLens: Ikona sloučení z nesouvisející větve](../ide/media/codelensbranchmergefromunrelatedicon.png)|Sloučení z nesouvisející větve (nepodložené sloučení)|

## <a name="linked-work-items"></a>Propojené pracovní položky

Najít propojené pracovní položky výběrem indikátoru **pracovních položek** nebo stisknutím **alt**+**8**.

![CodeLens - Najít pracovní položky pro konkrétní kód](../ide/media/codelens-work-items.png)

## <a name="linked-code-reviews"></a>Propojené revize kódu

Propojené recenze kódu najdete tak, že vyberete indikátor **recenzí.** Chcete-li používat klávesnici, podržte klávesu **Alt** a stisknutím **šipky vlevo** nebo **šipka doprava** procházejte možnostmi indikátoru.

![CodeLens - Zobrazit žádosti o kontrolu kódu](../ide/media/codelens-code-reviews.png)

## <a name="linked-bugs"></a>Propojené chyby

Najít propojené chyby výběrem indikátoru **chyb** nebo stisknutím **Alt**+**7**.

![CodeLens - Najít chyby spojené s changesets](../ide/media/codelens-bugs-changesets.png)

## <a name="contact-the-owner-of-an-item"></a>Kontaktování vlastníka položky

Najděte autora položky výběrem indikátoru **autoři** nebo stisknutím **klávesy Alt**+**5**.

![Kontaktování vlastníka položky](../ide/media/codelens-contact-item-owner.png)

Otevřete místní nabídku pro položku a zobrazte možnosti kontaktu. Pokud máte nainstalovaný Lync nebo Skype pro firmy, uvidíte tyto možnosti:

![Možnosti kontaktu pro položku](../ide/media/codelens-item-contact-menu.png)

## <a name="associated-unit-tests"></a>Přidružené jednotkové testy

Můžete zjistit testy částí, které existují pro váš kód jazyka C# nebo Visual Basic bez otevření **Průzkumníka testů**.

1. Přejděte na kód aplikace, který má přidružený [kód testování částí](../test/unit-test-your-code.md).

2. Pokud jste tak ještě neučinili, vytvořte aplikaci pro načtení testovacích indikátorů CodeLens. 

3. Zkontrolujte testy kódu stisknutím **klávesy Alt**+**3**.

     ![CodeLens - Zvolit stav testu v editoru kódu](../ide/media/codelens-choose-test-indicator.png)

4. Pokud se zobrazí varovná ikona ![ikona upozornění](../ide/media/codelenstestwarningicon.png), testy ještě nebyly spuštěny, proto je spusťte.

     ![CodeLens - Zobrazit testy částí ještě není spuštěna](../ide/media/codelens-tests-not-yet-run.png)

5. Chcete-li zkontrolovat definici testu, poklepejte na testovací položku v okně indikátoru CodeLens a otevřete soubor kódu v editoru.

     ![CodeLens - Přejít na definici testování částí](../ide/media/codelens-unit-test-definition.png)

6. Chcete-li zkontrolovat výsledky testu, zvolte![indikátor stavu](../ide/media/codelenstestfailedicon.png) ![testu (ikona neúspěšného testu nebo ikonu](../ide/media/codelenstestpassedicon.png)testu ) nebo stiskněte **klávesu Alt**+**1**.

     ![CodeLens - viz výsledek testu částí](../ide/media/codelens-unit-test-result.png)

7. Chcete-li zjistit, kolik lidí tento test změnilo, kdo tento test změnil nebo kolik změn bylo v tomto testu provedeno, [vyhledejte historii kódu](#find-changes-in-your-code) a propojené položky.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Chcete-li pomocí klávesnice vybrat indikátory, stiskněte a podržte klávesu **Alt,** chcete-li zobrazit související číselné klávesy, stiskněte číslo odpovídající indikátoru, který chcete vybrat.

![Přístupová čísla klávesnice](../ide/media/codelens-alt-keys.png)

> [!NOTE]
> Chcete-li vybrat indikátor **recenzí,** podržte **klávesu Alt** a pomocí kláves se šipkami vlevo a vpravo navigujte.

## <a name="q--a"></a>Otázky a odpovědi

### <a name="q-how-do-i-turn-codelens-off-or-on-or-choose-which-indicators-to-see"></a>Otázka: Jak vypnu CodeLens nebo zvolím, které indikátory se mají zobrazit?

**A:**  Indikátory můžete vypnout nebo zapnout, s výjimkou indikátoru odkazů. Přejít na**možnosti** >  **nástroje** > **textový editor** > **všechny jazyky** > **CodeLens**.

Když jsou indikátory zapnuté, můžete také otevřít volby CodeLens z indikátorů.

![CodeLens - Vypnutí nebo zapnutí indikátorů](../ide/media/codelensturnoffonindicatorsfromcode.png)

Zapněte a vypněte indikátory úrovně souborů CodeLens pomocí ikon prýmků v dolní části okna editoru.

![Zapnutí a vypnutí indikátorů na úrovni souborů](../ide/media/codelensfilelevelonandoff.png)

### <a name="q-where-is-codelens"></a>Otázka: Kde je CodeLens?

**A:** CodeLens se zobrazí v kódu Jazyka C# a Visual Basic na úrovni metody, třídy, indexeru a vlastností. CodeLens se zobrazí na úrovni souborů pro všechny ostatní typy souborů.

- Ujistěte se, že codelens je zapnutý. Přejít na**možnosti** >  **nástroje** > **textový editor** > **všechny jazyky** > **CodeLens**.

- Pokud je váš kód uložen v TFS, ujistěte se, že indexování kódu je zapnuto pomocí [příkazu CodeIndex](../ide/codeindex-command.md) s [příkazem TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

- Indikátory související s DevOps se zobrazí pouze v případě, že jsou pracovní položky propojeny s kódem a pokud máte oprávnění k otevření propojených pracovních položek. Potvrďte, že máte [oprávnění členů týmu](/azure/devops/organizations/security/view-permissions?view=vsts).

- Indikátory testování částí se nezobrazí, pokud kód aplikace nemá testy částí. Indikátory stavu testu se automaticky zobrazí v projektech testů. Pokud víte, že kód aplikace má testy částí, ale indikátory testu se nezobrazí, zkuste sestavení řešení (**Ctrl**+**Shift**+**B**).

::: moniker range=">=vs-2019"

> [!TIP]
> CodeLens je k dispozici v edici Visual Studio Community, ale indikátory *ovládacího prvku zdroj* nejsou k dispozici v tomto vydání.

::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> CodeLens není k dispozici v edici Visual Studio Community.

::: moniker-end

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>Otázka: Proč nevidím podrobnosti pracovní položky pro potvrzení?

**A:** K tomu může dojít, protože CodeLens nemůže najít pracovní položky v Azure Boards nebo TFS. Zkontrolujte, zda jste připojeni k projektu, který má tyto pracovní položky a že máte oprávnění k zobrazení těchto pracovních položek. Podrobnosti pracovní položky se také nemusí zobrazit, pokud popis potvrzení obsahuje nesprávné informace o ID pracovní položky v Azure Boards nebo TFS.

### <a name="q-why-dont-i-see-the-skype-indicators"></a>Otázka: Proč nevidím indikátory Skypu?

**A:** Indikátory Skypu se nezobrazují, pokud nejste přihlášení ke Skypu pro firmy, nemáte ho nainstalované nebo nemáte podporovanou konfiguraci. E-mail však stále můžete posílat:

![CodeLens - Vlastník sady změn kontaktů poštou](../ide/media/codelenscodesendmailchangesetnolync1.png)

**Které konfigurace Skypu a Lyncu jsou podporované?**

- Skype pro firmy (32bitový nebo 64bitový)

- Lync 2010 nebo novější sám (32bitový nebo 64bitový), ale ne Lync Basic 2013 s Windows 8.1

CodeLens nepodporuje instalaci různých verzí Lyncu nebo Skypu. Nemusí být lokalizovány pro všechny lokalizované verze sady Visual Studio.

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>Otázka: Jak změním písmo a barvu pro CodeLens?

**A:** Přejděte na**možnosti** >  **nástrojů** > **Písma** > **a barvy prostředí**.

![CodeLens - Změna nastavení písma a barev](../ide/media/codelensoptionsfontscolorssettings.png)

Použití klávesnice:

1. Stisknutím **klávesy Alt**+**T**+**O** otevřete dialogové okno **Možnosti.**

2. Stisknutím **klávesšipky nahoru** nebo **šipka dolů** přejděte na uzel **Prostředí** a stisknutím **klávesy Left Arrow** uzel rozbalte.

3. Stisknutím **klávesy Šipka dolů** přejděte na **Písma a barvy**.

4. Stisknutím **klávesy Tab** přejděte do seznamu **Zobrazit nastavení a** stisknutím **klávesy Šipka dolů** vyberte **CodeLens**.

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>Otázka: Lze přesunout pohotové zobrazení funkce CodeLens?

**A:** Ano, ![zvolte](../ide/media/codelensdockwindow.png) Ikona Ukotvení, chcete-li Ukotvit CodeLens jako okno.

![Tlačítko Dock v okně indikátoru CodeLens](../ide/media/codelensselectdockwindow.png)

![Okno Ukotvené odkazy CodeLens](../ide/media/codelensreferencesdockedwindow.png)

### <a name="q-how-do-i-refresh-the-indicators"></a>Otázka: Jak mohu aktualizovat indikátory?

**A:** To závisí na indikátoru:

- **Odkazy**: Tento indikátor se aktualizuje automaticky při změně kódu. Pokud je indikátor **Reference** ukotven jako samostatné okno, aktualizujte indikátor výběrem **možnosti Aktualizovat**:

   ![Tlačítko Aktualizovat v odkazech CodeLens](../ide/media/codelensviewreferencesdocked.png)

- **Tým**: Aktualizujte tyto indikátory výběrem **refresh CodeLens Team Indicators** z nabídky po kliknutí pravým tlačítkem myši:

   ![Aktualizovat položku nabídky Indikátory týmu CodeLens](../ide/media/codelensrefreshindicatorsfromcode.png)

- **Test**: [Najděte testy částí pro váš kód,](#associated-unit-tests) který aktualizuje indikátor **test.**

### <a name="q-whats-local-version"></a>Otázka: Co je "místní verze"?

**A:** Šipka **Místní verze** ukazuje na nejnovější sadu změn v místní verzi souboru. Pokud má server novější sady změn, zobrazí se nad nebo pod šipkou **Místní verze** v závislosti na pořadí použitém k řazení sad změn.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>Otázka: Mohu spravovat, jak CodeLens zpracovává kód pro zobrazení historie a propojených položek?

**Odpověď:** Ano. Pokud je váš kód v TFS, použijte [příkaz CodeIndex](../ide/codeindex-command.md) s [příkazem TFS Config](/azure/devops/server/command-line/tfsconfig-cmd).

### <a name="q-my-codelens-test-indicators-no-longer-appear-in-my-file-when-i-first-open-my-solution-how-can-i-load-them"></a>Otázka: Indikátory testu CodeLens se již nezobrazují v souboru při prvním otevření řešení. Jak je mohu načíst?

**A:** Sestavte projekt a získejte indikátory testu CodeLens, které se načtou do souboru. Chcete-li zvýšit výkon, Visual Studio již načte zdrojové informace pro testovací indikátory při načítání souborů kódu. Indikátory testu jsou načteny po sestavení nebo při přechodu na test poklepáním na něj v **Průzkumníku testů**.

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
