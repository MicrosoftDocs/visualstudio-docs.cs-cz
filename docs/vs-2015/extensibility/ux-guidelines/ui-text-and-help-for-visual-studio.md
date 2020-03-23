---
title: Text a nápověda uživatelského rozhraní
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea4f2b49838340fcee41bc9c41ef94558e44825e
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302320"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Text uživatelského rozhraní a nápověda pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="ui-text-and-terminology"></a><a name="BKMK_UITextAndTerminology"></a>Text a terminologie ui
 Srozumitelný text je rozhodující pro efektivní uI. Uživatelé softwaru mají tendenci nejprve číst štítky, a to ty, které jsou nejdůležitější pro dokončení úkolu. Statický text se čte s menší frekvencí. Naplánujte uživatelům zahájení pracovních relací pomocí rychlého prohledání celého okna, po kterém následuje čtení uživatelského okna v tomto přibližném pořadí:

1. Interaktivní ovládací prvky uprostřed

2. Tlačítka potvrzení

3. Interaktivní ovládací prvky nalezené jinde

4. Hlavní instrukce

5. Doplňující vysvětlení

6. Název okna

7. Jiný statický text v hlavním těle

### <a name="usage-patterns-for-ui-text"></a>Vzory použití textu ui

#### <a name="title-bar-text"></a>Text záhlaví
 Text záhlaví se musí shodovat s příkazem, který vytvořil ui.

#### <a name="instructional-text-helper-text"></a>Instruktážní text (pomocný text)
 V některých dialogových oknech je užitečné poskytnout hlavní pokyny, které vysvětlují, co dělat v okně nebo na stránce. To se někdy označuje jako "pomocný text."

##### <a name="writing-style-rules-for-helper-text"></a>Pravidla stylu psaní pro pomocné texty

- Nevysvětluj to, co je zřejmé. Pokud to není nezbytně nutné, nezahrnovat instruktážní text.

- Instruktážní text je vždy umístěn v horní části dialogového okna a měl by odkazovat na prováděnou úlohu.

- Přesně vysvětlit uživatelům, co je třeba udělat. Vyhněte se nadměrné komunikaci a redundanci.

- Zkontrolujte každé okno a odstraňte duplicitní slova a příkazy.

- Udržujte instruktážní text krátký. Pokud je pro určité uživatele nebo scénáře nezbytné další informace, zadejte odkaz na podrobné koncepční online téma.

- Napište text tak, aby každé slovo má váhu a je nezbytné.

- Postupujte podle existujících pokynů společnosti Microsoft pro text a [styl a tón](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx) [uživatelského rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) .

#### <a name="supplemental-instructions"></a>Doplňkové pokyny
 Doplňkové pokyny poskytují další informace, které pomáhají uživateli pochopit ovládací prvky nebo seskupení ovládacích prvků. To může také zahrnovat text nápovědy potřebný k pochopení, jaký formát vstupní ovládací prvek očekává. Používejte doplňkové pokyny střídmě. Rezervujte je pro případy, kdy je pravděpodobné, že uživatel nebude plně pochopit důsledky volby, které dělají.

 ![Doplňkový text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601-b_SupplementalText1")

 **Doplňkový text v sadě Visual Studio**

 ![Doplňkový text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601-c_SupplementalText2")

 **Doplňkový text v sadě Visual Studio**

#### <a name="infotips"></a>Informační tipy
 Často může být instruktážní text příliš zdlouhavý na to, aby se umístil na místě v uživatelském uživatelském nastavení, nebo může být užitečný pouze pro nové uživatele, což má pocit, že zkušení uživatelé jsou nepořádkem. V takovém případě by měl být instruktážní/informační text umístěn jako popis pod informačním tipem.

 Informační tipy by měly být umístěny v blízkosti ovládacích prvků, které souvisejí s a měly by používat konkrétní ikonu InfoTip, která je nenápadná, ale znatelná.

 ![Informační tip v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Příklad informačního tipu v sadě Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Pravidla stylu psaní pro informační tipy

- Napište informační tipy jako úplné věty. Vyžadují specifická slovesa, velká písmena věta a koncová interpunkce.

- Pomocí informačních tipů doplníte hlavní pokyny nebo informace. Pokud právě používáte různá slova, abyste přeformulovali hlavní myšlenku, nepotřebujete infotip.

- Mějte InfoTips krátké a sladké. Používejte malá slova a prostý, každodenní jazyk, který podporuje a povzbuzuje uživatele.

- Postupujte podle existujících pokynů společnosti Microsoft pro text a [styl a tón](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx) [uživatelského rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) .

#### <a name="control-labels"></a>Popisky ovládacích prvků
 Popisky ovládacích prvků by měly být krátké, stručné a podle [pokynů pro ovládací prvky na ploše systému Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx).

 Další informace o formátu popisku ovládacího prvku a umístění v uživatelském rozhraní naleznete [v části Rozložení pro visual studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Odkazy na nápovědu
 Odkazy nápovědy lze umístit do instruktážního textu nebo do těla hlavního použití. Mohou se na ně vymknou odkazy na nápovědu nebo spustí interní dialogová okna.

##### <a name="visual-style-rules-for-help-links"></a>Pravidla vizuálního stylu pro odkazy nápovědy

- Pro hypertextové odkazy použijte správné barvy prostředí. Správně stylizovaný hypertextový odkaz nebude po klepnutí krátce blikat červeně. Pokud se zobrazí toto, pak je to údaj, že barvy prostředí nejsou používány.

- Podtržení by se mělo používat pouze při najetí přes nebo když je odkaz vložen do odstavce.

- Podrobnější informace o vizuálních stylech a stylech interakce pro hypertextové odkazy naleznete v tématu Tlačítka a hypertextové odkazy.

##### <a name="writing-style-rules-for-help-links"></a>Psaní pravidel stylu pro odkazy nápovědy

- Při spouštění dialogových oken udržujte standardy pro tři tečky: žádné tři tečky pro navigaci, tři tečky, pokud úloha vyžaduje další uživatelské tlačítko.

     ![Odkaz nápovědy v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601-e_HelpLink")

     **Tři tečky (...) v odkazu nápovědy označují, že úloha bude vyžadovat další uI.**

- Odkazy by neměly začínat "Učit se", protože to není záměr uživatele. Uživatel chce odpovědět na konkrétní otázku, ne získat všeobecné vzdělání.

- Fráze nápověda odkazy tak, aby se zeptat na otázku, že téma bude odpovídat.

     Nesprávné: Další informace o cenách mobilních služeb Windows Azure

     Správně: "Jaké možnosti cen jsou dostupné pro mobilní služby Windows Azure?"

- Nikdy nepoužívejte *Tlačítko...* k textu odkazu.

- Nikdy nespojuj jen slovo "tady". To je problematické pro některé programy pro čtení z obrazovky, které budou vyjadřovat pouze slovo s hypertextovým odkazem.

     Nesprávné: "Najít informace o mobilních službách Windows Azure **zde**"

     Správně: "Jaké možnosti cen jsou dostupné pro mobilní služby Windows Azure?"

- Další informace o správném stylu psaní odkazů nápovědy naleznete v [nápovědě k ploše systému Windows](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).

#### <a name="hint-text"></a>Text nápovědy
 Text nápovědy se zobrazí jako vodoznak v ovládacím prvku nebo pod ovládacím prvkem. Správné formátování bude použito pomocí příslušného tokenu `Environment.GrayText`VSColors .

 Může se objevit v několika formách.

- Místo kontrolního štítku:

     ![Text nápovědy v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601-f_HintText1")

- Se slovesem, dávat pokyny:

     ![Text nápovědy v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601-g_HintText2")

- S textem označujícím požadovanou položku:

     ![Text nápovědy v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601-h_HintText3")

#### <a name="watermark-text"></a>Text vodoznaku
 Na prázdné návrhové ploše by měl text označovat, co dělat, a v případě potřeby poskytnout odkazy na otevření dalších souvisejících oken:

 ![Text vodoznaku v Sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601-i_WatermarkText")

 **Příklad textu vodoznaku v sadě Visual Studio**

### <a name="common-terminology"></a>Běžná terminologie

|Označení|Vysvětlení|Poznámka|
|----------|-----------------|-------------|
|Přihlásit se / odhlásit|Slovesa používaná jako synonymum pro web pro reprezentaci ověřování do webové vlastnosti. V rámci klientů to jednou používáme jako pojem nejvyšší úrovně pro přihlášení a odhlášení z připojení uživatelů ide, což představuje identitu nejvyšší úrovně, která poskytuje vyšší úrovně funkcí, jako je roaming a licencování, které nejsou k dispozici u všech ostatních připojení.|Uživatel ide je jedinou funkcí, která by měla představovat přihlášení / odhlásit sloveso, protože představuje uživatele ide nejvyšší úrovně.|
|Připojit / odpojit|Používá se v místech, kde funkce udržuje jedno připojení k online službě.|Průzkumník serveru, kde můžete mít současně jenom jedno aktivní připojení Azure, je příkladem připojení nebo odpojení.|
|Přidat / odebrat|Nedestruktivní. Používá se při přidávání nebo odebírání něčeho ze seznamu.|Dialogové okno seznamu serveru Správce připojení TFS je příkladem doplňku Přidat nebo odebrat.|
|Odstranění|Destruktivní. Použijte pouze v případě, že odebraný prvek bude trvale zahozen nebo odstraněn z disku.|"Odstranit" obvykle vyžaduje výzvu, pokud výsledek odstraní soubor z disku.|

## <a name="error-messages"></a>Chybové zprávy

### <a name="overview"></a>Přehled
 Dochází k chybám. Nastavení omezení na to, co uživatel může udělat, je rozumný první krok v prevenci vyhnout chybové zprávy. Pokud však dojde k chybě, může dobře napsaná chybová zpráva ujít dlouhou cestu ke zmírnění problému. Chybové zprávy jsou pravděpodobně jedním z nejdůležitějších typů oznámení, které uživatel vidí, protože jsou synchronní a označují problém, který je třeba vyřešit. Špatně napsané chybové zprávy nechávají uživatele samy o sobě, aby rozhodli o příčině chyb a možných řešeních.

 Uživatelé mohou přestat věnovat pozornost nadpoužívaným nebo matoucím chybové zprávy, takže napište pouze nezbytné zprávy, které přidávají hodnotu uživatelskému prostředí. Pokud je zpráva jednoduše oznámení, použijte alternativní prezentaci.

### <a name="rules-for-creating-an-error-message"></a>Pravidla pro vytvoření chybové zprávy

- Při vytváření chybových zpráv zvolte příslušnou úroveň chyb pro cílovou skupinu. Zaměřte se na jednoduché souhrny, které poskytují akci, kterou může uživatel provést, pokud je to možné. Neuvázejte nic, co uživatel nemusí vědět.

- Poskytovat konstruktivní pomoc. Je snazší číst a jednat na chybovou zprávu, která obsahuje instrukce.

- Nepoužívejte dvojité negativy.

- U všech chybových zpráv, které napíšete, proveďte automatickou i ruční kontrolu gramatiky a pravopisu.

- U složitých chybových zpráv se vyhněte sekvenční komunikaci. Nikdy nepoužívejte f1 přípojku pro chybovou zprávu. Samotná zpráva by měla být dostatečná.

- Použijte správnou ikonu.

- Usnadnit pochopení a použití tlačítek, která mají jasné volby, například "Odstranit" a Zrušit.

- U varování si ujasněte, jaký bude důsledek řízení. Tlačítka by měla uvádět důsledek.

- V případě chyb popište, co může uživatel provést k vyřešení problému. Tlačítka by měla být akce nebo vyslovit "Zavřít". Nepoužívejte tlačítko "OK" pro chybovou zprávu.

- Několik otázek, které si můžete položit při vytváření chybové zprávy:

  - Může uživatel zjistit, jak vyřešit problém s touto chybou sám?

  - Používá uživatel stejnou slovní zásobu jako tato chyba?

  - Je tato chyba ambigious nebo sdílené v několika situacích? Pokud ano, jak navádíte uživatele k řešení, které potřebují?

#### <a name="build-errors"></a>Chyby sestavení
 Vzhledem k tomu, že Visual Studio je nástroj pro vývoj softwaru, mnoho jeho součástí mají kompilaci, převod nebo kódování krok převést práci vývojáře do binární formě. Tyto převody mohou způsobit chyby, když kompilátor nemůže zpracovat nesprávně vytvořené soubory nebo když nebyly správně nastaveny možnosti kompilátoru.

 Uživatelé sady Visual Studio mohou strávit obrovský počet hodin vývoje při řešení chyb sestavení. Tato doba řešení se zvyšuje, pokud chyby mají závislosti nebo pokud jsou chybové zprávy špatně napsané, což může ztížit odhalení zdroje chyby.

 Nejlepší chyby sestavení jsou ty, které se nevyskytují v první řadě, což je důvod, proč Visual Studio poskytuje automatické dokončování a IntelliSense klikyháky. Validátory schématu a podobné nástroje poskytují stejný druh zpětné vazby. Tyto mechanismy proaktivně vést uživatele k vytvoření dobře formátovaný kód, snižuje pravděpodobnost chybsestavení.

 Visual Studio poskytuje okno nástroje, kde uživatelé mohou číst a procházet chyby, ke kterým došlo v jejich oknech dokumentu. Klávesové zkratky jsou k dispozici tak, aby uživatel mohl rychle procházet velké množství kódu a přejít přímo na umístění problému. Visual Studio také umožňuje, aby byla každá chyba sestavení svázána s určitým id klíčového slova nebo kontextu nápovědy, aby uživatel mohl přejít přímo na téma nápovědy, které poskytuje podrobnější informace o chybě.

 Napište jasné, stručné chyby sestavení:

- **Použijte prostý jazyk,** který vysvětluje problém s malým nebo žádným žargonem kompilátoru. Text chyby sestavení by neměl být příliš technický.

- **Nastínit možné příčiny.** Například "Chybí dvojtečka mezi vlastnosta a hodnota v deklaraci '(vlastnost) : (hodnota)"."

- Uveďte podrobnosti o možných opravách. Pokud není dostatek místa, mohou být do odpovídajícího tématu nápovědy vloženy další podrobnosti.

### <a name="components-of-a-well-written-error-message"></a>Součásti dobře napsané chybové zprávy

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Chybové zprávy slouží k použití dialogového okna prostředí.
 Pomocí služby dialogového okna prostředí můžete řídit vzhled zprávy – zejména písma – bez větších změn jednotlivých prvků. Použijte mechanismy **IErrorInfo** a oznamte je pomocí **prostředí IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Zvolte efektivní a vhodnou prezentaci oznámení.
 Modální dialogové okno s kritickým upozorněním použijte, pokud je nutná okamžitá akce, aby se zabránilo ztrátě dat (synchronní oznámení). Kritické ikony jsou vyhrazeny pro situace, ve kterých zavření zprávy bez čtení může vést k negativním důsledkům. Ztráta dat je kritická situace, která vyžaduje odezvu na úrovni alarmu. Nadužívání kritické ikony znecitlivuje uživatele k jeho důležitosti. Pokud je chybová zpráva informační povahy, zvažte alternativy k modálnímu dialogu (asynchronní oznámení).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Poskytněte čisté a stručné vysvětlení, proč k problému došlo, spíše než technické vysvětlení.
 Přetížení uživatelů s technickými podrobnostmi v vysvětlení způsobí, že budou více ignorovat chybové zprávy. Příklady dobrých zpráv:

- "Požadovaný soubor nelze otevřít."

- "Nelze se připojit k Internetu."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Zadejte informace o tom, jak problém vyřešit.
 Nabídněte uživatelům návrhy, jak problém vyřešit. Buďte k uživateli upřímní, pokud nejsou žádné návrhy. Poskytněte přímé odkazy na alternativní online zdroje, jako je technická podpora nebo komunitní podpora. Pokuste se nasměrovat uživatele na konkrétní online informace týkající se problému. Chcete-li získat ID chyby, zvažte propojení uživatelů s diskusním vláknem o této konkrétní chybě. Příklady dobrých zpráv:

- "Ujistěte se, že jste připojeni k Internetu, a akci opakujte."

- "Ujistěte se, že soubor existuje a že máte oprávnění k jeho otevření."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Napište zprávu, která je krátká a k věci.
 Chybová zpráva může upozornit, vysvětlit a nabídnout řešení, ale stále ignorovat, pokud je příliš rozvláčný. Jedním z řešení je použití progresivního zveřejnění s tlačítkem podrobností. Uveďte například krátký popis/řešení a poté pod tlačítko podrobnosti uveďte další podrobnosti. Pokud se uživatelé rozhodnou přečíst si další informace o chybě, mohou tak učinit.

 Jazyk ve zprávě by měl být:

- **Vhodné pro doménu.** Používejte jazyk, kterému uživatel bude rozumět. I když jsou naši zákazníci vývojáři, často nemají kontext a terminologii, kterou máme.

- **Specifické.** Vyhněte se vágní formulace a uveďte konkrétní názvy a umístění objektů zapojených. Například chybová zpráva, například "znak je neplatný" není užitečné. Jakou postavu? "Soubor nebyl nalezen." Který soubor?

- **Zdvořilý.** Neobviňujte uživatele, nebo aby se cítili hloupě. Vyhněte se nepřátelské nebo urážlivé jazyk (zabít, provést, ukončit, fatální, nelegální). Vyhněte se textu s velkými písmeny, který je často považován za křik a není tak čitelný. Nepoužívej humor.

- **Správné.** Používejte správný pravopis a gramatiku (i v alfách). Překlepy jsou neprofesionální a trapné.

- **Kontextově vhodné.** Použijte odpovídající text tlačítka. Vyhněte se tlačítku "OK" a místo toho použijte "Pokračovat" nebo "Ano/Ne".

### <a name="error-message-examples"></a>Příklady chybových zpráv

|Dobré|Chybné|
|----------|---------|
|"Číslo, které jste vytočili, již není v provozu. Zkontrolujte číslo a vytočte znovu nebo vytočte 0 pro operátora."|- "Chyba (449): Nelegální číslo"<br />- "Tato neošetřená chyba výjimky označuje, že operace byla úspěšně dokončena."<br /><br /> ![Chybná chybová zpráva v sadě Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602-a_ErrorDialog")|

## <a name="accessing-help"></a>Přístup k nápovědě

### <a name="overview"></a>Přehled
 Kromě dokumentace v msdn, visual studio uživatel má několik přístupových bodů, které pomáhají uživateli v uživatelském rozhraní. Aby bylo zajištěno, že tyto přístupové body jsou konzistentně k dispozici, musí týmy funkcí využít systém nápovědy, který nabízí prostředí. Tyto přístupové body jsou:

- **Instruktážní a doplňkový text v dialogových oknech.** Statický text, který poskytuje směr nebo vysvětlení, buď na povrchu uj.

- **Nápověda F1** (pouze editor). V editoru sady Visual Studio může uživatel kdykoli důvěřovat, že stisknutím klávesy F1 zobrazíte téma nápovědy specifické pro aktuální výběr. Ujistěte se, že témata spojená s F1 jsou vhodné a informativní.

- **Hypertextové odkazy na témata nápovědy.** Hypertextový odkaz v dialogovém okně, okně nástroje nebo návrhové ploše, který spouští téma, které pomáhá uživateli dozvědět se více o technologii, schopnostech nebo informacích o tom, jak provést úkol.

- **Pomocné mechanismy ui, jako jsou inteligentní značky a vytváření dialogových oken.** Tyto mechanismy pomáhají uživateli pochopit prvek uživatelského rozhraní nebo usnadňují úlohu, jako jsou inteligentní značky nebo dialogová okna tvůrce.

- **Tlačítka nápovědy ui** (zastaralé). Viditelný indikátor v záhlaví, který umožňuje přístup k souvisejícímu tématu nápovědy F1.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Instruktážní a doplňkový text v dialogových oknech
 V dialogových oknech, které podporují složité úkoly, může být potřeba poskytnout instruktážní text v rámci uj. Podrobnosti o stylu psaní najdete v [textu a terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) uj.

#### <a name="infotips"></a>Informační tipy
 Často může být instruktážní text příliš zdlouhavý na to, aby se umístil v uživatelském uživatelském nastavení, nebo může být užitečný pouze pro nové uživatele, což má pro zkušené uživatele pocit nepořádek. V takovém případě by měl být instruktážní/informační text umístěn jako popis pod informačním tipem.

 Informační tipy by měly být umístěny v blízkosti ovládacích prvků, které souvisejí s a měly by používat konkrétní ikonu InfoTip, která je nenápadná, ale znatelná.

 ![Informační tip v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601-d_InfoTip")

 **Příklad informačního tipu v sadě Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktivní mechanismy nápovědy

#### <a name="f1-help"></a>F1 – nápověda
 F1 Nápověda je vyžadována v editoru nebo návrhu povrchu, ale ne jinde v prostředí sady Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hypertextové odkazy na témata nápovědy
 Hypertextové odkazy lze použít k provedení akce, navigaci v rámci prostředí IDE nebo spuštění nápovědy v prohlížeči. Podrobnosti o jazyce a tlačítkách a hypertextových odkazech 07.10.01 najdete v tématu Text uživatelského rozhraní [a terminologie.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Tlačítka nápovědy [?] v záhlaví dialogového okna (zastaralé)
 Tlačítka nápovědy [?] v záhlaví dialogových oken jsou z větší části zastaralá. Témata s ui již nejsou součástí našeho modelu doc, a proto nemusí být relevantní téma, na které by bylo možné odkazovat. V podstatě bylo tlačítko záhlaví totéž jako nápověda F1 a to již není v dialogových oknech vyžadováno. V některých případech to lze stále použít jako indikátor, že je k dispozici více koncepčních nebo procedurálních informací, ačkoli hypertextové odkazy se častěji používají v novějším uzly.

##### <a name="dialogs-created-through-the-environment"></a>Dialogy vytvořené prostřednictvím prostředí
 Mnoho dialogových oken prostředí je vytvořeno pomocí funkce **VBDialogBoxParam.** Tato sdílená funkce byla aktualizována, aby pomohla přesunout tlačítko **Nápověda** z dialogového okna do **okna ?** a zároveň zachovat architekturu, která je zpětně kompatibilní a rozšiřitelná.

 Konkrétně funkce **VBDialogBoxParam** vyhledá šablonu dialogu pro tlačítko, jehož ID je **IDHELP** (9) nebo popisek je **nápověda** nebo **&nápověda**. Pokud je nalezeno tlačítko nápovědy, je skryté a **WS_EX_CONTEXTHELP** styl je přidán do dialogového okna, který umístí **?** v záhlaví dialogu.

 Po vytvoření dialogového okna odešle dialogové okno proc do zásobníku a vyvolá dialogové okno s dialogem proc proc s názvem **DialogPreProc**. Když **se ?** kliknul, odešle do dialogu **WM_SYSCOMMAND** **SC_CONTEXTHELP.** **DialogPreProc** zachytí tento příkaz a změní jej na **zprávu WM_HELP,** která je předána původní dialogové okno proc.

 Většina dialogových oken vytvořených prostředím má v dialogovém okně tlačítko Nápověda. Když se zobrazí dialogové okno, tlačítko Nápověda je automaticky skryto a pouze **?** tlačítko funguje. Pokud **se ?** je někdy odstraněn nebo změněn v systému Windows, toto řešení umožňuje rychle přejít zpět na původní tlačítka nápovědy.

 Toto řešení vytváří čtyři předpoklady, které by mohly způsobit chyby:

- Tlačítko nápovědy dialogového okna je **IDHELP** (9).

- Dialogové okno vypadá správně, když je tlačítko Nápověda skryté.

- Dialogové okno nenahrazuje jeho winproc.

- Dialogové okno není vloženo do jiného dialogového okna.

  Pokud váš dialog je umístěn v msenv a nepoužívá **VBDialogBoxParam**, prozkoumejte využití **VBDialogBoxParam** před implementací vlastní obslužné rutiny.

##### <a name="dialogs-created-through-other-packages"></a>Dialogy vytvořené prostřednictvím jiných balíčků
 Můžete implementovat vlastní řešení pro dialogy, které jsou umístěny mimo msenv. Pro sdílené dialogové okno třídy v VSPackage, zvažte přesunutí tlačítka do záhlaví nebo implementace obslužné rutiny v každém dialogovém okně. Následující kód je kostra implementace, které vám pomohou začít:

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

##### <a name="help-buttons-in-managed-code"></a>Tlačítka nápovědy ve spravovaném kódu
 Přepsání výchozího chování tlačítka nápovědy záhlaví okna je ve spravovaném kódu snadné. Níže je kompletní demo aplikace, která demonstruje toto chování. V podstatě je třeba přepsat metodu **WndProc** formuláře a poté vypálit žádosti nápovědy F1, když je zachycena **SC_CONTEXTHELP** zpráva.

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
 [Písma a formátování pro](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) rozložení sady Visual Studio pro [oznámení a průběh](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) sady [Visual](../../extensibility/ux-guidelines/layout-for-visual-studio.md) Studio
