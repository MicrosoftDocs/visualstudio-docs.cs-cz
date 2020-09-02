---
title: Vzory aplikací pro Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 036c95951fe3dc9e65a0f3338f75ae9867d721c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698598"
---
# <a name="application-patterns-for-visual-studio"></a>Vzory aplikací pro Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a> Interakce oken

### <a name="overview"></a>Přehled
Dva hlavní typy oken používané v aplikaci Visual Studio jsou editory dokumentů a okna nástrojů. Vzácná, ale možná, jsou velká nemodální dialogová okna. I když jsou v prostředí všechny nemodální, jejich vzory jsou zásadním rozdílem. Tato část se zabývá rozdílem mezi okny dokumentu, okny nástrojů a nemodálními dialogy. V [dialogových oknech](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)jsou pokryté modální vzory dialogových oken.

### <a name="comparing-window-usage-patterns"></a>Porovnávání vzorů využití oken
**Okna dokumentů** se téměř vždy zobrazují v dokumentaci dokumentu. Díky tomu má Editor dokumentů "prostřední fáze" k uspořádání doplňkových oken nástrojů.

**Panel nástrojů** se nejčastěji zobrazuje jako samostatné, menší okno sbalené s okrajem integrovaného vývojového prostředí (IDE). Tato možnost může být viditelná, skrytá nebo automaticky skrytá. Někdy se však okna nástrojů zobrazují v dokumentaci dokumentu tím, že v okně zrušíte kontrolu vlastností **okna nebo ukotvení** . Výsledkem je, že se jedná o další realitu, ale také o běžném rozhodnutí o návrhu: při pokusu o integraci do sady Visual Studio je nutné se rozhodnout, zda má vaše funkce Zobrazit okno nástroje nebo okno dokumentu.

V aplikaci Visual Studio se nedoporučuje **nemodální dialogová okna** . Většina nemodálních dialogových oken je, podle definice, okna plovoucího panelu a měla by být implementovaná tímto způsobem. Nemodální dialogová okna jsou povolená v případech, kdy by velikost normálního okna nástroje ukotveného pro danou stranu prostředí byla příliš omezená. Jsou povolené taky v případech, kdy by uživatel mohl přesunout dialogové okno do sekundárního monitorování.

Pečlivě se zamyslete nad tím, který typ kontejneru potřebujete. Běžné požadavky vzorů použití pro návrh uživatelského rozhraní jsou uvedené v následující tabulce.

||Okno dokumentu|Okno nástroje|Nemodální dialogové okno|
|-|---------------------|-----------------|---------------------|
| **Position** | Vždy umístěn v dokumentaci dokumentu a není ukotven kolem okrajů rozhraní IDE. Může být "vypnul", takže se z hlavního prostředí odpluje odděleně. | Obecně ukotvení karet kolem hran prostředí IDE, ale lze je přizpůsobit tak, aby bylo plovoucí, automaticky skryté (nepřipnutý), nebo ukotveno v dokumentaci dokumentu.|Velké plovoucí okno oddělené od rozhraní IDE. |
| **Model potvrzení** | *Zpožděné potvrzení*<br /><br /> Aby bylo možné data uložit v dokumentu, musí uživatel vydat příkaz ** &gt; Uložit**, **Uložit jako**nebo **Uložit vše** . Okno dokumentu má koncept dat v rámci něj "změněných" a pak se potvrdí do jednoho z příkazů pro uložení. Při zavírání okna dokumentu se veškerý obsah buď uloží na disk, nebo se ztratí. | *Okamžité potvrzení*<br /><br /> Neexistuje žádný model uložení. Pro okna inspektora nástroje, která pomáhají při úpravách souboru, musí být soubor otevřen v aktivním editoru nebo Návrháři a editor nebo Návrhář vlastní uložení. | *Zpožděné nebo okamžité potvrzení*<br /><br /> Většinou velké dialogové okno s nemodálním dialogovým oknem vyžaduje akci potvrdit změny a umožňuje operaci zrušit, která vrátí všechny změny provedené v relaci dialogu.  To odlišuje nemodální dialogové okno z okna nástrojů v tom, že okna nástrojů mají vždy model okamžitého potvrzení. |
| **Přehlednost** | *Otevřít/vytvořit (soubor) a zavřít*<br /><br /> Otevírání oken dokumentu se provádí buď otevřením existujícího dokumentu, nebo pomocí šablony k vytvoření nového dokumentu. Není k dispozici žádný \<specific editor> příkaz "otevřít". | *Skrýt a zobrazit*<br /><br /> Okna nástrojů s jednou instancí se dají skrýt nebo zobrazit. Obsah a stavy v okně nástroje uchovávají, zda jsou zobrazeny nebo skryty. Okna nástrojů s více instancemi lze zavřít a také skrýt. Když je okno nástroje s více instancemi zavřené, obsah a stav v rámci okna nástroje jsou zahozeny. | *Spuštěno z příkazu*<br /><br /> Dialogová okna se spouští z příkazu založeného na úlohách. |
| **Instance** | *Více instancí*<br /><br /> Několik editorů lze současně otevřít a upravovat různé soubory, zatímco některé editory také umožňují otevření stejného souboru ve více než jednom editoru (pomocí příkazu **okna &gt; nové okno** ).<br /><br /> Jeden editor může upravovat jeden nebo více souborů současně (Návrhář projektu). | *Jedna nebo více instancí*<br /><br /> Obsah se mění tak, aby odrážel kontext (jako v prohlížeči vlastností), nebo předávat fokus/kontext do jiných oken (Seznam úkolů Průzkumník řešení).<br /><br /> Okna s aktivním dokumentem by mělo být přidruženo k oknu s aktivním dokumentem, pokud neexistuje přesvědčivý důvod. | *Jedna instance* |
| **Příklady** | Editory **textu**, jako je editor kódu<br /><br /> **Návrhové plochy**, jako je Návrhář formuláře nebo plocha modelování<br /><br /> **Rozložení ovládacích prvků podobně jako dialogová okna**, jako je například Návrhář manifestu | **Průzkumník řešení** poskytuje řešení a projekty obsažené v řešení.<br /><br /> **Průzkumník serveru** poskytuje hierarchické zobrazení serverů a datových připojení, která uživatel zvolí k otevření v okně. Otevření objektu z hierarchie databáze, jako je dotaz, otevře okno dokumentu a umožní uživateli upravit dotaz.<br /><br /> **Prohlížeč vlastností** zobrazuje vlastnosti objektu vybraného buď v okně dokumentu, nebo v jiném okně nástroje. Vlastnosti jsou uvedeny buď v hierarchickém zobrazení mřížky, nebo v komplexních ovládacích prvcích podobného dialogu a umožňují uživateli nastavit hodnoty těchto vlastností. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a> Okna nástrojů

### <a name="overview"></a>Přehled
Okna nástrojů podporují práci uživatele, která se nachází v oknech dokumentů. Lze je použít k zobrazení hierarchie reprezentující základní kořenový objekt, který poskytuje aplikace Visual Studio a může s nimi manipulovat.

Při zvažování nového okna nástrojů v integrovaném vývojovém prostředí by autoři měli:

- Použijte existující okna nástrojů, která jsou vhodná pro úlohu, a nevytvářejte nová s podobnými funkcemi. Nové okna nástrojů by se měla vytvořit jenom v případě, že nabízejí výrazně odlišný nástroj nebo funkci, která se nedá integrovat do podobného okna, nebo když existující okno převedete do služby Pivot hub.

- V horní části okna nástroje použijte standardní panel příkazů (v případě potřeby).

- Musí být konzistentní se vzory, které už existují v jiných oknech nástrojů pro řízení prezentace a navigace pomocí klávesnice.

- Je konzistentní s prezentací řízení v jiných oknech nástrojů.

- Pokud je to možné, můžete nastavit automatické zobrazení oken nástrojů pro konkrétní dokument, aby se zobrazila pouze při aktivaci nadřazeného dokumentu.

- Zajistěte, aby byl obsah okna naviguje klávesnicí (podpora kláves se šipkami).

#### <a name="tool-window-states"></a>Stavy oken nástrojů
Okna nástrojů sady Visual Studio mají různé stavy, z nichž některé jsou aktivovány uživatelem (například funkce automatického skrývání). Další stavy, jako je automaticky viditelné, umožňují, aby se okna nástrojů zobrazovala ve správném kontextu a skryla, pokud není potřeba. Celkem je pět oken nástrojů.

- Okna **ukotveného/připnutého** nástroje lze připojit k libovolné ze čtyř stran v oblasti dokumentu. Ikona připínáček se zobrazí v záhlaví okna nástroje. Okno nástroje může být ukotveno vodorovně nebo svisle podél okraje prostředí a dalších oken nástrojů a může také být propojeno s kartami.

- **Automaticky skrytá** okna nástrojů jsou odpojena. Okno může vysouvat snímek z pohledu a opustit kartu (s názvem panelu nástrojů a jeho ikonou) na okraji oblasti dokumentu. Okno nástroje vysune snímek, když uživatel najede myší na kartu.

- Automaticky **zobrazovaná** okna nástrojů se automaticky zobrazí, když se spustí další část uživatelského rozhraní, jako je editor, nebo se získá fokus.

- **Plovoucí** nástrojů okna se najeďte mimo rozhraní IDE. To je užitečné při konfiguracích s více monitory.

- Okna nástrojů **dokumentu s kartami** lze ukotvit v dokumentaci dokumentu. To je užitečné pro velká okna nástrojů, jako je Prohlížeč objektů, které potřebují větší realitu než ukotvení k okrajům rámce.

![Stavy oken nástrojů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702 – 01_ToolWindowStates")<br />Stavy oken nástrojů v aplikaci Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Jedna instance a více instancí
Okna nástrojů jsou buď jedna instance, nebo více instancí. K aktivnímu oknu dokumentu může být přidruženo několik oken nástrojů s jedním instancí, zatímco okna nástrojů s více instancemi nemusí být. Okna nástrojů s více instancemi reagují na příkaz **okna &gt; Nový okno** vytvořením nové instance okna. Následující obrázek znázorňuje okno nástroje, které povoluje příkaz New Window, když je instance okna aktivní:

![Okno nástroje, které povoluje příkaz ' nové okno ', když je aktivní instance okna](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702 – 02_ToolWindowEnablingCommand")<br />Okno nástroje, které povoluje příkaz ' nové okno ', když je aktivní instance okna

Okna nástrojů s jednou instancí se dají skrýt nebo zobrazit, zatímco okna nástrojů s více instancemi se dají zavřít i skrýt. Všechna okna nástrojů mohou být ukotvena, karta propojená, plovoucí nebo nastavená jako podřízené okno rozhraní MDI (více dokumentů) (podobně jako okno dokumentu). Všechna okna nástrojů by měla reagovat na příslušné příkazy správy okna v nabídce okna:

![Příkazy správy oken v nabídce okna sady Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702 – 03_WindowManagementControls")<br />Příkazy správy oken v nabídce okna sady Visual Studio

#### <a name="document-specific-tool-windows"></a>Okna nástrojů specifických pro dokument
Některá okna nástrojů jsou navržena tak, aby se změnila v závislosti na daném typu dokumentu. Tyto Windows se průběžně aktualizují, aby odrážely funkce použitelné pro aktivní okno dokumentu v integrovaném vývojovém prostředí.

Příklady oken nástrojů, jejichž obsah se mění tak, aby odrážel vybraný editor, jsou sada nástrojů a Osnova dokumentu. Tato okna ukazují meze, když má Editor fokus, který nenabízí kontext pro okno.

#### <a name="navigable-list-tool-windows"></a>Okna nástrojů seznamu naviguje
Některá okna nástrojů zobrazují seznam naviguje položek, se kterými může uživatel pracovat. V tomto typu okna by vždy měla být zpětná vazba na aktuální položku v seznamu, i když je okno neaktivní. Seznam by měl reagovat na příkazy **GoToNextLocation** a **GoToPrevLocation** , když se změní aktuálně vybraná položka v okně.

Příklady oken nástrojů seznamu naviguje jsou Průzkumník řešení a okno výsledky hledání.

### <a name="tool-window-types"></a>Typy oken nástrojů

#### <a name="common-tool-windows-and-their-functions"></a>Společná okna nástrojů a jejich funkce

**Okna hierarchických nástrojů**

| Okno nástroje | Funkce |
| --- | --- |
| Průzkumník řešení | Hierarchický strom, který zobrazuje seznam dokumentů obsažených v projektech, různých souborech a položkách řešení. Zobrazení položek v projektech je definováno balíčkem, který vlastní typ projektu (například typy založené na odkazech, adresáře nebo kombinovaného režimu). |
| zobrazení tříd | Hierarchický strom tříd a různé prvky v pracovní sadě dokumentů, nezávisle na samotných souborech. |
| Průzkumník serveru | Hierarchický strom, který zobrazuje všechny servery a datová připojení v řešení. |
| Osnova dokumentu | Hierarchická struktura aktivního dokumentu. |

**Okna nástrojů mřížky**

| Okno nástroje | Funkce |
| --- | --- |
| Vlastnosti | Mřížka, která zobrazuje seznam vlastností pro vybraný objekt, spolu s nástrojem pro výběr hodnot pro úpravu těchto vlastností. |
| Seznam úkolů | Mřížka, která umožňuje uživateli vytvářet, upravovat a odstraňovat úkoly a komentáře. |

**Okna nástrojů obsahu**

| Okno nástroje | Funkce |
| --- | --- |
| Nápověda | Okno, které umožňuje uživatelům přístup k různým metodám získání přístupu, od "jak to?" videa na fórech MSDN. |
| Dynamická Help | Okno nástroje, které zobrazuje odkazy na témata nápovědy platná pro aktuální výběr. |
| prohlížeč objektů | Sada rámců se dvěma sloupci se seznamem hierarchických komponent objektů v levém podokně a vlastnostmi a metodami objektu v pravém sloupci. |

**Okna nástrojů dialogu**

| Okno nástroje | Funkce |
| --- | --- |
| Vyhledávání | Dialog, který uživateli umožňuje najít nebo najít a nahradit v různých souborech v rámci řešení. |
| Rozšířené hledání | Dialog, který uživateli umožňuje najít nebo najít a nahradit v různých souborech v rámci řešení. |

**Další okna nástrojů**

::: moniker range="vs-2017"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Panel nástrojů, který slouží k ukládání prvků, které budou přehozeny na návrhové plochy, poskytuje konzistentní zdroj přetažení pro všechny návrháře. |
| Úvodní stránka | Portál uživatele do sady Visual Studio s přístupem k informačním kanálům pro vývojáře, nápovědě pro Visual Studio a poslední projekty. Uživatelé mohou také vytvořit vlastní úvodní stránky zkopírováním souboru StartPage. XAML z adresáře "Common7\IDE\StartPages \" programu Visual Studio Program Files do složky StartPages v adresáři dokumentů sady Visual Studio a následným úpravou XAML ručně nebo jeho otevřením v aplikaci Visual Studio nebo v jiném editoru kódu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Panel nástrojů, který slouží k ukládání prvků, které budou přehozeny na návrhové plochy, poskytuje konzistentní zdroj přetažení pro všechny návrháře. |

::: moniker-end

**Okna nástrojů ladicího programu**

| Okno nástroje | Funkce |
| --- | --- |
| Automatické hodnoty ||
| Projev ||
| Výstup | Okno výstup lze použít vždy, když máte textové události nebo stav k deklaraci. |
| Paměť ||
| Zarážky ||
| Spuštěný ||
| Dokumenty ||
| Zásobník volání ||
| Místní hodnoty ||
| Sleduje ||
| Zpětný překlad ||
| Registrovat ||
| Vlákna ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Konvence editoru dokumentů

### <a name="document-interactions"></a>Interakce dokumentů
"Document redocuments" je největší místo v rámci rozhraní IDE a je tam, kde se uživatel obecně zaměřuje na jejich pozornost, aby mohl dokončit své úkoly, což je pomocná pro další okna nástrojů. Editory dokumentů reprezentují základní pracovní jednotky, které uživatel otevře a ukládá v rámci sady Visual Studio. Zachovají silný smysl výběru vázaných na Průzkumník řešení nebo jiná okna s aktivní hierarchií. Uživatel by měl být schopný nasměrovat na jedno z těchto oken hierarchie a zjistit, kde je dokument obsažený, a jeho vztah k řešení, projektu nebo jinému kořenovému objektu poskytovanému balíčkem sady Visual Studio.

Úpravy dokumentů vyžadují konzistentní uživatelské prostředí. Aby se uživatel mohl soustředit na místo na základě správy oken a hledání příkazů, vyberte strategii zobrazení dokumentu, která nejlépe odpovídá uživatelským úkolům pro úpravu tohoto typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Běžné interakce pro dokumentaci dokumentu

- Udržujte konzistentní model interakce v běžném **novém souborovém** prostředí a **otevřeném souboru** .

- Aktualizuje související funkce v souvisejících oknech a nabídkách, když se otevře okno dokumentu.

- Příkazy nabídky jsou vhodně integrované do běžných nabídek, jako jsou **Úpravy**, **formátování**a **zobrazení** nabídek. Pokud jsou k dispozici podstatné množství specializovaných příkazů, lze vytvořit novou nabídku. Tato nová nabídka by měla být viditelná pouze v případě, že dokument má fokus.

- Vložený panel nástrojů může být umístěn v horní části editoru. Je vhodnější mít samostatný panel nástrojů, který se zobrazí mimo editor.

- Vždy udržovat výběr v Průzkumník řešení nebo podobné aktivní hierarchii okna.

- Dvakrát klikněte na dokument v Průzkumník řešení by měl provést stejnou akci jako **otevřená**.

- Pokud je možné použít pro typ dokumentu více než jeden editor, uživatel by měl mít možnost přepsat nebo obnovit výchozí akci pro daný typ dokumentu pomocí dialogového okna **otevřít v aplikaci** kliknutím pravým tlačítkem myši na soubor a výběrem možnosti **otevřít** v z místní nabídky.

- Nevytvářejte průvodce ve správném dokumentu.

### <a name="user-expectations-for-specific-document-types"></a>Očekávání uživatelů pro konkrétní typy dokumentů
Existuje několik různých základních typů editorů dokumentů a každá z nich obsahuje sadu interakcí, které jsou konzistentní s jinými uživateli stejného typu.

- **Textový editor:** Editor kódu, soubory protokolu

- **Návrhová plocha:** Návrhář formulářů WPF, Windows Forms

- **Editor stylu dialogového okna:** Návrhář manifestu, vlastnosti projektu

- **Návrhář modelů:** Návrhář pracovního postupu, codemap, diagram architektury, průběh

K dispozici je také několik typů bez editoru, které používají dokumentaci dokumentu. I když neupravují samotné dokumenty, musí sledovat standardní interakce pro okna dokumentů.

- **Sestavy:** Sestava IntelliTrace, sestava technologie Hyper-V, sestava profileru

- **Řídicí panel:** Centrum diagnostiky

#### <a name="text-based-editors"></a>Editory založené na textu

- Dokument se účastní modelu karty Preview a umožňuje zobrazení náhledu dokumentu bez jeho otevření.

- Struktura dokumentu může být reprezentována v okně doprovodného nástroje, jako je například Osnova dokumentu.

- Technologie IntelliSense (Pokud je vhodná) se bude chovat konzistentně s dalšími editory kódu.

- Automaticky otevíraná okna nebo uživatelské rozhraní se řídí podobnými styly a vzorci pro existující podobné uživatelské rozhraní, například CodeLens.

- Zprávy týkající se stavu dokumentu se zobrazí v ovládacím prvku informační panel v horní části dokumentu nebo ve stavovém řádku.

- Uživatel musí být schopný přizpůsobit vzhled písma a barev pomocí stránky **možnosti > nástrojů** , buď na stránce Sdílená písma a barvy, nebo v editoru, který je specifický pro Editor.

#### <a name="design-surfaces"></a>Návrhové plochy

- Prázdný Návrhář by měl mít vodoznak na povrchu, který označuje, jak začít.

- Mechanismy přepínání zobrazení budou následovat po stávajících vzorech, jako je například Dvojí kliknutí, otevřít Editor kódu nebo karty v okně dokumentu, které umožňují interakci s oběma podokny.

- Přidávání prvků na návrhovou plochu by mělo být provedeno prostřednictvím sady nástrojů, pokud není vyžadováno vysoce specifické okno nástroje.

- Položky na povrchu budou následovat po konzistentním modelu výběru.

- Vložené panely nástrojů obsahují pouze příkazy specifické pro dokument, nikoli běžné příkazy, jako je například **Save**.

#### <a name="dialog-style-editors"></a>Editory stylu dialogového okna

- Rozložení ovládacího prvku by mělo dodržovat normální konvence rozložení dialogového okna.

- Karty v editoru by se neměly shodovat s vzhledem karet dokumentu, měly by odpovídat jednomu ze dvou povolených stylů karet interiéru.

- Uživatelé musí být schopni pracovat s ovládacími prvky pouze pomocí klávesnice; buď aktivací editoru a tabulátorů prostřednictvím ovládacích prvků nebo pomocí standardních symbolických instrukcí.

- Návrhář by měl použít společný model uložení. Na povrchu by se neměla umístit žádná tlačítka pro uložení ani potvrzení, i když můžou být vhodná další tlačítka.

#### <a name="model-designers"></a>Návrháři modelů

- Prázdný Návrhář by měl mít vodoznak na povrchu, který označuje, jak začít.

- Přidávání prvků na návrhovou plochu by mělo být provedeno prostřednictvím sady nástrojů.

- Položky na povrchu budou následovat po konzistentním modelu výběru.

- Vložené panely nástrojů obsahují pouze příkazy specifické pro dokument, nikoli běžné příkazy, jako je například **Save**.

- Legenda se může zobrazit na povrchu, a to buď orientační, nebo vodoznak.

- Uživatel musí být schopný přizpůsobit vzhled písma a barev pomocí stránky **nástroje > možnosti** , buď na stránce Sdílená písma a barvy, nebo v editoru, který je specifický pro Editor.

#### <a name="reports"></a>Sestavy

- Sestavy jsou typicky jenom pro informace a nepodílejí se na uložení modelu. Můžou ale zahrnovat interakci, jako jsou odkazy na jiné relevantní informace nebo oddíly, které rozšiřují a sbalí.

- Většina příkazů na povrchu by měla být hypertextové odkazy, ne tlačítka.

- Rozložení by mělo obsahovat hlavičku a postupovat podle standardních pokynů pro rozložení sestav.

#### <a name="dashboards"></a>Řídicí panely

- Řídicí panely nemají samotný model interakce, ale slouží jako způsob, jak nabízet celou řadu dalších nástrojů.

- Neúčastní se v modelu uložení.

- Uživatelé musí být schopni pracovat s ovládacími prvky pouze pomocí klávesnice, a to buď aktivací editoru a procházením pomocí ovládacích prvků, nebo pomocí standardních symbolických instrukcí.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a> Dialogových oknech

### <a name="introduction"></a>Úvod
Dialogová okna v aplikaci Visual Studio by obvykle podporovala jednu diskrétní jednotku práce uživatele a pak byla zrušena.

Pokud jste zjistili, že potřebujete dialog, máte tři možnosti, v pořadí podle priority:

1. Integrujte své funkce do jednoho ze sdílených dialogových oken v aplikaci Visual Studio.

2. Vytvořte si vlastní dialog pomocí vzoru nalezeného v existujícím podobném dialogovém okně.

3. Vytvořte nové dialogové okno, podle pokynů pro interakci a rozložení.

Tato část popisuje, jak zvolit správný vzor dialogového okna v rámci pracovních postupů sady Visual Studio a běžné konvence pro návrh dialogu.

### <a name="themes"></a>Motivy
Dialogová okna v aplikaci Visual Studio se řídí jedním ze dvou základních stylů:

#### <a name="standard-unthemed"></a>Standardní (neexistují)
Většina dialogových oken je standardní dialogová okna a měla by být nepevná. Neprovádějte znovu šablony běžných ovládacích prvků nebo se pokuste vytvořit stylizovaná "moderní" tlačítka nebo ovládací prvky. Vzhled ovládacích prvků a stylu okolí se řídí [standardními pokyny pro interakci s desktopovým systémem Windows pro dialogová okna](/windows/desktop/uxguide/win-dialog-box)

#### <a name="themed"></a>S motivem
Dialogová okna signatura můžou být tematická. Dialogová okna motivů mají odlišný vzhled, který má také některé speciální vzory interakce spojené se stylem. Motivujte dialog pouze v případě, že splňuje tyto požadavky:

- Dialog je běžné prostředí, které uvidí a často používá mnoho uživatelů (například dialogové okno **Nový projekt** ).

- Dialog obsahuje výrazné prvky značky produktu (například dialogové okno **Nastavení účtu** ).

- Dialogové okno se zobrazí jako nedílnou součást většího toku, který obsahuje další dialogová okna s motivem (například dialogové okno **Přidat připojenou službu** ).

- Dialog je důležitou součástí prostředí, které hraje strategickou roli při povýšení nebo odlišení verze produktu.

Při vytváření dialogového okna s motivem použijte příslušné barvy prostředí a sledujte správné vzory rozložení a interakce. (Viz [rozložení pro Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Návrh dialogu
Dobře navržené dialogy přijímají následující prvky:

- Podporovaný úkol uživatele

- Styl textu dialogového okna, jazyk a terminologie

- Možnosti řízení a zásady uživatelského rozhraní

- Specifikace vizuálního rozložení a zarovnání ovládacího prvku

- Přístup ke klávesnici

#### <a name="content-organization"></a>Organizace obsahu
Vezměte v úvahu rozdíly mezi těmito základními typy dialogových oken:

- [Jednoduché dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) představují ovládací prvky v jednom modálním okně. Prezentace může zahrnovat variace komplexních vzorů ovládacích prvků, včetně výběru polí nebo panelu ikon.

- [Vrstvená dialogová okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se používají k zajištění většiny zobrazení na obrazovce, když jedna část uživatelského rozhraní zahrnuje více skupin ovládacích prvků. Seskupení dialogů jsou "vrstvená" prostřednictvím ovládacích prvků TAB, ovládacích prvků navigace v seznamu nebo tlačítek, aby uživatel mohl zvolit, které seskupení se zobrazí v daném okamžiku.

- [Průvodci](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) jsou užitečné pro přesměrování uživatele prostřednictvím logické sekvence kroků k dokončení úkolu. Řady možností jsou nabízeny v sekvenčních panelech, někdy ale zabývají různé pracovní postupy ("větve") závislé na výběru provedeném na předchozím panelu.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a> Jednoduchá dialogová okna
Jednoduchý dialog je prezentace ovládacích prvků v jednom modálním okně. Tato prezentace může zahrnovat variace složitých vzorů ovládacích prvků, jako je například výběr polí. Pro jednoduché dialogy použijte standardní obecné rozložení a také všechna konkrétní rozložení nutná pro komplexní seskupení ovládacích prvků.

![ Příkladem jednoduchého dialogového okna v aplikaci Visual Studio je>vytvořit klíč se silným názvem.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704 – 01_CreateStrongNameKey")<br />Vytvoření klíče se silným názvem je příkladem jednoduchého dialogového okna v aplikaci Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Vrstvená dialogová okna
Vrstvená dialogová okna zahrnují karty, řídicí panely a vložené stromy. Používají se k maximalizaci skutečné nemovitosti, pokud je v jedné části uživatelského rozhraní nabídnuto více skupin ovládacích prvků. Seskupení jsou vrstvená tak, aby si uživatel mohl kdykoli zobrazit.

V nejjednodušším případě je mechanismus pro přepínání mezi seskupeními ovládací prvek karta. K dispozici je několik alternativ. Jak zvolit nejvhodnější styl, najdete v tématu určení priorit a vrstvení.

Dialogové **okno &gt; Možnosti nástrojů** je příkladem vrstveného dialogového okna s vloženým stromem:

![Nástroje > možnosti jsou příkladem vrstveného dialogového okna v aplikaci Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704 – 02_ToolsOptions")<br />Nástroje > možnosti jsou příkladem vrstveného dialogového okna v aplikaci Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a> Průvodc
Průvodci jsou užitečné pro přesměrování uživatele prostřednictvím logické sekvence kroků při dokončení úkolu. Řada možností je nabízena v sekvenčních panelech a uživatel musí pokračovat v každém kroku, než bude pokračovat na další. Jakmile jsou k dispozici dostatečné výchozí hodnoty, je tlačítko **Dokončit** povolené.

 Modální průvodci se používají pro úlohy, které:

- Obsahuje větvení, kde se v závislosti na volbách uživatele nabízejí různé cesty.

- Obsahuje závislosti mezi kroky, kde jsou další kroky závislé na vstupu uživatele z předchozích kroků.

- Jsou dostatečně složité, aby bylo možné použít uživatelské rozhraní k vysvětlení nabízených možností a možných výsledků v jednotlivých krocích.

- Jsou transakce, které vyžadují provedení sady kroků v celém rozsahu před potvrzením změn

### <a name="common-conventions"></a>Běžné konvence
Chcete-li dosáhnout optimálního návrhu a funkcí v dialogových oknech, postupujte podle těchto konvencí o velikosti dialogového okna, pozici, standardech, konfiguraci a zarovnání ovládacího prvku, textu uživatelského rozhraní, záhlavích, ovládacích tlačítkech a přístupových klíčích.

Pokyny pro konkrétní rozložení najdete v tématu [rozložení pro Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Velikost
Dialogy by se měly přizpůsobit minimálnímu rozlišení obrazovky v 768 a velikost počátečního dialogového okna by neměla přesáhnout 900x700 pixelů. Dialogová okna mohou mít velikost, ale nejedná se o požadavek.

K dispozici jsou dvě doporučení pro dialogová okna umožňující změnu velikosti:

1. Minimální velikost je definována pro dialog, který se optimalizuje pro sadu ovládacího prvku bez oříznutí, a upravuje tak, aby vyhovovala přijatelnému růstu lokalizace.

2. Zda velikost škálované uživatelem přetrvá z relace do relace. Například pokud uživatel škáluje dialogové okno na 150%, pak se následné spuštění dialogového okna zobrazí na 150%.

#### <a name="position"></a>Pozice
Dialogová okna musí být při prvním spuštění zobrazena uprostřed v rámci integrovaného vývojového prostředí. Poslední pozici dialogových oken bez změny velikosti není nutné zachovat, takže se budou zobrazovat uprostřed při následném spuštění.

Pro dialogová okna umožňující změnu velikosti by měla být velikost při následném spuštění trvalá. V případě modálních dialogových oken s možností změny velikosti nemusí být pozice trvalá. Zobrazení, která se centrují v rámci integrovaného vývojového prostředí (IDE), brání možnosti dialogového okna se v nepředvídatelné nebo nepoužitelné pozici, když se změnila konfigurace zobrazení uživatele.

Pro nemodální dialogová okna, která se dají přemístit, se má při následném spuštění udržovat poloha uživatele, protože dialogové okno se často používá jako nedílnou součást rozsáhlejšího pracovního postupu.

Když se dialogová okna musí zacházet v jiných dialogových oknech, horní dialogové okno by se mělo napravit doprava a dolů od nadřazeného, aby bylo zřejmé, že uživatel přešel na nové místo.

#### <a name="modality"></a>Modální
Modální znamená, že uživatelé jsou před pokračováním vyzváni k dokončení nebo zrušení dialogu. Vzhledem k tomu, že modální dialogová okna blokují uživateli možnost vzájemně pracovat s ostatními částmi prostředí, měl by tento tok úlohy používat co možná nejvíce zřídka. Když je nutná modální operace, Visual Studio má řadu sdílených dialogů, do kterých můžete integrovat své funkce. Pokud je nutné vytvořit nové dialogové okno, postupujte podle vzorce interakce existujícího dialogu s podobnými funkcemi.

Když uživatelé potřebují provádět dvě aktivity najednou, třeba **Najít** a **nahradit** při psaní nového kódu, dialog by měl být nemodální, aby uživatel mohl snadno přepínat mezi nimi. Visual Studio obecně používá okna nástrojů pro tento druh propojeného úkolu podporujícího Editor.

#### <a name="control-configuration"></a>Konfigurace ovládacího prvku
Být konzistentní s existujícími konfiguracemi ovládacích prvků, které mají stejnou věc v aplikaci Visual Studio.

#### <a name="title-bars"></a>Záhlaví

- Text v záhlaví musí odrážet název příkazu, který ho spustil.

- V záhlaví dialogových oken by se neměla používat žádná ikona. V případech, kdy systém vyžaduje jednu, použijte logo sady Visual Studio.

- Dialogová okna by neměla mít tlačítka pro minimalizaci a maximalizaci.

- Tlačítka podpory v záhlaví jsou zastaralá. Nepřidávat je do nových dialogových oken. Pokud existují, měli byste spustit téma nápovědy, které je pro úkol koncepčně relevantní.

  ![Specifikace zásad pro záhlaví v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704 – 03_TitleBarSpecs")<br />Specifikace zásad pro záhlaví v dialogových oknech sady Visual Studio

#### <a name="control-buttons"></a>Řídicí tlačítka
V pravém dolním rohu dialogového okna by se měla zobrazovat tlačítka v oblasti Obecné, **OK**, **Zrušit**a **pomáhat** vodorovně. Alternativní vertikální zásobník je povolený, pokud dialogové okno obsahuje několik dalších tlačítek v dolní části dialogového okna, které by představovalo vizuální nejasnost s ovládacími tlačítky.

![Přijatelné konfigurace pro řídicí tlačítka v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704 – 04_ControlButtonConfig")<br />Přijatelné konfigurace pro řídicí tlačítka v dialogových oknech sady Visual Studio

Dialogové okno musí obsahovat výchozí ovládací tlačítko. Pokud chcete určit nejvhodnější příkaz, který se má použít jako výchozí, vyberte jednu z následujících možností (v pořadí podle priority):

- Jako výchozí vyberte nejbezpečnější a nejbezpečnější příkaz. To znamená, že volba příkazu pravděpodobně brání ztrátě dat a vyhne se neúmyslnému přístupu k systému.

- Pokud ztráta dat a zabezpečení nejsou faktory, zvolte výchozí příkaz založený na pohodlí. Zahrnutí nejpravděpodobnějšího příkazu jako výchozího bude zlepšit pracovní postup uživatele v případě, že dialog podporuje časté nebo opakované úkoly.

Nevybírejte pro výchozí příkaz trvale destruktivní akci. Pokud je takový příkaz k dispozici, vyberte místo toho bezpečnější příkaz jako výchozí.

#### <a name="access-keys"></a>Přístupové klíče
Nepoužívejte přístupové klávesy pro tlačítka **OK**, **Zrušit**nebo **pomáhat** . Ve výchozím nastavení jsou tato tlačítka namapována na klávesové zkratky:

| Název tlačítka | Klávesová zkratka |
| --- | --- |
| OK | Enter |
| Zrušit | Esc |
| Nápověda | F1 |

#### <a name="imagery"></a>Obrázcích
Používejte v dialogových oknech jenom obrázky. V dialogových oknech nepoužívejte velké ikony pouze k použití místa. Použijte image jenom v případě, že jsou důležitou součástí přenosu zprávy uživateli, jako jsou ikony upozornění nebo animace stavu.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a> Stanovení priorit a vrstvení

#### <a name="prioritizing-your-ui"></a>Určení priorit uživatelského rozhraní
Může být nutné přenést do Forefrontu určité prvky uživatelského rozhraní a umístit pokročilejší chování a možnosti (včetně překrytí příkazů) do dialogových oken. Vydejte do Forefrontu často používané funkce tím, že pro ni využijete místo a v uživatelském rozhraní se zobrazí textový popisek, když se zobrazí dialogové okno.

#### <a name="layering-your-ui"></a>Vrstvení uživatelského rozhraní
Pokud jste zjistili, že je nezbytné dialogové okno, ale související funkce, které chcete uživateli prezentovat, překročí rámec toho, co se dá zobrazit v jednoduchém dialogu, pak musíte své uživatelské rozhraní navrstvit. Nejběžnější metody vrstvení, které Visual Studio používá, jsou karty a předsálí nebo řídicí panely. V některých případech můžou být vhodné oblasti, které se dají rozbalit a sbalit. Adaptivní uživatelské rozhraní se obecně nedoporučuje v aplikaci Visual Studio.

Existují výhody a nevýhody různých metod rozhraní vrstvení prostřednictvím ovládacích prvků na základě karet. Projděte si níže uvedený seznam a ujistěte se, že zvolíte techniku vrstvení, která je vhodná pro vaši situaci.

##### <a name="tabbing"></a>Přecházení

| Přepínání mechanismu | Výhody a vhodné použití | Nevýhody a nevhodné použití |
| --- | --- | --- |
| Ovládací prvek karta | Seskupení dialogových stránek logické skupiny do souvisejících sad<br /><br />Užitečné pro méně než pět (nebo počet karet, které odpovídají jednomu řádku v rámci dialogového okna) stránky souvisejících ovládacích prvků v dialogovém okně<br /><br />Popisky karet musí být krátké: jedno nebo dvě slova, která můžou snadno identifikovat obsah.<br /><br />Běžný styl dialogového okna systému<br /><br />Příklad: ** &gt; vlastnosti položky Průzkumníka souborů** | Vytváření popisných krátkých popisků může být obtížné.<br /><br />Obecně se v jednom dialogu neškáluje za pět karet.<br /><br />Nevhodné, pokud máte příliš mnoho karet pro jeden řádek (použijte jinou techniku vrstvení)<br /><br />Nerozšiřitelné |
| Navigační panel | Jednoduché přepínání zařízení, které může obsahovat více kategorií než karet<br /><br />Plochý seznam kategorií (bez hierarchie)<br /><br />Rozšiřiteln<br /><br />Příklad: **přizpůsobení... &gt; Přidat příkaz** | Není dobré používat vodorovný prostor, pokud je méně než tři skupiny.<br /><br />Úloha může být vhodnější pro rozevírací seznam. |
| Ovládací prvek strom | Umožňuje neomezený počet kategorií.<br /><br />Umožňuje seskupování a hierarchii kategorií.<br /><br />Rozšiřiteln<br /><br />Příklad: ** &gt; Možnosti nástrojů** | Silně vnořené hierarchie můžou způsobit nadměrné horizontální posouvání.<br /><br />Visual Studio má nadčetnost zobrazení stromové struktury. |
| Tip | Pomáhá s dokončením úkolu tím, že uživatele odgeneruje pomocí sekvenčních kroků na základě úkolů: průvodce představuje úlohu vysoké úrovně a jednotlivé panely představují dílčí úkoly potřebné k provedení celkové úlohy.<br /><br />Užitečné v případě, že úloha přechází mezi hranicemi uživatelského rozhraní, jako by uživatel jinak musel použít více editorů a oken nástrojů k dokončení úkolu.<br /><br />Užitečné v případě, že úkol vyžaduje větvení<br /><br />Užitečné v případě, že úloha obsahuje závislosti mezi kroky<br /><br />Užitečné v případě, že se dá v jednom dialogu předložit několik podobných úloh s jedním rozhodovacím rozvětvem, aby se snížil počet různých podobných dialogových oken. | Nevhodné pro všechny úlohy, které nevyžadují sekvenční pracovní postup<br /><br />Průvodce může být zahlcený a zmatený průvodcem s příliš velkým počtem kroků<br /><br />Průvodci mají svou podstatu omezený přehled o obrazovkách. |

##### <a name="hallways-or-dashboards"></a>Předsálí nebo řídicí panely
Předsálí a řídicí panely jsou dialogová okna nebo panely, které slouží jako spouštění bodů pro ostatní dialogová okna a okna. Dobře navržený "někde" hned rozsvítí jenom nejběžnější možnosti, příkazy a nastavení a umožňuje uživateli snadno provádět běžné úlohy. Podobně jako Real-World někde zajišťuje přístup k místnostem za nimi, toto méně běžné uživatelské rozhraní se shromáždí do samostatných "místností" (často se jedná o další dialogová okna) souvisejících funkcí, ke kterým se dá získat přístup z hlavní někde.

Alternativně je řídicí panel, který nabízí všechny dostupné funkce v jedné kolekci namísto refaktoringu méně častých funkcí do samostatných umístění.

![Někde koncept pro vystavení dalšího uživatelského rozhraní v Outlooku](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704 – 08_Hallway")<br />Někde koncept pro vystavení dalšího uživatelského rozhraní v Outlooku

##### <a name="adaptive-ui"></a>Adaptivní uživatelské rozhraní
Zobrazení nebo skrytí uživatelského rozhraní na základě využití nebo přihlášeného prostředí uživatele je dalším způsobem, jak předkládat potřebné uživatelské rozhraní při skrývání dalších částí. V sadě Visual Studio to nedoporučujeme, protože algoritmy pro rozhodování o zobrazení nebo skrytí uživatelského rozhraní můžou být obtížné a pravidla budou pro určitou sadu případů vždy špatná.

## <a name="projects"></a><a name="BKMK_Projects"></a> Projekty

### <a name="projects-in-the-solution-explorer"></a>Projekty v Průzkumník řešení
Většina projektů je klasifikována jako založená na odkazech, v adresáři nebo v kombinaci. Všechny tři typy projektů jsou v Průzkumník řešení podporovány současně. V rámci tohoto okna se koná kořen uživatelského prostředí při práci s projekty. I když různé uzly projektu jsou referenční, adresář nebo projekty typu kombinovaného režimu, existuje společný vzor interakce, který by měl být použit jako výchozí bod před rozdílním na uživatelské vzory specifické pro projekt.

Projekty by měly vždy:

- Podpora možnosti přidávat složky projektu pro uspořádání obsahu projektu

- Udržování konzistentního modelu pro trvalost projektu

Projekty by měly také udržovat konzistentní modely interakce pro:

- Odebírání položek projektu

- Ukládání dokumentů

- Úpravy vlastností projektu

- Úprava projektu v alternativním zobrazení

- Operace přetažení

### <a name="drag-and-drop-interaction-model"></a>Model interakce přetažení
Projekty jsou obvykle klasifikovány jako odkazy založené na odkazech (schopné uchovávat pouze odkazy na položky projektu v úložišti), založené na adresářích (schopné trvale uchovávat pouze položky projektu, které jsou fyzicky uloženy v rámci hierarchie projektu), nebo smíšené (schopnost uchovávat odkazy nebo fyzické položky). Integrované vývojové prostředí (IDE) splňuje všechny tři typy projektů současně v rámci **Průzkumník řešení**.

Z perspektivy přetažení by měly být následující vlastnosti použity pro každý typ projektu v rámci **Průzkumník řešení**:

- **Projekt založený na odkazech:** Klíčovým bodem je, že projekt přetahuje odkaz na položku v úložišti. Pokud projekt založený na odkazech funguje jako zdroj operace přesunutí, měl by odebrat pouze odkaz na položku z projektu. Položka by ve skutečnosti neměla být odstraněna z pevného disku. Pokud projekt založený na odkazech funguje jako cíl operace přesunutí (nebo kopírování), měl by přidat odkaz na původní zdrojovou položku, aniž by bylo nutné vytvořit soukromou kopii položky.

- **Projekt založený na adresáři:** Z pohledu přetažení, projekt přetahuje kolem fyzické položky namísto odkazu. Když projekt založený na adresáři funguje jako zdroj pro operaci přesunu, měl by se ukončit odstranění fyzické položky z pevného disku a její odebrání z projektu. Když projekt založený na adresáři funguje jako cíl operace přesunutí (nebo kopírování), měl by vytvořit kopii zdrojové položky v jejím cílovém umístění.

- **Smíšený cílový projekt:** Z pohledu přetažení je chování tohoto typu projektu založeno na potažení položky (buď odkaz na položku v úložišti, nebo na samotnou položku). Správné chování pro odkazy a fyzické položky jsou popsány výše.

Pokud v **Průzkumník řešení**existoval pouze jeden typ projektu, operace přetažení budou jednoduché. Vzhledem k tomu, že každý systém projektu má možnost definovat vlastní chování při přetahování, měly by být dodrženy určité pokyny (na základě chování při přetahování v Průzkumníkovi Windows), aby se zajistilo předvídatelné uživatelské prostředí:

- Nezměněná operace přetažení v **Průzkumník řešení** (pokud nejsou stisknuté klávesy CTRL ani Shift), měla by být výsledkem operace přesunutí.

- Operace přesunu by měla způsobit také operaci přesunutí.

- Operace CTRL-retáhnutí by měla mít za následek operaci kopírování.

- Referenční a smíšené systémy projektů podporují pojem přidání odkazu (nebo odkazu) na zdrojovou položku. Pokud jsou tyto projekty cílem operace přetažení (když je **kombinace kláves CTRL + SHIFT** ), měla by být výsledkem odkaz na položku přidanou do projektu.

Ne všechny operace přetahování jsou rozumné napříč kombinacemi projektů založených na odkazech, adresářových a smíšených projektů. Konkrétně je problematický, aby předstírat, že umožňuje operaci přesunutí mezi zdrojovým projektem založeným na adresářích a cílovým projektem na základě odkazu, protože zdrojový projekt založený na adresáři bude muset po dokončení přesunutí odstranit zdrojovou položku. Cílový projekt na základě odkazu by pak ukončil odkaz na odstraněnou položku.

Je také zavádějící jako předstírat pro povolení operace kopírování mezi těmito typy projektů, protože cílový projekt založený na odkazu by neměl vytvářet nezávislou kopii zdrojové položky. Podobně CTRL + SHIFT přetahování na cílový projekt založený na adresářích by neměl být povolen, protože projekt založený na adresáři nemůže uchovávat odkazy. V případě, že operace přetažení není podporována, IDE by měl zakázat přetažení a zobrazit uživatele jako ukazatel bez přetažení (zobrazeno v tabulce ukazatelů níže).

Aby bylo možné správně implementovat chování při přetahování, musí zdrojový projekt přetažení sdělit svůj charakter cílovému projektu. (Například je odkazem na adresář?) Tyto informace jsou označeny formátem schránky, který je nabízený zdrojem. Jako zdroj operace přetažení (nebo operace kopírování schránky) by měl projekt nabízet buď `CF_VSREFPROJECTITEMS` nebo v `CF_VSSTGPROJECTITEMS` závislosti na tom, zda je projekt založen na odkazech nebo v adresáři. Oba tyto formáty mají stejný datový obsah, který se podobá `CF_HDROP` formátu Windows s výjimkou toho, že seznam řetězců místo názvů souborů je dvojitě `NULL` ukončený seznam `Projref` řetězců (vrácený z `IVsSolution::GetProjrefOfItem` nebo `::GetProjrefOfProject` podle potřeby).

Jako cíl operace Drop (nebo vložení do schránky) by měl projekt přijmout `CF_VSREFPROJECTITEMS` a `CF_VSSTGPROJECTITEMS` , i když přesné zpracování operace přetažení se liší v závislosti na povaze cílového projektu a zdrojového projektu. Zdrojový projekt deklaruje jeho povahu, ať už nabízí `CF_VSREFPROJECTITEMS` nebo `CF_VSSTGPROJECTITEMS` . Cílem přetažení je pochopení své vlastní povahy a má proto dostatek informací, aby bylo možné rozhodnout, zda má být proveden přesun, kopírování nebo odkaz. Uživatel také upraví, která operace přetažení by měla být provedena stisknutím kláves CTRL, Shift nebo kláves CTRL a Shift. Je důležité, aby cíl přetažení správně označoval, která operace bude provedena předem v rámci svých `DragEnter` metod a `DragOver` . **Průzkumník řešení** automaticky ví, zda je zdrojový projekt a cílový projekt stejný projekt.

Přetahování položek projektu mezi instancemi aplikace Visual Studio (například z jedné instance devenv.exe do jiné) se konkrétně nepodporuje. **Průzkumník řešení** ho také přímo zakáže.

Uživatel by měl vždy být schopný určit účinek operace přetažení tím, že vybere položku, přetáhne ji do cílového umístění a bude pozorovat, který z následujících ukazatelů myši se zobrazí před vyřazením položky:

| Ukazatel myši | Příkaz | Popis |
| :---: | --- | --- |
| ![Ikona bez přesunutí](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706 – 01_MouseNoDrop") | Bez zrušení | Položku nelze vyřadit do zadaného umístění. |
| ![Ikona kopírovat myši](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706 – 02_MouseCopy") | Kopírovat | Položka bude zkopírována do cílového umístění. |
| ![Ikona přesunu myši](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706 – 03_MouseMove") | Přesunout | Položka bude přesunuta do cílového umístění. |
| ![Myš "Přidat odkaz" – ikona](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706 – 04_MouseAddRef") | Přidání odkazu | Odkaz na vybranou položku se přidá do cílového umístění. |

#### <a name="reference-based-projects"></a>Projekty založené na odkazech
 Následující tabulka shrnuje operace přetahování (a také funkce vyjmout/kopírovat/vložit), které by se měly provést na základě povýšení pro cílové projekty určené pro odkazy na základě povahy zdrojové položky a modifikačních kláves:

| Modifikátor | Kategorie | Zdrojová položka: odkaz nebo odkaz | Zdrojová položka: fyzická položka nebo systém souborů ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Žádný modifikátor | Akce | Přesunout | Odkaz |
| Žádný modifikátor | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Žádný modifikátor | Zdroj | Odstraní odkaz na původní položku. | Uchová původní položku. |
| Žádný modifikátor | Výsledek | `DROPEFFECT_MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_LINK` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| Shift + přetáhnout | Akce | Přesunout | Bez zrušení |
| Shift + přetáhnout | Cíl | Přidá odkaz na původní položku. | Bez zrušení |
| Shift + přetáhnout | Zdroj | Odstraní odkaz na původní položku. | Bez zrušení |
| Shift + přetáhnout | Výsledek | `DROPEFFECT_MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | Bez zrušení |
| Ctrl + přetažení | Akce | Kopírovat | Bez zrušení |
| Ctrl + přetažení | Cíl | Přidá odkaz na původní položku. | Bez zrušení |
| Ctrl + přetažení | Zdroj | Zachová odkaz na původní položku. | Bez zrušení |
| Ctrl + přetažení | Výsledek | `DROPEFFECT_COPY` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | Bez zrušení |
| CTRL + SHIFT + přetažení | Akce | Odkaz | Odkaz |
| CTRL + SHIFT + přetažení | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| CTRL + SHIFT + přetažení | Zdroj | Zachová odkaz na původní položku. | Uchová původní položku. |
| CTRL + SHIFT + přetažení | Výsledek | `DROPEFFECT_LINK` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_LINK` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| CTRL + SHIFT + přetažení | Poznámka | Stejné jako chování při přetahování pro zkratky v Průzkumníkovi Windows. ||
| Vyjmout/vložit | Akce | Přesunout | Odkaz |
| Vyjmout/vložit | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Vyjmout/vložit | Zdroj | Zachová odkaz na původní položku.|Uchová původní položku. |
| Vyjmout/vložit | Výsledek | Položka zůstane v úložišti v původním umístění. | Položka zůstane v úložišti v původním umístění. |
| Kopírovat/vložit | Akce | Kopírovat | Odkaz |
| Kopírovat/vložit | Zdroj | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Kopírovat/vložit | Výsledek | Zachová odkaz na původní položku. | Uchová původní položku. |
| Kopírovat/vložit | Akce | Položka zůstane v úložišti v původním umístění. | Položka zůstane v úložišti v původním umístění. |

#### <a name="directory-based-projects"></a>Projekty založené na adresářích
Následující tabulka shrnuje operace přetahování (a také funkce vyjmout/kopírovat/vložit), které by se měly provádět na základě povýšení pro cílové projekty v adresářích, a to v závislosti na povaze zdrojové položky a modifikačních kláves:

| Modifikátor | Kategorie | Zdrojová položka: odkaz nebo odkaz | Zdrojová položka: fyzická položka nebo systém souborů ( `CF_HDROP` ) |
|-----------------|----------| - | - |
| Žádný modifikátor | Akce | Přesunout | Přesunout |
| Žádný modifikátor | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Žádný modifikátor | Zdroj | Odstraní odkaz na původní položku. | Odstraní odkaz na původní položku. |
| Shift + přetáhnout | Akce | Přesunout | Přesunout |
| Shift + přetáhnout | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Shift + přetáhnout | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Shift + přetáhnout | Výsledek | `DROPEFFECT_MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| Ctrl + přetažení | Akce | Kopírovat | Kopírovat |
| Ctrl + přetažení | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Ctrl + přetažení | Zdroj | Zachová odkaz na původní položku. | Zachová odkaz na původní položku. |
| Ctrl + přetažení | Výsledek | `DROPEFFECT_COPY` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_COPY` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| CTRL + SHIFT + přetažení | | Bez zrušení | Bez zrušení |
| Vyjmout/vložit | Akce | Přesunout | Přesunout |
| Vyjmout/vložit | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Vyjmout/vložit | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Vyjmout/vložit | Výsledek | Položka zůstane v úložišti v původním umístění. | Položka se odstraní z původního umístění v úložišti. |
| Kopírovat/vložit | Akce | Kopírovat | Kopírovat |
| Kopírovat/vložit | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Kopírovat/vložit | Zdroj | Uchová původní položku. | Uchová původní položku. |
| Kopírovat/vložit | Výsledek | Položka zůstane v úložišti v původním umístění. | Položka zůstane v úložišti v původním umístění. |

#### <a name="mixed-target-projects"></a>Smíšené cílové projekty
Následující tabulka shrnuje operace přetahování (a také funkce vyjmout/kopírovat/vložit), které by se měly provádět na základě povaze zdrojové položky a modifikačních kláves pro projekty se smíšeným cílem:

| Modifikátor | Kategorie | Zdrojová položka: odkaz nebo odkaz | Zdrojová položka: fyzická položka nebo systém souborů ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Žádný modifikátor | Akce | Přesunout | Přesunout |
| Žádný modifikátor | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Žádný modifikátor | Zdroj | Odstraní odkaz na původní položku. | Odstraní odkaz na původní položku. |
| Žádný modifikátor | Výsledek | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka se odstraní z původního umístění v úložišti. |
| Shift + přetáhnout | Akce | Přesunout | Přesunout |
| Shift + přetáhnout | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Shift + přetáhnout | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Shift + přetáhnout | Výsledek | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka se odstraní z původního umístění v úložišti. |
| Ctrl + přetažení | Akce | Kopírovat | Kopírovat |
| Ctrl + přetažení | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Ctrl + přetažení | Zdroj | Zachová odkaz na původní položku. | Uchová původní položku. |
| Ctrl + přetažení | Výsledek | `DROPEFFECT_ COPY` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ COPY` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| CTRL + SHIFT + přetažení | Akce | Odkaz | Odkaz |
| CTRL + SHIFT + přetažení | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní zdrojovou položku. |
| CTRL + SHIFT + přetažení | Zdroj | Zachová odkaz na původní položku. | Uchová původní položku. |
| CTRL + SHIFT + přetažení | Výsledek | `DROPEFFECT_ LINK` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ LINK` se vrátí jako akce z `::Drop` a položka zůstane v původním umístění v úložišti. |
| Vyjmout/vložit | Akce | Přesunout | Přesunout |
| Vyjmout/vložit | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Vyjmout/vložit | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Vyjmout/vložit | Výsledek | Položka zůstane v úložišti v původním umístění. | Položka se odstraní z původního umístění v úložišti. |
| Kopírovat/vložit | Akce | Kopírovat | Kopírovat |
| Kopírovat/vložit | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Kopírovat/vložit | Zdroj | Uchová původní položku. | Uchová původní položku. |
| Kopírovat/vložit | Výsledek | Položka zůstane v úložišti v původním umístění. | Položka zůstane v úložišti v původním umístění. |

Tyto podrobnosti by se měly vzít v úvahu při provádění přetahování v **Průzkumník řešení**:

- Návrh pro více scénářů výběru.

- Názvy souborů (úplná cesta) musí být v rámci cílového projektu jedinečné, jinak nesmí být povoleno řazení.

- Názvy složek musí být jedinečné (bez rozlišení velkých a malých písmen) na úrovni, které jsou vyhozeny.

- Existují rozdíly v chování souborů, které jsou otevřeny nebo uzavřeny v době přetažení (ve scénářích výše nejsou zmíněny).

- Soubory nejvyšší úrovně se chovají mírně jinak než soubory ve složkách.

Dalším problémem, který je třeba znát, je zpracování operací přesunutí u položek, které mají otevřené návrháře nebo editory. Očekávané chování je následující (platí pro všechny typy projektů):

1. Pokud otevřený Editor nebo Návrhář neobsahuje žádné neuložené změny, okno editoru nebo návrháře by mělo být tiše zavřeno.

2. Pokud otevřený Editor nebo Návrhář obsahuje neuložené změny, pak by měl zdroj přetažení čekat na přetažení a potom požádat uživatele o uložení nepotvrzených změn v otevřených dokumentech před zavřením okna s výzvou, která bude vypadat přibližně takto:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Díky tomu může uživatel příležitost Uložit probíhající práci předtím, než cíl provede své kopie. Byla přidána nová metoda `IVsHierarchyDropDataSource2::OnBeforeDropNotify` pro povolení tohoto zpracování.

Cíl pak zkopíruje stav položky, protože je v úložišti (včetně neuložených změn v editoru, pokud uživatel nezvolil možnost **ne**). Jakmile cíl dokončí kopírování (v `IVsHierarchyDropDataSource::Drop` ), je zdroji dána možnost Dokončit část odstranění operace přesunu (v `IVsHierarchyDropDataSource::OnDropNotify` ).

Všechny editory s neuloženými změnami by měly být ponechány otevřené. U dokumentů s neuloženými změnami to znamená, že část kopírování operace přesunutí bude provedena, ale odstranění části bude přerušeno. Ve scénáři vícenásobného výběru, pokud uživatel zvolí hodnotu **ne**, nesmí být tyto dokumenty s neuloženými změnami uzavřeny ani odebrány, ale ty, které neobsahují neuložené změny, by se měly zavřít a odebrat.
