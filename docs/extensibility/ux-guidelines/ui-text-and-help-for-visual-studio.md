---
title: Text uživatelského rozhraní a nápovědu pro Visual Studio | Microsoft Docs
description: Přečtěte si o textu uživatelského rozhraní a terminologii používané v informacích o nápovědě pro Visual Studio.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b128c5e95c70457d92843e620b4aa072c409ba
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899430"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Text uživatelského rozhraní a nápověda pro Visual Studio
## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a> Text uživatelského rozhraní a terminologie
 Srozumitelnější text je zásadní pro efektivní uživatelské rozhraní. Uživatelé softwaru obvykle čtou štítky, konkrétně ty, které jsou relevantní pro dokončení úlohy. Statický text je čten s menší frekvencí. Naplánujte uživatelům, aby si spouštěli své pracovní relace s rychlou kontrolou celého okna a za tímto přibližným pořadím přečetli uživatelské rozhraní.

1. Interaktivní ovládací prvky v centru

2. Tlačítka potvrzení

3. Interaktivní ovládací prvky nalezené jinde

4. Hlavní pokyny

5. Doplňková vysvětlení

6. Název okna

7. Další statický text v hlavním těle

### <a name="usage-patterns-for-ui-text"></a>Vzorce používání pro text uživatelského rozhraní

#### <a name="title-bar-text"></a>Text záhlaví
 Text záhlaví se musí shodovat s příkazem, který vytvořil uživatelské rozhraní.

#### <a name="instructional-text-helper-text"></a>Instruktážní text (pomocný text)
 V některých dialogových oknech je užitečné poskytnout nejvýraznější hlavní pokyny, které vám pomůžou vysvětlit, co dělat v okně nebo na stránce. V takovém případě se někdy označuje jako "text nápovědy".

##### <a name="writing-style-rules-for-helper-text"></a>Psaní pravidel stylu pro text nápovědy

- Nevysvětlí zjevné. Pokud není nezbytně nutné, nezahrnujte instruktážní text.

- Instruktážní text je vždycky umístěný v horní části dialogového okna a měl by se vztahovat na úkol, který se má provést.

- Přesně Vysvětlete uživatele, co potřebují. Vyhněte se nadměrné komunikaci a redundanci.

- Zkontrolujte jednotlivá okna a Eliminujte duplicitní slova a příkazy.

- Stručně ponechte text s pokyny. Pokud jsou pro určité uživatele nebo scénáře potřeba další informace, zadejte odkaz na podrobné koncepční téma online.

- Napište svůj text tak, aby každé slovo mělo váhu a bylo nezbytné.

- Řiďte se stávajícími pokyny Microsoftu pro [text uživatelského rozhraní](/windows/desktop/uxguide/text-ui) a [styl a tón](/windows/desktop/uxguide/text-style-tone).

#### <a name="supplemental-instructions"></a>Doplňkové pokyny
 Doplňkové pokyny poskytují další informace, které pomáhají uživatelům pochopit ovládací prvky nebo seskupení ovládacích prvků. Může to také zahrnovat text nápovědy, který je nezbytný k pochopení toho, jaký formát vstupní ovládací prvek očekává. Používejte doplňkové pokyny zřídka. Rezervujte je pro případy, kdy je pravděpodobnější, že uživatel nebude plně rozumět vlivům volby, které provádějí.

 ![Snímek obrazovky s tlačítkem možnosti aplikace Internet Explorer s doplňujícím textem, který popisuje dopad změny nastavení možností.](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 – b_SupplementalText1")

 **Doplňkový text v aplikaci Visual Studio**

 ![Snímek obrazovky dialogového okna zvolit správu zdrojového kódu v aplikaci Visual Studio zobrazující doplňkový text, který popisuje jednotlivé možnosti systému správy zdrojů.](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 – c_SupplementalText2")

 **Doplňkový text v aplikaci Visual Studio**

#### <a name="infotips"></a>Informační popisy
 Často je možné, že text s pokyny může být příliš dlouhý na pozici v uživatelském rozhraní nebo může být užitečný jenom pro nové uživatele, takže zkušení uživatelé mají hodně na dobrém místě. V takovém případě by se pokyny a informační text měly umístit jako popis v popisu.

 Informační popisy by se měly umístit poblíž ovládacích prvků, ke kterým se vztahují, a měly by používat konkrétní ikonu informačního popisu, která se ještě nevšimla.

 ![Informační Tip v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 – d_InfoTip")

 **Příklad informačního popisu v aplikaci Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Psaní pravidel stylu pro informační popisy

- Zápis informačního popisu jako úplných vět. Vyžadují konkrétní slovesa, Velká a koncová interpunkční znaménka.

- K doplnění vaší hlavní instrukce nebo informací použijte informační popis. Pokud k restavování hlavní myšlenky používáte jenom různá slova, nebudete potřebovat informační Tip.

- Ponechte krátké a sladké informační popisy. Používejte malá slova a obyčejný, každodenní jazyk, který podporuje a podporuje uživatele.

- Řiďte se stávajícími pokyny Microsoftu pro [text uživatelského rozhraní](/windows/desktop/uxguide/text-ui) a [styl a tón](/windows/desktop/uxguide/text-style-tone).

#### <a name="control-labels"></a>Popisky ovládacích prvků
 Popisky ovládacích prvků by měly být krátké, stručné a postupovat podle [pokynů pro stolní počítače s Windows](/windows/desktop/uxguide/controls).

 Další informace o formátu a umístění popisků ovládacích prvků v uživatelském rozhraní naleznete v tématu [layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Odkazy na Help
 Odkazy na help lze umístit do popisného textu nebo do těla uživatelského rozhraní. Můžou se jednat o odkazy, které pomohou nebo spouštějí interní dialogová okna.

##### <a name="visual-style-rules-for-help-links"></a>Pravidla vizuálního stylu pro odkazy na nápovědu

- Použijte správné barvy prostředí pro hypertextové odkazy. Hypertextový odkaz s správným stylem nebude při kliknutí krátce blikat červený. Pokud se to zobrazí, je indikace, že se nepoužívají barvy prostředí.

- Podtržení by mělo být použito pouze při najetí myší nebo v případě, že je odkaz vložen do odstavce.

- Podrobnější informace o vizuálních a stylech interakce pro hypervazby najdete v tématu tlačítka a hypertextové odkazy.

##### <a name="writing-style-rules-for-help-links"></a>Psaní pravidel stylu pro odkazy na nápovědu

- Když spouštíte dialogy, udržujte standardy pro tři tečky: žádné tři tečky pro navigaci, tři tečky, pokud úkol vyžaduje další uživatelské rozhraní.

     ![Odkaz na Help v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 – e_HelpLink")

     **Tři tečky (...) v odkazu na help označuje, že úkol bude vyžadovat další uživatelské rozhraní.**

- Odkazy by neměly začínat "učit", protože to není záměr uživatele. Uživatel chce odpovědět na konkrétní otázku a získat obecné vzdělávání.

- Fráze nápovědy odkazují, aby se dotazoval na otázku, že téma bude odpovídat.

     Nesprávné: Přečtěte si další informace o cenách Windows Azure Mobile Services.

     Správné: "jaké cenové možnosti jsou k dispozici pro Windows Azure Mobile Services?"

- Nikdy *nepoužívejte text odkazu na odkaz* .

- Nikdy nepropojit pouze slovo "zde". To je problematické pro některé čtečky obrazovky, které budou hlas pouze hypertextovým slovem s hypertextovými odkazy.

     Nesprávné: **tady** najdete informace v systému Windows Azure Mobile Services

     Správné: "jaké cenové možnosti jsou k dispozici pro Windows Azure Mobile Services?"

- Další informace o správném stylu psaní pro odkazy na nápovědu naleznete v doprovodné příručce k [ploše systému Windows](/windows/desktop/uxguide/winenv-help).

#### <a name="hint-text"></a>Text nápovědy
 Text nápovědy se zobrazí jako vodoznak v rámci ovládacího prvku nebo pod ovládacím prvkem. Správné formátování se použije pomocí odpovídajícího tokenu VSColors `Environment.GrayText` .

 Může se objevit v několika formách.

- Místo popisku ovládacího prvku:

     ![Snímek obrazovky ovládacího prvku rozevíracího seznamu s textem nápovědy místo popisku ovládacího prvku, který čte "Search Průzkumník řešení (CTRL +;)".](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 – f_HintText1")

- Pomocí příkazu, který poskytuje pokyny:

     ![Snímek obrazovky s textovým polem s nápovědou v ovládacím prvku, který čte "zadejte své jméno".](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 – g_HintText2")

- S textem, který označuje požadovanou položku:

     ![Snímek obrazovky s textovým polem s nápovědou v ovládacím prvku, který čte " \< povinné \> ".](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 – h_HintText3")

#### <a name="watermark-text"></a>Text vodoznaku
 Na prázdné návrhové ploše by měl text indikovat, co dělat, a také poskytnout odkazy na otevírání dalších souvisejících oken, pokud je to vhodné:

 ![Text vodoznaku v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 – i_WatermarkText")

 **Příklad textu vodoznaku v aplikaci Visual Studio**

### <a name="common-terminology"></a>Společná terminologie

|Pojem|Vysvětlení|Komentář|
|----------|-----------------|-------------|
|Přihlášení nebo odhlášení|Příkazy používané jako synonymaem na webu pro reprezentaci ověřování do webové vlastnosti. V rámci klientů používáme tuto možnost jednou jako pojem nejvyšší úrovně pro přihlašování a odhlašování pomocí uživatelského připojení IDE, které představuje identitu nejvyšší úrovně, která poskytuje funkce vyšší úrovně, jako je například roaming a licencování, které nejsou k dispozici u všech ostatních připojení.|Jenom uživatel IDE je jedinou funkcí, která by měla představovat operaci přihlášení nebo odhlášení, protože představuje uživatele integrovaného vývojového prostředí (IDE) nejvyšší úrovně.|
|Připojit nebo odpojit|Použijte v místech, kde funkce zachovává jedno připojení k online službě.|Průzkumník serveru, kde můžete mít v jednom okamžiku aktivní připojení k Azure, je příkladem připojení nebo odpojení.|
|Přidat nebo odebrat|Není destruktivní. Použijte při přidávání nebo odebírání něčeho ze seznamu.|Dialogové okno seznam serverů Správce připojení TFS je příkladem přidání/odebrání.|
|Odstranit|Stejné. Použijte pouze v případě, že odebraný prvek bude trvale vyřazen nebo odstraněn z disku.|Při odstranění se obvykle vyžaduje, aby se zobrazila výzva, pokud výsledek odstraňuje soubor z disku.|

## <a name="error-messages"></a>Chybové zprávy

### <a name="overview"></a>Přehled
 Dojde k chybám. Nastavení omezení pro to, co může uživatel provádět, je rozumné prvním krokem při předcházení neoprávněným chybovým zprávám. Pokud ale dojde k chybě, může být dobře napsaná chybová zpráva náročná na to, aby problém zmírnit. Chybové zprávy se pravděpodobně jedním z nejdůležitějších typů oznámení, které uživatel vidí, protože jsou synchronní a označují problém, který je potřeba vyřešit. Špatně napsané chybové zprávy přinechávají uživatelům své vlastní rozhodnutí, aby mohli určit příčinu chyb a všechna možná řešení.

 Uživatelé můžou přestat věnovat pozornost nepoužitým nebo nematoucím chybovým zprávám, takže zapisují jenom nezbytné zprávy, které přidávají k uživatelskému prostředí hodnotu. Pokud je zpráva pouhým oznámením, použijte alternativní prezentaci.

### <a name="rules-for-creating-an-error-message"></a>Pravidla pro vytvoření chybové zprávy

- Při sestavování chybových zpráv vyberte příslušnou úroveň chyby pro cílovou skupinu. Cílem pro jasné souhrny, které poskytují akci, kterou může uživatel přijmout (je-li k dispozici). Nestavte nic, co uživatel nemusí znát.

- Poskytněte konstruktivní pomoc. Čtení a zpracování chybové zprávy, která obsahuje instrukci, je snazší.

- Nepoužívejte dvojité záporné.

- Proveďte automatickou i ruční kontrolu pravopisu a kontrolu pravopisu u libovolné chybové zprávy, kterou píšete.

- U složitých chybových zpráv se vyhnete sekvenční komunikaci. Pro chybovou zprávu nikdy nepoužívejte propojení F1. Zpráva by měla být dostačující.

- Použijte správnou ikonu.

- Zjednodušte pochopení a používání tlačítek, která mají jasné možnosti, jako je například "odstranění" nebo "zrušit".

- Pro upozornění je jasné, co je to v souvislosti s tím, jak bude pokračovat. Tlačítka by měla označovat důsledek.

- V případě chyb popište, co může uživatel provést k vyřešení problému. Tlačítka by měla být akce nebo vyslovit "Zavřít". Pro chybovou zprávu nepoužívejte tlačítko OK.

- Některé otázky pro dotazování při vytváření chybové zprávy:

  - Může uživatel zjistit, jak problém vyřešit jedinou chybou?

  - Používá uživatel stejný slovník jako tuto chybu?

  - Je tato chyba ambigious nebo sdílená ve více situacích? Pokud ano, jak si můžete vyřídit uživatele pro řešení, které potřebují?

#### <a name="build-errors"></a>Chyby sestavení
 Vzhledem k tomu, že Visual Studio je nástroj pro vývoj softwaru, mnoho z jeho komponent má krok kompilace, převodu nebo kódování pro převod práce vývojáře do binárního formátu. Tyto převody mohou způsobit chyby, pokud kompilátor nemůže zpracovat nesprávně vytvořené soubory nebo když nejsou správně nastaveny možnosti kompilátoru.

 Uživatelé sady Visual Studio můžou při řešení chyb sestavení strávit mimořádně mnoho hodin vývoje. Tato doba řešení se zvyšuje, když chyby mají závislosti, nebo pokud jsou chybové zprávy špatně napsány, což může ztížit zjištění zdroje chyby.

 Nejlepší chyby sestavení jsou ty, které se nevyskytují v prvním místě, což je proč Visual Studio poskytuje funkce AutoComplete a IntelliSense. Validátory schémat a podobné nástroje poskytují stejný druh zpětné vazby. Tyto mechanismy proaktivně napomáhají uživateli vytvořit kód ve správném formátu a snížit pravděpodobnost chyb sestavení.

 Visual Studio poskytuje okno nástrojů, kde mohou uživatelé číst a procházet chyby, ke kterým došlo v oknech dokumentů. Klávesové zkratky jsou k dispozici, aby uživatel mohl rychle procházet velké množství kódu a přejít přímo do umístění problému. Visual Studio také umožňuje, aby každá chyba sestavení byla vázaná na konkrétní klíčové slovo nebo kontextové ID nápovědy, takže uživatel může přejít přímo k tématu nápovědy, které poskytuje podrobné informace o této chybě.

 Zapsat jasné a stručné chyby sestavení:

- **Používejte prostý jazyk** , který vysvětluje problém s malým nebo nežargonum kompilátoru. Text chyby sestavení by neměl být příliš technický.

- **Vytvořte si možné příčiny.** Například "chybí dvojtečka mezi vlastností a hodnotou v deklaraci" (vlastnost): (hodnota) ".

- Poskytněte podrobnosti o potenciálních opravách. Pokud není dostatek místa, mohou být do odpovídajícího tématu nápovědy vloženy další podrobnosti.

### <a name="components-of-a-well-written-error-message"></a>Součásti dobře napsané chybové zprávy

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Pro chybové zprávy použijte službu dialog prostředí.
 Pomocí služby dialogu prostředí můžete ovládat vzhled zprávy, zejména písma, a to bez podstatných změn v jednotlivých prvcích. Použijte mechanismy **IErrorInfo** a Sestavujte je pomocí **IVsUIShell:: SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Vyberte efektivní a odpovídající prezentaci oznámení.
 Pokud chcete zabránit ztrátě dat (synchronní oznámení), použijte modální dialog s kritickým upozorněním. Kritické ikony jsou vyhrazené pro situace, kdy se zpráva uzavírá bez jejich čtení, může vést k negativním důsledkům. Ztráta dat je kritická situace, která vyžaduje reakci na úrovni alarmu. Nadměrné využití ikony kritická má za uživatele desenzibilizující důležitost. Pokud je chybová zpráva v podstatě informativní, zvažte alternativy modálního dialogového okna (asynchronní oznámení).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Poskytněte čisté a stručné vysvětlení, proč k problému došlo, a ne technické vysvětlení.
 Přetěžující uživatelé s technickými podrobnostmi v vysvětlení budou pravděpodobněji ignorovat chybové zprávy. Příklady správného zasílání zpráv:

- "Nepovedlo se otevřít požadovaný soubor."

- "Nelze se připojit k Internetu".

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Zadejte informace o tom, jak tento problém vyřešit.
 Nabízí návrhy uživatelů, jak tento problém vyřešit. Pokud nejsou k dispozici žádné návrhy, je nutné, abyste byli na uživateli velmi velmi velmi Poskytněte přímé odkazy na alternativní online zdroje, jako je technická podpora nebo podpora komunity. Pokuste se uživatele nasměrovat na konkrétní online informace, které se týkají problému. Pro ID chyby zvažte možnost propojit uživatele s diskuzním vláknem o této konkrétní chybě. Příklady správného zasílání zpráv:

- "Ujistěte se, že jste připojení k Internetu, a zkuste tuto operaci znovu."

- "Zkontrolujte, zda soubor existuje a zda máte oprávnění k jeho otevření."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Napište zprávu, která je krátká a k bodu.
 Chybová zpráva může informovat, vysvětlit a nabízet řešení, ale i nadále ignorovat, pokud je příliš slovo. Jedním z řešení je použití postupného vyzrazení s tlačítkem Details (podrobnosti). Zadejte například krátký popis/řešení a potom na tlačítko Podrobnosti vložte více podrobností. Pokud se uživatel rozhodne přečíst si další informace o chybě, může to provést.

 Jazyk ve zprávě by měl:

- **Odpovídající doméně.** Použijte jazyk, který bude uživatel rozumět. I když naši zákazníci jsou vývojáři, často nemají kontext a terminologii, které máme.

- **Konkrétní.** Vyhněte se Vague slovům a poskytněte konkrétní názvy a umístění souvisejících objektů. Například chybová zpráva, například "znak je neplatný", není užitečná. Který znak? "Soubor nebyl nalezen." Který soubor?

- **Courteous.** Neviny uživatele nebo se mu nedaří Stupid. Vyhněte se nepřátelským nebo urážlivému jazyku (kill, Execute, ukončení, kritický, neplatný). Nepoužívejte text na velká písmena, který se často zobrazuje jako Shouting a není tak čitelný. Nepoužívejte humor.

- **Správně.** Používejte správnou kontrolu pravopisu a gramatiky (i v alfa). Překlepy jsou neprofesionální a absolutně.

- **Podle kontextového závislosti.** Použijte odpovídající text tlačítka. Vyhněte se tlačítku "OK" a místo toho použít "pokračovat" nebo "Ano/ne".

### <a name="error-message-examples"></a>Příklady chybových zpráv

|Dobré|Chybné|
|----------|---------|
|"Číslo, které jste vytočili, již není součástí služby. Zkontrolujte číslo a znovu ho vytočte nebo pro něj použijte volání 0. "|-"Error (449): neplatné číslo"<br />-"Tato Neošetřená chyba výjimky indikuje, že operace byla úspěšně dokončena."<br /><br /> ![Chybná chybová zpráva v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 – a_ErrorDialog")|

## <a name="accessing-help"></a>Přístup k nápovědě

### <a name="overview"></a>Přehled
 Kromě dokumentace na webu MSDN má uživatel sady Visual Studio několik přístupových bodů, které uživateli pomáhají při práci v uživatelském rozhraní. Aby se zajistilo, že jsou tyto přístupové body trvale dostupné, týmy funkcí potřebují využít systém pro usnadnění, který nabízí prostředí. Tyto přístupové body jsou:

- **Instruktážní a doplňkový text v dialogových oknech.** Statický text, který poskytuje směr nebo vysvětlení, buď na povrchu uživatelského rozhraní, nebo dostupný při najetí myší na ikonu informačního panelu

- **Nápověda F1** (pouze Editor). V rámci editoru sady Visual Studio může uživatel kdykoli důvěřovat, když stisknutím klávesy F1 zobrazíte téma nápovědy specifické pro aktuální výběr. Zajistěte, aby témata přidružená k F1 byla vhodná a informativní.

- **Hypertextové odkazy na témata nápovědy** Hypertextový odkaz v dialogovém okně, panelu nástrojů nebo návrhové ploše, který spustí téma, které uživateli pomáhá naučit se více o technologii, schopnosti nebo informace o tom, jak provést úlohu.

- **Mechanismy pomocníka uživatelského rozhraní, jako jsou inteligentní značky a vytváření dialogových oken.** Tyto mechanismy pomáhají uživateli v porozumění prvku uživatelského rozhraní nebo usnadnění úlohy, jako jsou například inteligentní značky nebo dialogy tvůrce.

- **Tlačítka pro pomocníka uživatelského rozhraní** (zastaralé). Viditelný indikátor v záhlaví, který poskytuje přístup k souvisejícímu tématu nápovědy F1.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Instruktážní a doplňkový text v dialogových oknech
 V dialogových oknech, které podporují složité úlohy, může být nutné poskytnout pokyny v uživatelském rozhraní, často v horní části dialogového okna nebo blízko složitých ovládacích prvků. Podrobnosti o psaní stylu naleznete v tématu [text a terminologie uživatelského rozhraní](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="infotips"></a>Informační popisy
 V uživatelském rozhraní se často může jednat o instruktážní text, který je příliš dlouhý, nebo může být užitečný jenom pro nové uživatele, takže zkušení uživatelé mají hodně na dobrém místě. V takovém případě by se pokyny a informační text měly umístit jako popis v popisu.

 Informační popisy by se měly umístit poblíž ovládacích prvků, ke kterým se vztahují, a měly by používat konkrétní ikonu informačního popisu, která se ještě nevšimla.

 ![Informační Tip v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 – d_InfoTip")

 **Příklad informačního popisu v aplikaci Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktivní mechanismy pomocníka

#### <a name="f1-help"></a>F1 – nápověda
 Nápověda F1 se vyžaduje v rámci editoru nebo návrhové plochy, ale ne jinde v prostředí Visual studia.

#### <a name="hyperlinks-to-help-topics"></a>Hypertextové odkazy na témata nápovědy
 Hypertextové odkazy lze použít k provedení akce, navigaci v rámci integrovaného vývojového prostředí (IDE) nebo spuštění nápovědě v prohlížeči. Podrobnosti o pravidlech a 07.10.01 tlačítek a hypertextových odkazech pro vizuální a rozložení najdete v tématu [text a terminologie uživatelského rozhraní](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) .

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Tlačítko Help [?] v záhlaví dialogových oken (zastaralé)
 Pro většinu částí jsou tlačítka Help [?] v záhlaví dialogových oken zastaralá. Témata uživatelského rozhraní již nejsou součástí našeho modelu doc, a proto nemusí být k dispozici příslušné téma k propojení. V podstatě bylo tlačítko záhlaví stejné jako Nápověda F1 a v dialogových oknech již není vyžadováno. V některých případech je možné tuto možnost i nadále používat jako indikátor, že jsou k dispozici více koncepčních nebo procedurálních informací, i když se hypertextové odkazy v novějším uživatelském rozhraní častěji používají.

##### <a name="dialogs-created-through-the-environment"></a>Dialogová okna vytvořená v prostředí
 Pomocí funkce **VBDialogBoxParam** se vytvářejí spousta dialogových oken prostředí. Tato sdílená funkce se aktualizovala, aby vám pomohla při přesunu tlačítka **pomoci** z tohoto dialogového okna do **?** tlačítko při zachování architektury, která je zpětně kompatibilní a rozšiřitelná.

 Konkrétně funkce **VBDialogBoxParam** podívá se na šablonu dialogového okna pro **tlačítko, jehož** ID je **IDHELP** (9) nebo popisek je Help nebo **&nápovědu**. Pokud je nalezeno tlačítko Help, je skryto a do dialogového okna je přidán **WS_EX_CONTEXTHELP** styl, který umístí **?** na záhlaví dialogového okna.

 Po vytvoření dialogového okna se tato procedura vloží do zásobníku a vyvolá dialogové okno s předzpracováním procedury dialogového okna s názvem **DialogPreProc**. Když **?** kliknete na tlačítko, pošle **WM_SYSCOMMAND** **SC_CONTEXTHELP** dialogového okna. **DialogPreProc** tento příkaz zachytí a změní jej na **WM_HELPovou** zprávu, která je předána do původní procedury dialogu.

 Většina dialogových oken vytvořených v prostředí má v dialogovém okně tlačítko pro podporu. Po zobrazení dialogového okna je tlačítko Help automaticky skryto a pouze **?** tlačítko funguje. Pokud **?** tlačítko se v systému Windows někdy odebralo nebo změnilo, toto řešení vám umožní rychle přejít zpátky na původní tlačítka.

 Toto řešení vytvoří čtyři předpoklady, které by mohly způsobit chyby:

- Tlačítko Help dialogového okna je **IDHELP** (9).

- Pokud je tlačítko Help skryté, dialogové okno vypadá správně.

- Dialogové okno nenahrazuje své návrat WinProc.

- Dialogové okno není vložené uvnitř jiného dialogového okna.

  Pokud se vaše dialogové okno nachází v Msenv a nepoužívá **VBDialogBoxParam**, prozkoumejte využití **VBDialogBoxParam** před implementací vlastní obslužné rutiny.

##### <a name="dialogs-created-through-other-packages"></a>Dialogová okna vytvořená prostřednictvím jiných balíčků
 Můžete implementovat vlastní řešení pro dialogy, které se nacházejí mimo Msenv. Pro sdílenou třídu dialogového okna ve VSPackage zvažte přesunutí tlačítka na záhlaví nebo implementaci obslužné rutiny v každém dialogovém okně. Následující kód je kostrou implementace, která vám může pomáhat začít:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Tlačítka pro podporu ve spravovaném kódu
 Přepsání výchozího chování tlačítka panelu záhlaví okna je snadné ve spravovaném kódu. Níže je kompletní ukázková aplikace, která demonstruje toto chování. V podstatě musíte přepsat metodu **WndProc** formuláře a pak při zachycení zprávy **SC_CONTEXTHELP** vyvolávat žádosti o nápovědu F1.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Viz také
- [Písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)
- [Rozložení pro Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)
- [Oznámení a průběh pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
