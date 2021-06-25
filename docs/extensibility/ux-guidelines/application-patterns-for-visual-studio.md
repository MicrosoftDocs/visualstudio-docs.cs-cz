---
title: Vzory aplikací pro Visual Studio | Microsoft Docs
description: Přečtěte si o rozdílech mezi okny dokumentu, okny nástrojů a nemodálními dialogy, včetně vzorců používání oken pro nové funkce sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2726c7096bbf4606fbab2c32b01ffd197549e13c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899183"
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
| **Model potvrzení** | *Zpožděné potvrzení*<br /><br /> Aby bylo možné data uložit v dokumentu, musí uživatel vydat příkaz **&gt; Uložit**, **Uložit jako** nebo **Uložit vše** . Okno dokumentu má koncept dat v rámci něj "změněných" a pak se potvrdí do jednoho z příkazů pro uložení. Při zavírání okna dokumentu se veškerý obsah buď uloží na disk, nebo se ztratí. | *Okamžité potvrzení*<br /><br /> Neexistuje žádný model uložení. Pro okna inspektora nástroje, která pomáhají při úpravách souboru, musí být soubor otevřen v aktivním editoru nebo Návrháři a editor nebo Návrhář vlastní uložení. | *Zpožděné nebo okamžité potvrzení*<br /><br /> Většinou velké dialogové okno s nemodálním dialogovým oknem vyžaduje akci potvrdit změny a umožňuje operaci zrušit, která vrátí všechny změny provedené v relaci dialogu.  To odlišuje nemodální dialogové okno z okna nástrojů v tom, že okna nástrojů mají vždy model okamžitého potvrzení. |
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

![Stavy oken nástrojů v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stavy oken nástrojů v aplikaci Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Jedna instance a více instancí
Okna nástrojů jsou buď jedna instance, nebo více instancí. Některá okna nástrojů s jednou instancí můžou být přidružená k aktivnímu oknu dokumentu, zatímco okna nástrojů s více instancemi ne. Okna nástrojů s více instancemi reagují na příkaz **Nové &gt; okno** okna vytvořením nové instance okna. Následující obrázek znázorňuje okno nástroje, které umožňuje příkaz New Window (Nové okno), když je instance okna aktivní:

![Okno nástroje, které umožňuje příkaz New Window (Nové okno), když je instance okna aktivní](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Okno nástroje, které umožňuje příkaz New Window (Nové okno), když je instance okna aktivní

Okna nástrojů s jednou instancí mohou být skrytá nebo zobrazená, zatímco okna nástrojů s více instancemi je možné zavřít i skrýt. Všechna okna nástrojů je možné ukotvit, propojit s kartami, plovoucí desetinnou čárkou nebo nastavit jako podřízené okno Multiple-Document Interface (MDI) (podobně jako okno dokumentu). Všechna okna nástrojů by měla reagovat na příslušné příkazy pro správu oken v nabídce Okna:

![Příkazy pro správu oken v nabídce Visual Studio Okna](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Příkazy pro správu oken v nabídce Visual Studio Okna

#### <a name="document-specific-tool-windows"></a>Okna nástrojů pro konkrétní dokumenty
Některá okna nástrojů jsou navržena ke změně na základě daného typu dokumentu. Tato okna se průběžně aktualizují, aby odrážela funkce, které platí pro aktivní okno dokumentu v integrovaném vývojovém prostředí.

Mezi příklady panelů nástrojů, jejichž obsah se mění tak, aby odrážel vybraný editor, patří panel nástrojů a osnova dokumentu. Tato okna zobrazují vodoznak, když má editor fokus, který nenabízí kontext okna.

#### <a name="navigable-list-tool-windows"></a>Okna nástrojů pro navigaci v seznamu
Některá okna nástrojů zobrazují seznam položek, se kterými uživatel může pracovat. V tomto typu okna by se měla vždy zobrazit zpětná vazba k aktuální položce v seznamu, i když je okno neaktivní. Seznam by měl reagovat na **příkazy GoToNextLocation** a **GoToPrevLocation** tím, že změní také aktuálně vybranou položku v okně.

Mezi příklady oken s nástroji seznam navigace patří Průzkumník řešení a Okno Najít výsledky.

### <a name="tool-window-types"></a>Typy oken nástrojů

#### <a name="common-tool-windows-and-their-functions"></a>Běžná okna nástrojů a jejich funkce

**Hierarchická okna nástrojů**

| Okno nástroje | Funkce |
| --- | --- |
| Průzkumník řešení | Hierarchický strom, který zobrazuje seznam dokumentů obsažených v projektech, různých souborech a položkách řešení. Zobrazení položek v projektech je definováno balíčkem, který vlastní typ projektu (například odkazové typy, typy založené na adresáři nebo smíšené režimy). |
| zobrazení tříd | Hierarchický strom tříd a různých prvků v pracovní sadě dokumentů, nezávisle na samotných souborech. |
| Průzkumník serveru | Hierarchický strom, který zobrazuje všechny servery a datová připojení v řešení. |
| Osnova dokumentu | Hierarchická struktura aktivního dokumentu. |

**Okna nástrojů mřížky**

| Okno nástroje | Funkce |
| --- | --- |
| Vlastnosti | Mřížka, která zobrazuje seznam vlastností vybraného objektu spolu s výběrem hodnot pro úpravy těchto vlastností. |
| Seznam úkolů | Mřížka, která uživateli umožňuje vytvářet, upravovat a odstraňovat úkoly a komentáře. |

**Okna nástrojů pro obsah**

| Okno nástroje | Funkce |
| --- | --- |
| Help | Okno, které uživatelům umožňuje přístup k různým metodám získání nápovědy z tématu "Jak mám?" na fóra MSDN. |
| Dynamická nápověda | Okno nástroje, které zobrazuje odkazy na témata nápovědy platná pro aktuální výběr. |
| prohlížeč objektů | Sada rámců se dvěma sloupci se seznamem komponent hierarchických objektů v levém podokně a vlastnostmi a metodami objektu v pravém sloupci. |

**Okna nástrojů dialogového okna**

| Okno nástroje | Funkce |
| --- | --- |
| Vyhledávání | Dialogové okno, které umožňuje uživateli vyhledat nebo nahradit v různých souborech v rámci řešení. |
| Rozšířené hledání | Dialogové okno, které umožňuje uživateli vyhledat nebo nahradit v různých souborech v rámci řešení. |

**Další okna nástrojů**

::: moniker range="vs-2017"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Okno nástroje slouží k ukládání prvků, které se přetahují na návrhové plochy, a poskytuje tak konzistentní zdroj přetažení pro všechny návrháře. |
| Úvodní stránka | Portál uživatele pro správu Visual Studio přístup k informačním kanálům novinek pro vývojáře, Visual Studio nápovědě a posledním projektům. Uživatelé mohou také vytvářet vlastní úvodní stránky zkopírováním souboru StartPage.xaml z adresáře souborů programu Common7\IDE\StartPage Visual Studio s do složky StartPages v adresáři dokumentů Visual Studio a pak buď ručně upravit XAML, nebo ho otevřít v Visual Studio nebo jiném editoru \" kódu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Okno nástroje slouží k ukládání prvků, které se přetahují na návrhové plochy, a poskytuje tak konzistentní zdroj přetažení pro všechny návrháře. |

::: moniker-end

**Okna nástrojů ladicího programu**

| Okno nástroje | Funkce |
| --- | --- |
| Auta ||
| Okamžité ||
| Výstup | Výstupní okno lze použít vždy, když máte textové události nebo stav, který chcete deklarovat. |
| Memory (Paměť) ||
| Zarážky ||
| Spuštěno ||
| dokumenty. ||
| Zásobník volání ||
| Místní obyvatelé ||
| Hodinky ||
| Demontáž ||
| Registruje ||
| Vlákna ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a> Konvence editoru dokumentů

### <a name="document-interactions"></a>Interakce dokumentů
"Dobře dokument" je největší prostor v rámci integrovaného vývojového prostředí a je to místo, kde se uživatel obecně zaměřil na plnění svých úkolů s asistencí doplňkových oken nástrojů. Editory dokumentů představují základní jednotky práce, které uživatel otevře a uloží do Visual Studio. Zachovávají si silný smysl pro výběr spojený s Průzkumník řešení nebo jinými aktivními okny hierarchie. Uživatel by měl být schopný odkazovat na jedno z těchto oken hierarchie a vědět, kde je dokument obsažen a jeho vztah k řešení, projektu nebo jinému kořenovému objektu poskytnutému balíčkem Visual Studio.

Úpravy dokumentů vyžadují konzistentní uživatelské prostředí. Pokud chcete uživateli umožnit, aby se místo na správu oken a hledání příkazů soustředil na úlohu, vyberte strategii zobrazení dokumentu, která nejlépe odpovídá uživatelským úlohám pro úpravy tohoto typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Běžné interakce pro dobře dokument

- Udržujte konzistentní model interakce ve společných **prostředích Nový soubor** a **Otevřít** soubor.

- Aktualizujte související funkce v souvisejících oknech a nabídkách při otevření okna dokumentu.

- Příkazy nabídky jsou vhodně integrované do běžných nabídek, jako jsou **nabídky Upravit,** **Formát** **a** Zobrazit. Pokud jsou k dispozici podstatné množství specializovaných příkazů, lze vytvořit novou nabídku. Tato nová nabídka by měla být viditelná pouze v případě, že dokument má fokus.

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

![ Příkladem jednoduchého dialogového okna v aplikaci Visual Studio je>vytvořit klíč se silným názvem.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Vytvoření klíče se silným názvem je příkladem jednoduchého dialogového okna v aplikaci Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a> Vrstvená dialogová okna
Vrstvená dialogová okna zahrnují karty, řídicí panely a vložené stromy. Používají se k maximalizaci skutečné nemovitosti, pokud je v jedné části uživatelského rozhraní nabídnuto více skupin ovládacích prvků. Seskupení jsou vrstvená tak, aby si uživatel mohl kdykoli zobrazit.

V nejjednodušším případě je mechanismus pro přepínání mezi seskupeními ovládací prvek karta. K dispozici je několik alternativ. Jak zvolit nejvhodnější styl, najdete v tématu určení priorit a vrstvení.

Dialogové **okno &gt; Možnosti nástrojů** je příkladem vrstveného dialogového okna s vloženým stromem:

![Nástroje > možnosti jsou příkladem vrstveného dialogového okna v aplikaci Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Nástroje > možnosti jsou příkladem vrstveného dialogového okna v aplikaci Visual Studio.

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

  ![Specifikace zásad pro záhlaví v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specifikace zásad pro záhlaví v dialogových oknech sady Visual Studio

#### <a name="control-buttons"></a>Řídicí tlačítka
V pravém dolním rohu dialogového okna by se měla zobrazovat tlačítka v oblasti Obecné, **OK**, **Zrušit** a **pomáhat** vodorovně. Alternativní vertikální zásobník je povolený, pokud dialogové okno obsahuje několik dalších tlačítek v dolní části dialogového okna, které by představovalo vizuální nejasnost s ovládacími tlačítky.

![Přijatelné konfigurace pro řídicí tlačítka v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Přijatelné konfigurace pro řídicí tlačítka v dialogových oknech sady Visual Studio

Dialogové okno musí obsahovat výchozí ovládací tlačítko. Pokud chcete určit nejvhodnější příkaz, který se má použít jako výchozí, vyberte jednu z následujících možností (v pořadí podle priority):

- Jako výchozí vyberte nejbezpečnější a nejbezpečnější příkaz. To znamená, že volba příkazu pravděpodobně brání ztrátě dat a vyhne se neúmyslnému přístupu k systému.

- Pokud ztráta dat a zabezpečení nejsou faktory, zvolte výchozí příkaz založený na pohodlí. Zahrnutí nejpravděpodobnějšího příkazu jako výchozího bude zlepšit pracovní postup uživatele v případě, že dialog podporuje časté nebo opakované úkoly.

Nevybírejte pro výchozí příkaz trvale destruktivní akci. Pokud je takový příkaz k dispozici, vyberte místo toho bezpečnější příkaz jako výchozí.

#### <a name="access-keys"></a>Přístupové klíče
Nepoužívejte přístupové klávesy pro tlačítka **OK**, **Zrušit** nebo **pomáhat** . Ve výchozím nastavení jsou tato tlačítka namapována na klávesové zkratky:

| Název tlačítka | Klávesová zkratka |
| --- | --- |
| OK | Enter |
| Zrušit | Esc |
| Help | F1 |

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
| Ovládací prvek karta | Seskupení dialogových stránek logické skupiny do souvisejících sad<br /><br />Užitečné pro méně než pět (nebo počet karet, které odpovídají jednomu řádku v rámci dialogového okna) stránky souvisejících ovládacích prvků v dialogovém okně<br /><br />Popisky karet musí být krátké: jedno nebo dvě slova, která snadno identifikují obsah.<br /><br />Běžný styl dialogového okna systému<br /><br />Příklad: **Průzkumník souborů &gt; položky** | Vytváření popisných krátkých popisků může být obtížné<br /><br />Obecně se v jednom dialogovém okně nesnídí posledních pět karet<br /><br />Nevhodný, pokud máte příliš mnoho karet pro jeden řádek (použijte alternativní techniku vrstvení).<br /><br />Není rozšiřitelné |
| Navigace na bočním panelu | Jednoduché přepínací zařízení, které může pojmout více kategorií než karet<br /><br />Plochý seznam kategorií (bez hierarchie)<br /><br />Extensible<br /><br />Příklad: **Přizpůsobit... &gt; Přidat příkaz** | Není vhodné použít vodorovný prostor, pokud existuje méně než tři skupiny.<br /><br />Úloha může být pro rozevírací seznam lepší. |
| Stromový ovládací prvek | Umožňuje neomezené kategorie.<br /><br />Umožňuje seskupování nebo hierarchii kategorií.<br /><br />Extensible<br /><br />Příklad: **Možnosti &gt; nástrojů** | Velmi vnořené hierarchie mohou způsobit nadměrné vodorovné posouvání.<br /><br />Visual Studio zobrazení stromové struktury překysáhuje. |
| Průvodce | Pomáhá s dokončením úkolu tím, že uživatele provede sekvenčními kroky založenými na úkolech: průvodce představuje úkol vysoké úrovně a jednotlivé panely představují dílčí úkoly potřebné k provedení celkového úkolu.<br /><br />Užitečné, když úloha překročí hranice uživatelského rozhraní, jako by uživatel jinak k dokončení úlohy muset použít více editorů a oken nástrojů.<br /><br />Užitečné, když úloha vyžaduje větvení<br /><br />Užitečné, když úloha obsahuje závislosti mezi kroky<br /><br />Užitečné, když se v jednom dialogovém okně může zobrazit několik podobných úloh s jedním rozhodovacím forkem, aby se snížil počet různých podobných dialogů. | Nevhodný pro všechny úlohy, které nevyžadují sekvenční pracovní postup<br /><br />Průvodce může uživatele zahltit a zaměnit s příliš mnoha kroky.<br /><br />Průvodci mají ze své podstaty omezenou prostorovou obrazovku. |

##### <a name="hallways-or-dashboards"></a>Neschůdné nebo řídicí panely
Řídicí panely a dialogy jsou dialogy nebo panely, které slouží jako spouštěcí body pro další dialogy a okna. Dobře navržené "podchycené" okamžitě zdůlechťují pouze nejběžnější možnosti, příkazy a nastavení, což uživateli umožňuje snadno provádět běžné úlohy. Podobně jako v reálném světě poskytuje dveře pro přístup k místnostem za nimi, zde se méně běžné uživatelské rozhraní shromažďuje do samostatných "místností" (často i dalších dialogů) souvisejících funkcí, ke kterým lze přistupovat z hlavního zařízení.

Případně uživatelské rozhraní, které nabízí všechny dostupné funkce v jedné kolekci, místo refaktoringu méně běžných funkcí do samostatných umístění, je jednoduše řídicí panel.

![Koncept odhalení dalšího uživatelského rozhraní v Outlooku](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Koncept odhalení dalšího uživatelského rozhraní v Outlooku

##### <a name="adaptive-ui"></a>Adaptivní uživatelské rozhraní
Zobrazení nebo skrytí uživatelského rozhraní na základě využití nebo uživatelského prostředí hlášené uživatelem je další způsob, jak prezentovat nezbytné uživatelské rozhraní a současně skrýt další části. To se nedoporučuje v Visual Studio, protože algoritmy pro rozhodování o tom, kdy zobrazit nebo skrýt uživatelské rozhraní, mohou být složité a pravidla budou v některých případech vždy chybná.

## <a name="projects"></a><a name="BKMK_Projects"></a> Projekty

### <a name="projects-in-the-solution-explorer"></a>Projekty v Průzkumník řešení
Většina projektů je klasifikovaná jako odkazová, adresářová nebo smíšená. Všechny tři typy projektů jsou podporovány současně v Průzkumník řešení. Kořen uživatelského prostředí při práci s projekty se odehrá v tomto okně. Přestože různé uzly projektu jsou projekty typu odkaz, adresář nebo smíšený režim, existuje běžný vzor interakce, který by se měl použít jako výchozí bod před tím, než se rozchýlete do vzorů uživatelů specifických pro konkrétní projekt.

Projekty by měly vždy:

- Podpora možnosti přidávat složky projektu pro uspořádání obsahu projektu

- Zachování konzistentního modelu pro trvalost projektu

Projekty by také měly udržovat konzistentní modely interakce pro:

- Odebrání položek projektu

- Ukládání dokumentů

- Úpravy vlastností projektu

- Úprava projektu v alternativním zobrazení

- Operace přetažení

### <a name="drag-and-drop-interaction-model"></a>Model interakce s přetahováním
Projekty se obvykle klasifikují jako odkazové (jsou schopné zachovat pouze odkazy na položky projektu v úložišti), adresářové (schopné zachovat pouze položky projektu fyzicky uložené v rámci hierarchie projektu) nebo smíšené (schopné zachovat odkazy nebo fyzické položky). Integrované vývojové prostředí (IDE) umožňuje současně jmout všechny tři typy **projektů Průzkumník řešení**.

Z hlediska přetahování myší by se měly na každý typ projektu v rámci projektu v rámci Průzkumník řešení **:**

- **Projekt založený na odkazech:** Klíčovým bodem je, že projekt přetahují odkaz na položku v úložišti. Pokud projekt založený na odkazech funguje jako zdroj pro operaci přesunutí, měl by z projektu odebrat pouze odkaz na položku. Položka by se ve skutečnosti neměla odstranit z pevného disku. Když projekt založený na odkazech funguje jako cíl operace přesunutí (nebo kopírování), měl by přidat odkaz na původní zdrojovou položku bez vytvoření privátní kopie položky.

- **Projekt založený na adresáři:** Z pohledu přetahováním přetáhne projekt fyzickou položku místo odkazu. Když projekt založený na adresáři funguje jako zdroj pro operaci přesunutí, měl by nakonec odstranit fyzickou položku z pevného disku a odebrat ji z projektu. Když projekt založený na adresáři funguje jako cíl pro operaci přesunutí (nebo kopírování), měl by vytvořit kopii zdrojové položky v cílovém umístění.

- **Projekt se smíšenými cíli:** Z hlediska přetažení je chování tohoto typu projektu založené na povaze přetahované položky (buď odkaz na položku v úložišti, nebo na samotnou položku). Správné chování odkazů a fyzických položek je popsáno výše.

Pokud by v projektu byl jen jeden **Průzkumník řešení**, byly by operace přetažení jednoduché. Vzhledem k tomu, že každý projektový systém má schopnost definovat vlastní chování při přetahování myší, měly by se dodržovat určité pokyny (na základě chování přetahování myší v systému Průzkumník Windows), které zajistí předvídatelné uživatelské prostředí:

- Neupravená operace přetažení v **Průzkumník řešení** (když nejsou stisknuté klávesy Ctrl ani Shift), by měla mít za následek operaci přesunutí.

- Operace posunutím myší by měla také vést k operaci přesunutí.

- Operace ctrl+přetažení by měla vést k operaci kopírování.

- Systémy referenčních a smíšených projektů podporují vazbu (nebo odkaz) na zdrojovou položku. Pokud jsou tyto projekty cílem operace přetažení (když je stisknutou klávesu **Ctrl + Shift),** měla by výsledkem přidání odkazu na položku do projektu.

Ne všechny operace přetažení myší jsou rozumné napříč kombinacemi referenčních, adresářových a smíšených projektů. Konkrétně je problematické vydávat se, že je možné povolit operaci přesunu mezi zdrojovým projektem založeným na adresáři a cílovým projektem založeným na odkazech, protože projekt založený na zdrojovém adresáři bude muset po dokončení přesunu odstranit zdrojovou položku. Cílový projekt založený na odkazech by pak skončil s odkazem na odstraněnou položku.

Je také zavádějící vydávat, že se povolí operace kopírování mezi těmito typy projektů, protože cílový projekt založený na odkazech by neměl vytvořit nezávislou kopii zdrojové položky. Podobně by nemělo být povolené přetahování kláves Ctrl +Shift do cílového projektu založeného na adresáři, protože projekt založený na adresáři nedokáže zachovat odkazy. V případech, kdy není operace přetažení podporována, by integrované vývojové prostředí (IDE) mělo zakázat přetažení a zobrazit uživateli kurzor bez přetažení (viz tabulka ukazatelů níže).

Pokud chcete správně implementovat chování přetažení, musí zdrojový projekt přetažení sdělit svou povahu cílovému projektu. (Je to například odkaz nebo adresář?) Tyto informace jsou označeny formátem schránky, který nabízí zdroj. Jako zdroj operace přetažení (nebo kopírování schránky) by projekt měl nabízet buď nebo , v závislosti na tom, jestli je projekt založený na odkazech nebo `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` na adresáři. Oba tyto formáty mají stejný datový obsah, který se podobá formátu Windows s tím rozdílem, že seznamy řetězců místo názvů souborů jsou seznamem řetězců s dvojitou ukončenou hodnotou (podle potřeby vrácených z řetězce nebo `CF_HDROP` `NULL` `Projref` `IVsSolution::GetProjrefOfItem` `::GetProjrefOfProject` ).

Jako cíl operace přetažení (nebo vložení schránky) by projekt měl přijmout i , i když přesné zpracování operace přetažení se liší v závislosti na povaze cílového projektu a `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` zdrojového projektu. Zdrojový projekt deklaruje svou povahu podle toho, jestli nabízí `CF_VSREFPROJECTITEMS` nebo `CF_VSSTGPROJECTITEMS` . Cíl poklesu rozumí své vlastní povaze, a proto má dostatek informací k rozhodování o tom, jestli se má provést přesun, kopírování nebo propojení. Uživatel také upraví, která operace přetažení se má provést stisknutím kláves Ctrl, Shift nebo Ctrl a Shift. Je důležité, aby cíl odstranění správně indikoval, která operace se provede předem ve svých metodách `DragEnter` `DragOver` a . Aplikace **Průzkumník řešení** automaticky ví, jestli je zdrojový a cílový projekt stejný.

Přetažení položek projektu mezi instancemi Visual Studio (například z jedné instance devenv.exe do jiné) není podporováno. Tento **Průzkumník řešení** také přímo zakáže.

Uživatel by měl vždy být schopný určit účinek operace přetažení myší tak, že položku vybere, přetáhne ji do cílového umístění a zjistí, který z následujících ukazatelů myši se zobrazí před vyřazením položky:

| Ukazatel myši | Příkaz | Popis |
| :---: | --- | --- |
| ![Ikona "bez poklesu" myši](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Bez poklesu | Položku nelze vyřazení do zadaného umístění. |
| ![Ikona kopírování myší](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopírovat | Položka se zkopíruje do cílového umístění. |
| ![Ikona "přesunutí" myši](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Přesunout | Položka se přesune do cílového umístění. |
| ![Ikona Přidat odkaz myší](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Přidání odkazu | Do cílového umístění se přidá odkaz na vybranou položku. |

#### <a name="reference-based-projects"></a>Projekty založené na odkazech
 Následující tabulka shrnuje operace přetažení (a také operace vyjmutí/kopírování/vložení), které by se měly provést na základě povahy zdrojové položky a modifikačních kláves stisknutých pro odkazované cílové projekty:

| Modifikátor | Kategorie | Zdrojová položka: Odkaz/odkaz | Zdrojová položka: Fyzická položka nebo systém souborů ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Žádný modifikátor | Akce | Přesunout | Odkaz |
| Žádný modifikátor | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Žádný modifikátor | Zdroj | Odstraní odkaz na původní položku. | Zachová původní položku. |
| Žádný modifikátor | Výsledek | `DROPEFFECT_MOVE` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_LINK` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. |
| Shift + přetažení | Akce | Přesunout | Bez poklesu |
| Shift + přetažení | Cíl | Přidá odkaz na původní položku. | Bez poklesu |
| Shift + přetažení | Zdroj | Odstraní odkaz na původní položku. | Bez poklesu |
| Shift + přetažení | Výsledek | `DROPEFFECT_MOVE` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | Bez poklesu |
| Ctrl + přetažení | Akce | Kopírovat | Bez poklesu |
| Ctrl + přetažení | Cíl | Přidá odkaz na původní položku. | Bez poklesu |
| Ctrl + přetažení | Zdroj | Zachová odkaz na původní položku. | Bez poklesu |
| Ctrl + přetažení | Výsledek | `DROPEFFECT_COPY` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | Bez poklesu |
| Ctrl + Shift + přetažení | Akce | Odkaz | Odkaz |
| Ctrl + Shift + přetažení | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Ctrl + Shift + přetažení | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl + Shift + přetažení | Výsledek | `DROPEFFECT_LINK` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_LINK` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. |
| Ctrl + Shift + přetažení | Poznámka | Stejné jako chování při přetahování u zkratek v Průzkumník Windows. ||
| Vyjmutí a vložení | Akce | Přesunout | Odkaz |
| Vyjmutí a vložení | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Vyjmutí a vložení | Zdroj | Zachová odkaz na původní položku.|Zachová původní položku. |
| Vyjmutí a vložení | Výsledek | Položka zůstane v původním umístění v úložišti. | Položka zůstane v původním umístění v úložišti. |
| Kopírování a vkládání | Akce | Kopírovat | Odkaz |
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
Následující tabulka shrnuje operace přetažení (a také operace vyjmutí/kopírování/vložení), které by se měly provést na základě povahy zdrojové položky a modifikačních kláves stisknutých pro projekty se smíšenými cíli:

| Modifikátor | Kategorie | Zdrojová položka: Odkaz/odkaz | Zdrojová položka: Fyzická položka nebo systém souborů ( `CF_HDROP` ) |
| --- | --- | --- | --- |
| Bez modifikátoru | Akce | Přesunout | Přesunout |
| Bez modifikátoru | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Bez modifikátoru | Zdroj | Odstraní odkaz na původní položku. | Odstraní odkaz na původní položku. |
| Bez modifikátoru | Výsledek | `DROPEFFECT_ MOVE` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka se odstraní z původního umístění v úložišti. |
| Shift + přetažení | Akce | Přesunout | Přesunout |
| Shift + přetažení | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Shift + přetažení | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Shift + přetažení | Výsledek | `DROPEFFECT_ MOVE` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ MOVE` se vrátí jako akce z `::Drop` a položka se odstraní z původního umístění v úložišti. |
| Ctrl + přetažení | Akce | Kopírovat | Kopírovat |
| Ctrl + přetažení | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Ctrl + přetažení | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl + přetažení | Výsledek | `DROPEFFECT_ COPY` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ COPY` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. |
| Ctrl + Shift + přetažení | Akce | Odkaz | Odkaz |
| Ctrl + Shift + přetažení | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní zdrojovou položku. |
| Ctrl + Shift + přetažení | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl + Shift + přetažení | Výsledek | `DROPEFFECT_ LINK` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. | `DROPEFFECT_ LINK` se vrátí jako akce z a `::Drop` položka zůstane v původním umístění v úložišti. |
| Vyjmutí a vložení | Akce | Přesunout | Přesunout |
| Vyjmutí a vložení | Cíl | Zkopíruje položku do cílového umístění. | Zkopíruje položku do cílového umístění. |
| Vyjmutí a vložení | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Vyjmutí a vložení | Výsledek | Položka zůstane v původním umístění v úložišti. | Položka se odstraní z původního umístění v úložišti. |
| Kopírování a vkládání | Akce | Kopírovat | Kopírovat |
| Kopírování a vkládání | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění. |
| Kopírování a vkládání | Zdroj | Zachová původní položku. | Zachová původní položku. |
| Kopírování a vkládání | Výsledek | Položka zůstane v původním umístění v úložišti. | Položka zůstane v původním umístění v úložišti. |

Tyto podrobnosti byste měli vzít v úvahu při implementaci přetažení do **Průzkumník řešení**:

- Návrh pro různé scénáře výběru

- Názvy souborů (úplná cesta) musí být v rámci cílového projektu jedinečné, jinak by neměl být povolený pokles.

- Názvy složek musí být jedinečné (bez rozlišení velkých a malých písmen) na úrovni, na které se zahodí.

- Mezi soubory, které jsou při přetažení otevřené nebo uzavřené, existují rozdíly v chování (není to uvedeno ve scénářích výše).

- Soubory nejvyšší úrovně se chovají trochu jinak než soubory ve složkách.

Dalším problémem, o kterém byste měli vědět, je způsob zpracování operací přesunu u položek, které mají otevřené návrháře nebo editory. Očekávané chování je následující (platí pro všechny typy projektů):

1. Pokud otevřený editor/návrhář nemá žádné neuložené změny, mělo by se okno editoru nebo návrháře bezobslužně zavřít.

2. Pokud otevřený editor nebo návrhář obsahuje neuložené změny, měl by zdroj přetažení počkat, než dojde k poklesu, a potom požádat uživatele, aby nepotrzené změny v otevřených dokumentech uložit před zavřením okna s výzvou podobnou této:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

Díky tomu může uživatel uložit práci v průběhu ještě před tím, než cíl vytvoří kopie. Byla přidána `IVsHierarchyDropDataSource2::OnBeforeDropNotify` nová metoda, která toto zpracování povolí.

Cíl pak zkopíruje stav položky tak, jak je v úložišti (bez neuložené změny v editoru, pokud uživatel zvolil **Ne).** Po dokončení kopírování cíle (v souboru ) má zdroj možnost dokončit část operace `IVsHierarchyDropDataSource::Drop` přesunu odstranění (v souboru `IVsHierarchyDropDataSource::OnDropNotify` ).

Všechny editory s neuloženou změnou by měly být otevřené. U dokumentů s neuloženou změnou to znamená, že se provede část operace přesunutí kopírování, ale část odstranění se přeruší. Ve scénáři s vícenásobným výběrem, když uživatel zvolí **Ne,** by se dokumenty s neuloženým změnami neměly zavřít ani odebrat, ale ty, které nemají neuložené změny, by se měly zavřít a odebrat.
