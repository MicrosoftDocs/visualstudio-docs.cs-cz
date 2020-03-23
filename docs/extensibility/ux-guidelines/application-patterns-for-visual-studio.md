---
title: Vzory aplikací pro sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55044df3898b452e87ec877f9ae10dd12a2b1110
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303188"
---
# <a name="application-patterns-for-visual-studio"></a>Vzory aplikací pro Visual Studio
## <a name="window-interactions"></a><a name="BKMK_WindowInteractions"></a>Interakce s okny

### <a name="overview"></a>Přehled
Dva typy hlavních oken používané v sadě Visual Studio jsou editory dokumentů a okna nástrojů. Vzácné, ale možné, jsou velké nemodální dialogy. I když jsou všechny nemodalené ve skořápce, jejich vzory jsou zásadně odlišné. Tato část popisuje rozdíl mezi okny dokumentu, okny nástrojů a nemodálními dialogy. Modální dialogová vzory jsou popsány v [dialogech](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porovnání vzorců využití oken
**Okna dokumentu** jsou téměř vždy zobrazena v dokumentu dobře. To dává editoru dokumentů "středjeviště" uspořádat doplňující okna nástrojů kolem.

**Okno nástroje** se nejčastěji zobrazuje jako samostatné, menší okno sbalené proti okraji ide. To může být viditelné, skryté nebo automaticky skryté. Někdy však okna nástrojů jsou prezentovány v rámci dokumentu dobře, zrušením zaškrtnutí **Window/Docking** vlastnost v okně. Výsledkem je více nemovitostí, ale také společné rozhodnutí o návrhu: při pokusu o integraci do sady Visual Studio se musíte rozhodnout, zda má funkce zobrazit okno nástroje nebo okno dokumentu.

**Moderování dialogových oken** se nedoporučuje v sadě Visual Studio. Většina nemodálnídialogová okna jsou, podle definice, plovoucí okna nástrojů a měly by být implementovány tímto způsobem. Nemodální dialogová okna jsou povolena v případech, kdy by velikost normálního okna nástroje ukotvená na straně skořepiny byla příliš omezující. Jsou také povoleny v případech, kdy by uživatel pravděpodobně přesunul dialogové okno na sekundární monitor.

Pečlivě si rozmyslete, jaký typ kontejneru potřebujete. Běžné aspekty vzor použití pro návrh ui jsou v následující tabulce.

||Okno dokumentu|Okno nástroje|Nemodální dialog|
|-|---------------------|-----------------|---------------------|
| **Pozici** | Vždy umístěn v rámci dokumentu dobře a není ukotvení kolem okrajů ide. Může být "vytažen" tak, aby plaval odděleně od hlavního pláště. | Obvykle tabulátor ukotvené kolem okrajů ide, ale lze přizpůsobit plovoucí, automaticky skryté (unpinned), nebo ukotvené v rámci dokumentu dobře.|Velké plovoucí okno oddělené od ide. |
| **Model potvrzení** | *Zpožděné potvrzení*<br /><br /> Chcete-li uložit data do dokumentu, musí uživatel vydat příkaz **Uložit soubor &gt; **, Uložit **jako**nebo **Uložit vše.** Okno dokumentu má koncept dat v něm je "dirtied" pak potvrzena jeden z uložit příkazy. Při zavírání okna dokumentu se veškerý obsah uloží na disk nebo se ztratí. | *Okamžité potvrzení*<br /><br /> Neexistuje žádný model uložení. Pro okna nástrojů inspektora, která pomáhají při úpravách souboru, musí být soubor otevřen v aktivním editoru nebo návrháři a editor nebo návrhář vlastní uložení. | *Zpožděné nebo okamžité potvrzení*<br /><br /> Nejčastěji velké nemodální dialogové okno vyžaduje akci k potvrzení změn a umožňuje operaci "Zrušit", která vrátí zpět všechny změny provedené v rámci relace dialogového okna.  Tím se odliší nemodální dialog od okna nástroje v tomto okně nástroje, které má vždy model okamžitého potvrzení. |
| **Viditelnost** | *Otevřít/vytvořit (soubor) a Zavřít*<br /><br /> Otevření oken dokumentu se provádí buď otevřením existujícího dokumentu, nebo použitím šablony k vytvoření nového dokumentu. Neexistuje žádný příkaz \<"Otevřít konkrétní editor>". | *Skrýt a zobrazit*<br /><br /> Okna nástrojů s jednou instancí mohou být skryta nebo zobrazena. Obsah a stavy v okně nástroje přetrvávají, ať už v zobrazení nebo skryté. Okna nástrojů pro více instancí lze uzavřít i skrýt. Když je okno nástroje s více instancemi zavřené, obsah a stav v okně nástroje se zahodí. | *Spuštěno z příkazu*<br /><br /> Dialogová okna jsou spouštěna z příkazu založeného na úlohách. |
| **Instance** | *Více instancí*<br /><br /> Několik editorů může být otevřeno současně a upravovat různé soubory, zatímco některé editory také umožňují, aby byl stejný soubor otevřen ve více než jednom editoru (pomocí příkazu **Window &gt; New Window).**<br /><br /> Jeden editor může upravovat jeden nebo více souborů současně (Návrhář projektu). | *Jedna nebo více instancí*<br /><br /> Obsah se změní tak, aby odrážel kontext (jako v prohlížeči vlastností) nebo zasunul fokus/kontext do jiných oken (Seznam úloh, Průzkumník řešení).<br /><br /> Okna nástrojů pro jednu i více instancí by měla být přidružena k aktivnímu oknu dokumentu, pokud k tomu neexistuje závažný důvod. | *Jedna instance* |
| **Příklady** | **Textové editory**, jako je editor kódu<br /><br /> **Návrh povrchů**, jako je návrhář formulářů nebo modelovací povrch<br /><br /> **Rozložení ovládacích tlačítek podobná dialogům**, například Návrhář manifestu | **Průzkumník řešení** poskytuje řešení a projekty obsažené v řešení<br /><br /> **Průzkumník serveru** poskytuje hierarchické zobrazení serverů a datových připojení, které se uživatel rozhodne otevřít v okně. Otevření objektu z hierarchie databáze, například dotazu, otevře okno dokumentu a umožní uživateli upravit dotaz.<br /><br /> **Prohlížeč vlastností** zobrazuje vlastnosti objektu vybraného buď v okně dokumentu, nebo v jiném okně nástroje. Vlastnosti jsou zobrazeny buď v hierarchickém zobrazení mřížky nebo ve složitých ovládacích prvcích podobných dialogu a umožňují uživateli nastavit hodnoty pro tyto vlastnosti. | |

## <a name="tool-windows"></a><a name="BKMK_ToolWindows"></a>Okna nástrojů

### <a name="overview"></a>Přehled
Okna nástrojů podporují práci uživatele, ke které dochází v oknech dokumentu. Lze je použít k zobrazení hierarchie, která představuje základní kořenový objekt, který visual studio poskytuje a může manipulovat.

Při zvažování nové okno nástroje v ide, autoři by měli:

- Používejte existující okna nástrojů odpovídající úlohám a nevytvářejte nová s podobnými funkcemi. Nová okna nástrojů by měla být vytvořena pouze v případě, že nabízejí výrazně odlišný "nástroj" nebo funkce, které nelze integrovat do podobného okna, nebo otočením existujícího okna na otočný rozbočovač.

- V případě potřeby použijte standardní panel příkazů v horní části okna nástroje.

- Buďte konzistentní se vzorky, které jsou již k dispozici v jiných oknech nástrojů pro ovládání prezentace a navigace pomocí klávesnice.

- Buďte konzistentní s ovládacím prvkem prezentace v jiných oknech nástrojů.

- Pokud je to možné, zviditelněte okna nástrojů specifických pro dokument tak, aby se zobrazila pouze při aktivaci nadřazeného dokumentu.

- Ujistěte se, že jejich obsah okna je splavný pomocí klávesnice (podpora kláves se šipkami).

#### <a name="tool-window-states"></a>Stavy oken nástroje
Okna nástrojů sady Visual Studio mají různé stavy, z nichž některé jsou aktivovány uživatelem (například funkce automatického skrytí). Jiné stavy, například automaticky viditelné, umožňují, aby se okna nástrojů zobrazovala ve správném kontextu a skryla se, když je to potřeba. Existuje celkem pět stavů oken nástrojů.

- **Ukotvená/připnutá** okna nástrojů lze připojit k libovolné ze čtyř stran oblasti dokumentu. V záhlaví okna nástroje se zobrazí ikona připínáčku. Okno nástroje lze ukotvit vodorovně nebo svisle podél okraje skořepiny a dalších oken nástrojů a může být také propojeno tabulátory.

- **Automaticky skrytá** okna nástrojů jsou odepnutá. Okno může sklouznout z dohledu a nechat kartu (s názvem okna nástroje a jeho ikonou) na okraji oblasti dokumentu. Okno nástroje se vysune, když uživatel najedou na kartu.

- **Automaticky viditelná** okna nástrojů se automaticky zobrazí, když je spuštěna jiná část ui, jako je editor, nebo získá fokus.

- **Plovoucí** okna nástrojů najedou mimo prostředí IDE. To je užitečné pro konfigurace s více monitory.

- Okna **nástrojů pro dokumenty s kartami** lze dobře ukotvit v dokumentu. To je užitečné pro velká okna nástrojů, jako je prohlížeč objektů, které potřebují více nemovitostí, než dokování k okrajům rámečku umožňuje.

![Stavy oken nástrojů v sadě Visual Studio](../../extensibility/ux-guidelines/media/0702-01_toolwindowstates.png "0702-01_ToolWindowStates")<br />Stavy oken nástrojů v sadě Visual Studio

#### <a name="single-instance-and-multi-instance"></a>Jedna instance a více instancí
Okna nástrojů jsou buď jednoinstancí, nebo víceindicí. Některá okna nástrojů s jednou instancí mohou být přidružena k aktivnímu oknu dokumentu, zatímco okna nástrojů pro více instancí nemusí. Okna nástrojů pro více instancí reagují na příkaz **Window &gt; New Window** vytvořením nové instance okna. Následující obrázek znázorňuje okno nástroje, které umožňuje příkaz Nové okno, když je aktivní instance okna:

![Okno nástroje umožňující příkaz Nové okno, když je aktivní instance okna](../../extensibility/ux-guidelines/media/0702-02_toolwindowenablingcommand.png "0702-02_ToolWindowEnablingCommand")<br />Okno nástroje umožňující příkaz Nové okno, když je aktivní instance okna

Okna nástrojů s jednou instancí mohou být skryta nebo zobrazena, zatímco okna nástrojů pro více instancí mohou být uzavřena i skryta. Všechna okna nástrojů lze ukotvit, propojit tabulátory, plovoucí nebo nastavit jako podřízené okno rozhraní MDI (Multiple-Document Interface) (podobně jako okno dokumentu). Všechna okna nástrojů by měla reagovat na příslušné příkazy správy oken v nabídce Okno:

![Příkazy pro správu oken v nabídce Okno sady Visual Studio](../../extensibility/ux-guidelines/media/0702-03_windowmanagementcontrols.png "0702-03_WindowManagementControls")<br />Příkazy pro správu oken v nabídce Okno sady Visual Studio

#### <a name="document-specific-tool-windows"></a>Okna nástrojů specifických pro dokument
Některá okna nástrojů jsou navržena tak, aby se měnila na základě daného typu dokumentu. Tato okna se průběžně aktualizují tak, aby odrážela funkce platné pro okno aktivního dokumentu v prostředí IDE.

Příklady oken nástrojů, jejichž obsah se mění tak, aby odrážel vybraný editor, jsou Panel nástrojů a Osnova dokumentu. Tato okna zobrazit vodoznak, když editor má fokus, který nenabízí kontext okna.

#### <a name="navigable-list-tool-windows"></a>Okna nástrojů pro splavný seznam
Některá okna nástrojů zobrazují seznam splavných položek, se kterými může uživatel pracovat. V tomto typu okna by měla být vždy zpětná vazba pro aktuální položku v seznamu, i v případě, že okno je neaktivní. Seznam by měl reagovat na příkazy **GoToNextLocation** a **GoToPrevLocation** také změnou aktuálně vybrané položky v okně

Příklady splavných oken nástrojů seznamu jsou Průzkumník řešení a okno Najít výsledky.

### <a name="tool-window-types"></a>Typy oken nástrojů

#### <a name="common-tool-windows-and-their-functions"></a>Běžná okna nástrojů a jejich funkce

**Hierarchická okna nástrojů**

| Okno nástroje | Funkce |
| --- | --- |
| Průzkumník řešení | Hierarchický strom, který zobrazuje seznam dokumentů obsažených v projektech, různé soubory a položky řešení. Zobrazení položek v rámci projektů je definováno balíčkem, který vlastní typ projektu (například na základě odkazu, na základě adresáře nebo smíšený režim typy). |
| zobrazení tříd | Hierarchický strom tříd a různých prvků v pracovní sadě dokumentů, nezávisle na samotných souborech. |
| Průzkumník serveru | Hierarchický strom, který zobrazuje všechny servery a datová připojení v řešení. |
| Osnova dokumentu | Hierarchická struktura aktivního dokumentu. |

**Okna nástroje Mřížka**

| Okno nástroje | Funkce |
| --- | --- |
| Vlastnosti | Mřížka, která zobrazuje seznam vlastností pro vybraný objekt spolu s výběrem hodnot pro úpravu těchto vlastností. |
| Seznam úkolů | Mřížka, která umožňuje uživateli vytvářet/ upravovat/odstraňovat úkoly a komentáře. |

**Okna nástroje obsah**

| Okno nástroje | Funkce |
| --- | --- |
| Nápověda | Okno, které umožňuje uživatelům přístup k různým metodám získání nápovědy z možnosti How Do I?" videa do fórm MSDN. |
| Dynamická nápověda | Okno nástroje, které zobrazuje odkazy na témata nápovědy vztahující se k aktuálnímu výběru. |
| prohlížeč objektů | Sada rámců se dvěma sloupci se seznamem součástí hierarchických objektů v levém podokně a vlastnostmi a metodami objektu v pravém sloupci. |

**Okna nástroje dialog**

| Okno nástroje | Funkce |
| --- | --- |
| Vyhledávání | Dialogové okno, které umožňuje uživateli najít nebo najít a nahradit v různých souborech v rámci řešení. |
| Rozšířené hledání | Dialogové okno, které umožňuje uživateli najít nebo najít a nahradit v různých souborech v rámci řešení. |

**Další okna nástrojů**

::: moniker range="vs-2017"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Okno nástroje slouží k ukládání prvků, které budou vynechány na návrhové povrchy, poskytuje konzistentní zdroj přetažení pro všechny návrháře. |
| Úvodní stránka | Portál uživatele do sady Visual Studio s přístupem k informačním kanálům pro vývojáře, nápovědě sady Visual Studio a nedávným projektům. Uživatelé mohou také vytvořit vlastní úvodní stránky zkopírováním souboru StartPage.xaml\" z adresáře programových souborů Common7\IDE\StartPages Visual Studio do složky StartPages v adresáři dokumentů sady Visual Studio a poté ručně upravit jazyk XAML nebo jej otevřít v sadě Visual Studio nebo jiném editoru kódu. |

::: moniker-end

::: moniker range=">=vs-2019"

| Okno nástroje | Funkce |
| --- | --- |
| Sada nástrojů | Okno nástroje slouží k ukládání prvků, které budou vynechány na návrhové povrchy, poskytuje konzistentní zdroj přetažení pro všechny návrháře. |

::: moniker-end

**Okna nástrojů ladicího programu**

| Okno nástroje | Funkce |
| --- | --- |
| Auta ||
| Okamžité ||
| Výstup | Výstupní okno lze použít vždy, když máte textové události nebo stav deklarovat. |
| Memory (Paměť) ||
| Zarážky ||
| Spuštěno ||
| Dokumenty ||
| Zásobník volání ||
| Místní obyvatelé ||
| Hodinky ||
| Demontáž ||
| Registruje ||
| Vlákna ||

## <a name="document-editor-conventions"></a><a name="BKMK_DocumentEditorConventions"></a>Konvence editoru dokumentů

### <a name="document-interactions"></a>Interakce s dokumenty
"Dokument dobře" je největší prostor v rámci IDE a je místo, kde uživatel obecně zaměřilsvou pozornost, aby dokončili své úkoly, za pomoci doplňkových oken nástrojů. Editory dokumentů představují základní jednotky práce, které uživatel otevře a uloží v rámci sady Visual Studio. Zachovávají silný smysl pro výběr vázaný na Průzkumníka řešení nebo jiná aktivní okna hierarchie. Uživatel by měl být schopen přejděte na jedno z těchto oken hierarchie a vědět, kde je dokument obsažen a jeho vztah k řešení, projektu nebo jinému kořenovému objektu poskytovanému balíčkem sady Visual Studio.

Úpravy dokumentů vyžadují konzistentní uživatelské prostředí. Chcete-li uživateli umožnit, aby se místo správy oken a hledání příkazů zaměřil na daný úkol, vyberte strategii zobrazení dokumentu, která nejlépe vyhovuje úlohám uživatele pro úpravy tohoto typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Běžné interakce pro dokument dobře

- Udržujte konzistentní model interakce ve společných prostředích **Nový soubor** a **Otevřený soubor.**

- Po otevření okna dokumentu aktualizujte související funkce v souvisejících oknech a nabídkách.

- Příkazy nabídek jsou vhodně integrovány do běžných nabídek, jako jsou **nabídky Úpravy**, **Formát**a **Zobrazení.** Pokud je k dispozici značné množství specializovaných příkazů, lze vytvořit novou nabídku. Tato nová nabídka by měla být viditelná pouze v případě, že dokument má fokus.

- Vložený panel nástrojů může být umístěn v horní části editoru. To je vhodnější mít samostatný panel nástrojů, který se zobrazí mimo editor.

- Vždy udržujte výběr v Průzkumníku řešení nebo v podobném okně aktivní hierarchie.

- Poklepáním na dokument v Průzkumníku řešení by měla provést stejnou akci jako **Otevřít**.

- Pokud lze u typu dokumentu použít více editorů, měl by být uživatel schopen přepsat nebo obnovit výchozí akci u daného typu dokumentu pomocí dialogového okna **Otevřít v** textu klepnutím pravým tlačítkem myši na soubor a výběrem **možnosti Otevřít v** programu z místní nabídky.

- Nevytvářejte průvodce v dokumentu dobře.

### <a name="user-expectations-for-specific-document-types"></a>Očekávání uživatelů pro konkrétní typy dokumentů
Existuje několik různých základních typů editorů dokumentů a každý z nich má sadu interakcí, které jsou konzistentní s ostatními stejného typu.

- **Textový editor:** editor kódu, soubory protokolu

- **Návrhová plocha:** Návrhář formulářů WPF, formuláře systému Windows

- **Editor stylu dialogu:** Návrhář manifestu, vlastnosti projektu

- **Návrhář modelu:** návrhář pracovního postupu, kód, diagram architektury, postup

Existuje také několik typů bez editoru, které dobře používají dokument. I když dokumenty samy neupravují, musí se řídit standardními interakcemi pro okna dokumentů.

- **Zprávy:** Sestava IntelliTrace, sestava Hyper-V, sestava profileru

- **Řídicí panel:** Centrum diagnostiky

#### <a name="text-based-editors"></a>Textové editory

- Dokument se účastní modelu karty Náhled, což umožňuje zobrazit náhled dokumentu bez jeho otevření.

- Struktura dokumentu může být reprezentována v okně doprovodného nástroje, například v osnově dokumentu.

- Technologie IntelliSense (v případě potřeby) se bude chovat konzistentně s ostatními editory kódu.

- Automaticky otevíraná hesla nebo asistenční ui sledovat podobné styly a vzory pro stávající podobné ui, jako je například CodeLens.

- Zprávy týkající se stavu dokumentu se zobrazí v ovládacím prvku informačního panelu v horní části dokumentu nebo na stavovém řádku.

- Uživatel musí být schopen přizpůsobit vzhled písem a barev pomocí stránky **Možnosti nástroje >,** a to buď na stránce sdílená písma a barvy, nebo na stránce specifické pro editor.

#### <a name="design-surfaces"></a>Konstrukční povrchy

- Prázdný návrhář by měl mít na povrchu vodoznak označující, jak začít.

- Mechanismy přepínání zobrazení budou následovat existující vzory, jako je například poklepání na otevření editoru kódu nebo karty v okně dokumentu umožňující interakci s oběma podokny.

- Přidání prvků do návrhové plochy by mělo být provedeno prostřednictvím panelu nástrojů, pokud není vyžadováno vysoce specifické okno nástroje.

- Položky na povrchu budou následovat konzistentní model výběru.

- Vložené panely nástrojů obsahují pouze příkazy specifické pro dokument, nikoli běžné příkazy, například **Uložit**.

#### <a name="dialog-style-editors"></a>Editory ve stylu dialogů

- Rozložení ovládacího prvku by se mělo řídit podle běžných konvencí rozložení dialogů.

- Karty v editoru by neměly odpovídat vzhledu karet dokumentu, měly by odpovídat jednomu ze dvou povolených stylů vnitřních karet.

- Uživatelé musí být schopni pracovat s ovládacími prvky pouze pomocí klávesnice; aktivací editoru a procházením tabulátorem pomocí ovládacích prvků nebo pomocí standardních mnemotechnické pomůcky.

- Návrhář by měl používat společný uložit model. Na povrch by neměla být umístěna žádná tlačítka pro uložení nebo potvrzení, i když mohou být vhodná jiná tlačítka.

#### <a name="model-designers"></a>Návrháři modelů

- Prázdný návrhář by měl mít na povrchu vodoznak označující, jak začít.

- Přidání prvků do návrhové plochy by mělo být provedeno prostřednictvím panelu nástrojů.

- Položky na povrchu budou následovat konzistentní model výběru.

- Vložené panely nástrojů obsahují pouze příkazy specifické pro dokument, nikoli běžné příkazy, například **Uložit**.

- Na povrchu se může objevit legenda, indikativní nebo vodoznak.

- Uživatel musí být schopen přizpůsobit vzhled písem/barev pomocí stránky **Možnosti nástroje >,** a to buď na stránce sdílená písma a barvy, nebo na stránce specifické pro editor.

#### <a name="reports"></a>Sestavy

- Sestavy jsou obvykle pouze informační a neúčastní se uložit model. Mohou však zahrnovat interakci, například odkazy na jiné relevantní informace nebo oddíly, které se rozbalují a sbalí.

- Většina příkazů na povrchu by měla být hypertextové odkazy, nikoli tlačítka.

- Rozložení by mělo obsahovat záhlaví a podle standardních pokynů pro rozložení sestavy.

#### <a name="dashboards"></a>Řídicí panely

- Řídicí panely samy o sobě nemají model interakce, ale slouží jako prostředek, který nabízí celou řadu dalších nástrojů.

- Neúčastní se uložit model.

- Uživatelé musí být schopni pracovat s ovládacími prvky pouze pomocí klávesnice, a to buď aktivací editoru a tabulátory prostřednictvím ovládacích prvků nebo pomocí standardních mnemotechnické pomůcky.

## <a name="dialogs"></a><a name="BKMK_Dialogs"></a>Dialogy

### <a name="introduction"></a>Úvod
Dialogy v sadě Visual Studio by obvykle měly podporovat jednu samostatnou jednotku práce uživatele a poté být odmítnuty.

Pokud jste zjistili, že potřebujete dialog, máte tři možnosti v pořadí podle priority:

1. Integrujte své funkce do jednoho ze sdílených dialogových oken v sadě Visual Studio.

2. Vytvořte si vlastní dialogové okno pomocí vzoru nalezeného v existujícím podobném dialogu.

3. Vytvořte nový dialog podle pokynů pro interakci a rozložení.

Tato část popisuje, jak zvolit správný dialogový vzor v rámci pracovních postupů sady Visual Studio a běžné konvence pro návrh dialogu.

### <a name="themes"></a>Motivy
Dialogová okna v sadě Visual Studio se řídí jedním ze dvou základních stylů:

#### <a name="standard-unthemed"></a>Standardní (bez tématiky)
Většina dialogových oken jsou standardní dialogová okna nástroje a měla by být bez tématika. Nepoužívejte re-šablony běžné ovládací prvky nebo se pokoušet vytvořit stylizované "moderní" tlačítka nebo ovládací prvky. Ovládací prvky a vzhled chromu se řídí [standardními pokyny pro interakci na ploše systému Windows pro dialogová okna](/windows/desktop/uxguide/win-dialog-box).

#### <a name="themed"></a>Tématickém
Speciální "podpis" dialogy mohou být tématika. Tématické dialogy mají odlišný vzhled, který má také některé speciální interakce vzory spojené se stylem. Dialogové okno motivujte pouze v případě, že splňuje tyto požadavky:

- Dialogové okno je běžné prostředí, které bude často vidět a používat mnoho uživatelů (například dialogové okno **Nový projekt.**

- Dialogové okno obsahuje výrazné prvky značky produktu (například dialogové **okno Nastavení účtu).**

- Dialogové okno se zobrazí jako nedílná součást většího toku, který obsahuje další tematou dialogová okna (například dialogové okno **Přidat připojenou službu).**

- Dialog je důležitou součástí prostředí, které hraje strategickou roli při propagaci nebo rozlišování verze produktu.

Při vytváření tematého dialogu použijte příslušné barvy prostředí a postupujte podle správného rozložení a vzorů interakce. (Viz [Rozložení pro Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).)

### <a name="dialog-design"></a>Návrh dialogu
Dobře navržená dialogová okna berou v úvahu následující prvky:

- Podporovaná úloha uživatele

- Styl textu dialogu, jazyk a terminologie

- Možnost volby řízení a konvence ui

- Vizuální specifikace rozvržení a zarovnání ovládacího prvku

- Přístup z klávesnice

#### <a name="content-organization"></a>Organizace obsahu
Zvažte rozdíly mezi těmito základními typy dialogových oken:

- [Jednoduchá dialogová okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) představují ovládací prvky v jednom modálním okně. Prezentace může obsahovat varianty složitých vzorů ovládacího prvku, včetně výběru polí nebo panelu ikon.

- [Vrstvené dialogy](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se používají k co nejvíce obrazovky nemovitostí, když jeden kus uI obsahuje více skupin ovládacích prvků. Seskupení dialogu jsou "vrstvené" pomocí ovládacích prvků tabulátoru, ovládacích prvků navigačního seznamu nebo tlačítek, takže si uživatel může vybrat, které seskupení se má zobrazit v daném okamžiku.

- [Průvodci](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) jsou užitečné pro nasměrování uživatele prostřednictvím logické posloupnosti kroků směrem k dokončení úkolu. Řada možností je nabízena v sekvenčních panelech, které někdy zavádějí různé pracovní postupy ("větve") v závislosti na volbě provedené v předchozím panelu.

#### <a name="simple-dialogs"></a><a name="BKMK_SimpleDialogs"></a>Jednoduchá dialogová okna
Jednoduchý dialog je prezentace ovládacích prvků v jednom modálním okně. Tato prezentace může obsahovat varianty složitých vzorů ovládacího prvku, například výběr polí. Pro jednoduché dialogy postupujte podle standardního obecného rozložení, stejně jako jakékoli konkrétní rozložení potřebné pro komplexní seskupení ovládacích prvk.

![>Vytvořit silný název klíče je příkladem jednoduchého dialogu v sadě Visual Studio.](../../extensibility/ux-guidelines/media/0704-01_createstrongnamekey.png "0704-01_CreateStrongNameKey")<br />Vytvořit silný název klíče je příkladem jednoduchého dialogu v sadě Visual Studio.

#### <a name="layered-dialogs"></a><a name="BKMK_LayeredDialogs"></a>Dialogová okna s vrstvami
Dialogová okna s vrstvami zahrnují karty, řídicí panely a vložené stromy. Používají se k maximalizaci nemovitostí, pokud existuje více skupin ovládacích prvků nabízených v jednom kusu ui. Seskupení jsou vrstvené tak, aby uživatel mohl zvolit, které seskupení chcete zobrazit v jednom okamžiku.

V nejjednodušším případě mechanismus pro přepínání mezi seskupeníje ovládací prvek karta. K dispozici je několik alternativ. Informace o tom, jak zvolit nejvhodnější styl, najdete v tématu Stanovení priorit a vrstvení.

Dialogové okno **Volby nástrojů &gt; ** je příkladem dialogu s vrstvami pomocí vloženého stromu:

![Nástroje > Možnosti je příkladem dialogu s vrstvami v sadě Visual Studio.](../../extensibility/ux-guidelines/media/0704-02_toolsoptions.png "0704-02_ToolsOptions")<br />Nástroje > Možnosti je příkladem dialogu s vrstvami v sadě Visual Studio.

#### <a name="wizards"></a><a name="BKMK_Wizards"></a>Průvodci
Průvodci jsou užitečné pro nasměrování uživatele prostřednictvím logické posloupnosti kroků při dokončení úkolu. Řada možností jsou nabízeny v sekvenční panely, a uživatel musí pokračovat v každém kroku před pokračováním na další. Jakmile jsou k dispozici dostatečné výchozí hodnoty, je povoleno tlačítko **Dokončit.**

 Modální průvodci se používají pro úkoly, které:

- Obsahují větvení, kde jsou nabízeny různé cesty v závislosti na volbách uživatele

- Obsahují závislosti mezi kroky, kde následující kroky závisí na vstupu uživatele z předchozího kroku (kroků)

- Jsou dostatečně složité, že by se ujmutého článku mělo vysvětlit nabízené volby a možné výsledky v každém kroku

- Jsou transakční, vyžadující sadu kroků, které mají být dokončeny v plném rozsahu před jakékoli změny jsou potvrzeny

### <a name="common-conventions"></a>Společné konvence
Chcete-li dosáhnout optimálního návrhu a funkčnosti pomocí dialogových oken, postupujte podle těchto konvencí o velikosti dialogu, poloze, standardech, konfiguraci a zarovnání ovládacího prvku, textu a záhlaví, ovládacích tlačítkách a přístupových klávesách.

Pokyny pro konkrétní rozložení najdete [v tématu Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Velikost
Dialogová okna by měla být v rozsahu minimálně 1024 × 768 a počáteční velikost dialogového okna by neměla přesáhnout 900 × 700 pixelů. Dialogová okna mohou mít možnost zhodnošit, ale není to požadavek.

Existují dvě doporučení pro dialogová okna s nastavitelnou rezižádostí:

1. Minimální velikost je definována pro dialogové okno, které bude optimalizováno pro sadu ovládacích prvku bez oříznutí a upravit tak, aby vyhovovaly přiměřenému růstu lokalizace.

2. Velikost uživatelského měřítka přetrvává od relace k relaci. Pokud například uživatel změní měřítko dialogového okna na 150 %, zobrazí se následné spuštění dialogového okna na 150 %.

#### <a name="position"></a>Pozice
Dialogová okna se musí při prvním spuštění zobrazit v centru ide. Poslední pozice dialogových oken, které nelze změnit, nemusí být zachována, takže se zobrazí na následujících spuštěních.

Pro dialogová okna s nastavitelnou velikostí by měla být zachována při následných spuštěních. Pro modální dialogová okna s nastavitelnou polohou nemusí být pozice zachována. Jejich zobrazení vystředěné v rámci rozhraní IDE zabrání možnosti, že se dialogové okno zobrazí v nepředvídatelné nebo nepoužitelné poloze při změně konfigurace zobrazení uživatele.

U nemodlavých dialogových oken, která lze přemístit, by měla být pozice uživatele zachována při následných spuštěních, protože dialogové okno může být často používáno jako nedílná součást většího pracovního postupu.

Když dialogová okna musí vytvořit další dialogová okna, vrchní dialogové okno by mělo kaskády doprava a dolů od nadřazeného objektu tak, aby bylo zřejmé, že uživatel i oni přešli na nové místo.

#### <a name="modality"></a>Modality
Být modální znamená, že uživatelé jsou povinni dokončit nebo zrušit dialogové okno před pokračováním. Vzhledem k tomu, že modální dialogová okna blokují uživateli interakci s jinými částmi prostředí, měl by je tok úloh vaší funkce používat co nejšetrněji. Pokud je nutná modální operace, Visual Studio má řadu sdílených dialogových oken můžete integrovat funkce do. Pokud je nutné vytvořit nový dialog, postupujte podle vzoru interakce existujícího dialogového okna s podobnými funkcemi.

Když uživatelé potřebují provádět dvě aktivity najednou, jako **je najít** a **nahradit** při psaní nového kódu, dialogové okno by mělo být nemodální, aby mezi nimi uživatel mohl snadno přepínat. Visual Studio obvykle používá okna nástrojů pro tento druh editorpodporující propojené úlohy.

#### <a name="control-configuration"></a>Konfigurace ovládacího prvku
Buďte konzistentní s existující konfigurace ovládacího prvku, které dosáhnout stejné věci v sadě Visual Studio.

#### <a name="title-bars"></a>Záhlaví

- Text v záhlaví musí odrážet název příkazu, který jej spustil.

- V záhlaví dialogových oken by neměla být použita žádná ikona. V případech, kdy systém vyžaduje jeden, použijte logo Visual Studio.

- Dialogová okna by neměla mít minimalizovat nebo maximalizovat tlačítka.

- Tlačítka nápovědy v záhlaví byla zastaralá. Nepřidávejte je do nových dialogových oken. Pokud existují, měli by spustit téma nápovědy, které je koncepčně relevantní pro daný úkol.

  ![Specifikace obecných zásad pro záhlaví v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-03_titlebarspecs.png "0704-03_TitleBarSpecs")<br />Specifikace obecných zásad pro záhlaví v dialogových oknech sady Visual Studio

#### <a name="control-buttons"></a>Ovládací tlačítka
Tlačítka **OK**, **Cancel**a **Nápověda** by měla být obecně uspořádána vodorovně v pravém dolním rohu dialogového okna. Alternativní svislý zásobník je povolen, pokud dialogové okno obsahuje několik dalších tlačítek v dolní části dialogového okna, které by představovaly vizuální záměnu s ovládacími tlačítky.

![Přijatelné konfigurace ovládacích tlačítek v dialogových oknech sady Visual Studio](../../extensibility/ux-guidelines/media/0704-04_controlbuttonconfig.png "0704-04_ControlButtonConfig")<br />Přijatelné konfigurace ovládacích tlačítek v dialogových oknech sady Visual Studio

Dialogové okno musí obsahovat výchozí ovládací tlačítko. Chcete-li určit nejlepší příkaz, který chcete použít jako výchozí, zvolte z následujících možností (uvedených v pořadí podle priority):

- Jako výchozí zvolte nejbezpečnější a nejbezpečnější příkaz. To znamená, že výběr příkazu s největší pravděpodobností zabránit ztrátě dat a zabránit nezamýšlený přístup k systému.

- Pokud ztráta dat a zabezpečení nejsou faktory, zvolte výchozí příkaz na základě pohodlí. Zahrnutí nejpravděpodobnějšího příkazu jako výchozího zlepší pracovní postup uživatele, pokud dialogové okno podporuje časté nebo opakující se úkoly.

Nevybírejte pro výchozí příkaz trvale destruktivní akci. Pokud takový příkaz je k dispozici, zvolte bezpečnější příkaz jako výchozí místo.

#### <a name="access-keys"></a>Přístupové klíče
Nepoužívejte přístupové klávesy pro tlačítka **OK**, **Cancel**nebo **Help.** Tato tlačítka jsou ve výchozím nastavení mapována na klávesové zkratky:

| Název tlačítka | Klávesová zkratka |
| --- | --- |
| OK | Enter |
| Zrušit | Esc |
| Nápověda | F1 |

#### <a name="imagery"></a>Snímky
Používejte obrázky střídmě v dialogových oknech. Nepoužívejte velké ikony v dialogových oknech pouze k využití místa. Obrázky používejte pouze v případě, že jsou důležitou součástí předávání zprávy uživateli, jako jsou ikony upozornění nebo animace stavu.

### <a name="prioritizing-and-layering"></a><a name="BKMK_PrioritizingAndLayering"></a>Stanovení priorit a vrstvení

#### <a name="prioritizing-your-ui"></a>Stanovení priority ui
Může být nutné přenést určité prvky uživatelského rozhraní do popředí a umístit pokročilejší chování a možnosti (včetně obskurních příkazů) do dialogových oken. Převést běžně používané funkce do popředí tím, že prostor pro něj a tím, že je viditelné ve výchozím nastavení v ui s textovým popiskem při zobrazení dialogového okna.

#### <a name="layering-your-ui"></a>Vrstvení vašeho uI
Pokud jste zjistili, že dialog je nezbytné, ale související funkce, které chcete prezentovat uživateli přesahuje to, co lze zobrazit v jednoduchém dialogu, pak je třeba vrstvy uživatelského rozhraní. Nejběžnější metody vrstvení Visual Studio používá jsou karty a chodby nebo řídicí panely. V některých případech může být vhodné oblasti, které lze rozbalit a sbalit. Adaptivní uI se obecně nedoporučuje v sadě Visual Studio.

Existují výhody a nevýhody různých metod vrstvení uI prostřednictvím ovládacích prvků podobných tabulátoru. Projděte si níže uvedený seznam a ujistěte se, že vybíráte techniku vrstvení, která je vhodná pro vaši situaci.

##### <a name="tabbing"></a>Tabování

| Spínací mechanismus | Výhody a vhodné použití | Nevýhody a nevhodné použití |
| --- | --- | --- |
| Ovládací prvek Tabulátor | Logicky seskupit stránky dialogu do souvisejících sad<br /><br />Užitečné pro méně než pět (nebo počet karet, které se vejdou do jednoho řádku přes dialogové okno) stránky souvisejících ovládacích prvků v dialogovém okně<br /><br />Popisky tabulátorů musí být krátké: jedno nebo dvě slova, která mohou snadno identifikovat obsah<br /><br />Společný styl systémového dialogu<br /><br />Příklad: **Vlastnosti položky &gt; Průzkumníka souborů** | Vytváření popisných krátkých popisků může být obtížné<br /><br />Obecně nelze změnit měřítko za pět karet v jednom dialogovém okně<br /><br />Nevhodné, pokud máte příliš mnoho karet pro jeden řádek (použijte alternativní techniku vrstvení)<br /><br />Není rozšiřitelný |
| Navigace na postranním panelu | Jednoduché spínací zařízení, které pojme více kategorií než karty<br /><br />Plochý seznam kategorií (bez hierarchie)<br /><br />Extensible<br /><br />Příklad: **Přizpůsobit... Přidat &gt; příkaz** | Není dobré využít horizontální prostor, pokud existuje méně než tři skupiny<br /><br />Úkol může být vhodnější pro rozevírací seznam. |
| Řízení stromu | Umožňuje neomezené kategorie<br /><br />Umožňuje seskupování a/nebo hierarchii kategorií<br /><br />Extensible<br /><br />Příklad: ** &gt; Možnosti nástrojů** | Silně vnořené hierarchie mohou způsobit nadměrné vodorovné posouvání<br /><br />Visual Studio má nadbytek stromových zobrazení |
| Průvodce | Pomáhá s dokončením úkolu tím, že vede uživatele prostřednictvím sekvenčních kroků založených na úkolech: průvodce představuje úkol na vysoké úrovni a jednotlivé panely představují dílčí úkoly potřebné k provedení celkového úkolu<br /><br />Užitečné, když úkol překročí hranice uživatelského rozhraní, jako když by jinak uživatel musel k dokončení úkolu použít více editorů a oken nástrojů<br /><br />Užitečné v případě, že úloha vyžaduje větvení<br /><br />Užitečné, když úkol obsahuje závislosti mezi kroky<br /><br />Užitečné, když několik podobných úkolů s jedním rozhodnutím rozdvojené lze zobrazit v jednom dialogu ke snížení počtu různých podobných dialogů | Nevhodné pro všechny úkoly, které nevyžadují sekvenční pracovní postup<br /><br />Uživatelé mohou být zahlceni a zmateni průvodcem s příliš mnoha kroky<br /><br />Průvodci mají ze své podstaty omezenou obrazovku nemovitostí |

##### <a name="hallways-or-dashboards"></a>Chodby nebo palubní desky
Chodby a řídicí panely jsou dialogy nebo panely, které slouží jako spouštěcí body do jiných dialogových oken a oken. Dobře navržená "chodba" okamžitě vykresluje pouze nejběžnější možnosti, příkazy a nastavení, což uživateli umožňuje snadno provádět běžné úkoly. Stejně jako v reálném světě chodba poskytuje vchody pro přístup do místností za nimi, zde méně-společné ui se shromažďují do samostatných "místností" (často jiné dialogy) souvisejících funkcí, které lze přistupovat z hlavní chodby.

Případně urozhraní, které nabízí všechny dostupné funkce v jedné kolekci, spíše než refaktoring méně běžné funkce do samostatných umístění je jednoduše řídicí panel.

![Koncept chodby pro vystavení dalšího ui v aplikaci Outlook](../../extensibility/ux-guidelines/media/0704-08_hallway.png "0704-08_Hallway")<br />Koncept chodby pro vystavení dalšího ui v aplikaci Outlook

##### <a name="adaptive-ui"></a>Adaptivní uI
Zobrazení nebo skrytí uživatelského rozhraní na základě využití nebo vlastního prostředí uživatele je další způsob, jak prezentovat potřebné uživatelské rozhraní při skrytí jiných částí. To se nedoporučuje v sadě Visual Studio, jako algoritmy pro rozhodování o tom, kdy zobrazit nebo skrýt ui může být složité a pravidla budou vždy nesprávné pro některé sady případů.

## <a name="projects"></a><a name="BKMK_Projects"></a>Projekty

### <a name="projects-in-the-solution-explorer"></a>Projekty v Průzkumníku řešení
Většina projektů jsou klasifikovány jako založené na odkazu, na základě adresáře nebo smíšené. Všechny tři typy projektů jsou podporovány současně v Průzkumníku řešení. Kořen uživatelské zkušenosti při práci s projekty probíhá uvnitř tohoto okna. Přestože různé uzly projektu jsou referenční, adresář nebo smíšené míchaného typu projektů, je společný vzor interakce, který by měl být použit jako výchozí bod před rozcházející se do vzorců uživatele specifické pro projekt.

Projekty by měly vždy:

- Podpora přidání složek projektu pro uspořádání obsahu projektu

- Udržovat konzistentní model pro trvalost projektu

Projekty by měly také udržovat konzistentní modely interakce pro:

- Odebrání položek projektu

- Ukládání dokumentů

- Úpravy vlastností projektu

- Úprava projektu v alternativním zobrazení

- Operace přetažení myší

### <a name="drag-and-drop-interaction-model"></a>Model interakce přetažením
Projekty se obvykle klasifikují jako založené na referencích (lze zachovat pouze odkazy na položky projektu v úložišti), založené na adresáři (lze zachovat pouze položky projektu fyzicky uložené v hierarchii projektu) nebo smíšené (schopné zachovat odkazy nebo fyzické předměty). Rozhraní IDE pojme všechny tři typy projektů současně v průzkumníku **řešení**.

Z hlediska přetažení by měly následující charakteristiky platit pro každý typ projektu v průzkumníku **řešení**:

- **Referenční projekt:** Klíčovým bodem je, že projekt je přetažením kolem odkaz na položku v úložišti. Pokud projekt založený na odkazech funguje jako zdroj pro operaci přesunutí, měl by pouze odebrat odkaz na položku z projektu. Položka by ve skutečnosti neměla být odstraněna z pevného disku. Pokud projekt založený na odkazu funguje jako cíl pro operaci přesunutí (nebo kopírování), měl by přidat odkaz na původní zdrojovou položku bez vytvoření soukromé kopie položky.

- **Projekt založený na adresáři:** Z hlediska přetažení projektu se táhne kolem fyzické položky, nikoli odkaz. Pokud projekt založený na adresáři funguje jako zdroj pro operaci přesunutí, měl by skončit odstraněním fyzické položky z pevného disku a odebráním z projektu. Pokud projekt založený na adresáři funguje jako cíl pro operaci přesunutí (nebo kopírování), měl by vytvořit kopii zdrojové položky v cílovém umístění.

- **Projekt smíšených cílů:** Z hlediska přetažení je chování tohoto typu projektu založeno na povaze přetahované položky (buď odkaz na položku v úložišti, nebo na položku samotnou). Správné chování pro odkazy a fyzické položky jsou popsány výše.

Pokud by v **Průzkumníku řešení**existoval pouze jeden typ projektu , operace přetažení by byly jednoduché. Vzhledem k tomu, že každý systém projektu má schopnost definovat své vlastní chování přetažení, některé pokyny (na základě chování přetažení průzkumníka Windows) by měly být dodržovány zajistit předvídatelné uživatelské prostředí:

- Nezměněná operace přetažení v **Průzkumníku řešení** (pokud nejsou stisknuty klávesy Ctrl ani Shift) by měla vést k operaci přesunutí.

- Operace se stisknutou klávesou Shift by měla mít za následek také operaci přesunutí.

- Operace se stisknutou klávesou Ctrl by měla vést k operaci kopírování.

- Systémy projektů založené na odkazech a smíšené projekty podporují pojem přidání odkazu (nebo odkazu) ke zdrojové položce. Pokud jsou tyto projekty cílem operace přetažení myší (při podržení **klávesCtrl + Shift),** mělo by to mít za následek odkaz na položku přidanou do projektu

Ne všechny operace přetažení jsou rozumné napříč kombinacemi referenčních, adresářových a smíšených projektů. Zejména je problematické předstírat, že umožňuje přesun operace mezi zdrojový projekt založený na adresáři a referenční cílový projekt, protože zdrojový projekt založený na adresáři bude muset odstranit zdrojovou položku po dokončení přesunutí. Cílový projekt založený na odkazech by pak skončil s odkazem na odstraněnou položku.

Je také zavádějící předstírat, že povolit operaci kopírování mezi těmito typy projektů, protože cílový projekt založený na odkazu by neměl vytvořit nezávislou kopii zdrojové položky. Podobně by nemělo být povoleno přetahování kláves Ctrl + Shift do cílového projektu založeného na adresáři, protože projekt založený na adresáři nemůže zachovat odkazy. V případech, kdy operace přetažení není podporována, ide by měl zakázat přetažení a zobrazit uživateli kurzor bez pádu (viz tabulka ukazatele níže).

Chcete-li správně implementovat chování přetažení, zdrojový projekt přetažení musí komunikovat jeho povahu do cílového projektu. (Například je to odkaz- nebo adresář-based?) Tyto informace jsou označeny formátem schránky, který nabízí zdroj. Jako zdroj přetažení (nebo operace kopírování schránky) by `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS` projekt měl nabízet buď nebo v uvedeném pořadí, v závislosti na tom, zda je projekt založen na referencích nebo na adresáři. Oba tyto formáty mají stejný obsah dat, který `CF_HDROP` je podobný formátu systému Windows s tím rozdílem, že `Projref` seznamy řetězců, `IVsSolution::GetProjrefOfItem` místo `::GetProjrefOfProject` toho, aby názvy souborů, jsou dvakrát`NULL` ukončený seznam řetězců (jak se vrátil z nebo podle potřeby).

Jako cíl drop (nebo operace vložení schránky), projekt `CF_VSREFPROJECTITEMS` by `CF_VSSTGPROJECTITEMS`měl přijmout oba a , i když přesné zpracování operace přetažení se liší v závislosti na povaze cílového projektu a zdrojového projektu. Zdrojový projekt deklaruje svou `CF_VSREFPROJECTITEMS` `CF_VSSTGPROJECTITEMS`povahu podle toho, zda nabízí nebo . Cíl poklesu chápe svou vlastní povahu, a proto má dostatek informací, aby se rozhodl, zda by měl být proveden přesun, kopie nebo odkaz. Uživatel také upraví, která operace přetažení by měla být provedena stisknutím kláves Ctrl, Shift nebo Ctrl nebo Shift. Je důležité, aby cíl přetažení správně uvedl, která `DragEnter` operace `DragOver` bude provedena předem v jejích metodách a metodách. **Průzkumník řešení** automaticky ví, zda zdrojový projekt a cílový projekt jsou stejný projekt.

Přetahování položek projektu mezi instancemi sady Visual Studio (například z jedné instance devenv.exe do jiné) není výslovně podporováno. **Průzkumník řešení** také přímo zakáže to.

Uživatel by měl být vždy schopen určit účinek operace přetažení výběrem položky, přetažením do cílového umístění a pozorováním, které z následujících ukazatelů myši se zobrazí před vynecháním položky:

| Ukazatel myši | Příkaz | Popis |
| :---: | --- | --- |
| ![Ikona myši "no drop"](../../extensibility/ux-guidelines/media/0706-01_mousenodrop.png "0706-01_MouseNoDrop") | Bez poklesu | Položku nelze vynechat do zadaného umístění. |
| ![Ikona myši "kopírovat"](../../extensibility/ux-guidelines/media/0706-02_mousecopy.png "0706-02_MouseCopy") | Kopírovat | Položka bude zkopírována do cílového umístění. |
| ![Ikona myši "move"](../../extensibility/ux-guidelines/media/0706-03_mousemove.png "0706-03_MouseMove") | Přesunout | Položka bude přesunuta do cílového umístění. |
| ![Ikona "Přidat odkaz" myši](../../extensibility/ux-guidelines/media/0706-04_mouseaddref.png "0706-04_MouseAddRef") | Přidání odkazu | Odkaz na vybranou položku bude přidán do cílového umístění. |

#### <a name="reference-based-projects"></a>Referenční projekty
 Následující tabulka shrnuje operace přetažení (stejně jako vyjmutí/kopírování/vložení), které by měly být provedeny na základě povahy zdrojové položky a modifikačních kláves stisknutých pro cílové projekty založené na odkazovaných:

| Modifikátor | Kategorie | Zdrojová položka: Odkaz/odkaz | Zdrojová položka: Fyzická`CF_HDROP`položka nebo systém souborů ( ) |
| --- | --- | --- | --- |
| Bez modifikátoru | Akce | Přesunout | Odkaz |
| Bez modifikátoru | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Bez modifikátoru | Zdroj | Odstraní odkaz na původní položku. | Zachová původní položku. |
| Bez modifikátoru | Výsledek | `DROPEFFECT_MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_LINK`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Shift+táhnout | Akce | Přesunout | Bez poklesu |
| Shift+táhnout | Cíl | Přidá odkaz na původní položku. | Bez poklesu |
| Shift+táhnout | Zdroj | Odstraní odkaz na původní položku. | Bez poklesu |
| Shift+táhnout | Výsledek | `DROPEFFECT_MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | Bez poklesu |
| Ctrl+Táhnout | Akce | Kopírovat | Bez poklesu |
| Ctrl+Táhnout | Cíl | Přidá odkaz na původní položku. | Bez poklesu |
| Ctrl+Táhnout | Zdroj | Zachová odkaz na původní položku. | Bez poklesu |
| Ctrl+Táhnout | Výsledek | `DROPEFFECT_COPY`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | Bez poklesu |
| Ctrl+Shift+Táhnout | Akce | Odkaz | Odkaz |
| Ctrl+Shift+Táhnout | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Ctrl+Shift+Táhnout | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl+Shift+Táhnout | Výsledek | `DROPEFFECT_LINK`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_LINK`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Ctrl+Shift+Táhnout | Poznámka | Stejné jako chování přetažení klávesových zkratek v Průzkumníkovi Windows. ||
| Vyjmout/vložit | Akce | Přesunout | Odkaz |
| Vyjmout/vložit | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Vyjmout/vložit | Zdroj | Zachová odkaz na původní položku.|Zachová původní položku. |
| Vyjmout/vložit | Výsledek | Položka zůstává v původním umístění v úložišti | Položka zůstává v původním umístění v úložišti |
| Kopírovat nebo vložit | Akce | Kopírovat | Odkaz |
| Kopírovat nebo vložit | Zdroj | Přidá odkaz na původní položku. | Přidá odkaz na původní položku. |
| Kopírovat nebo vložit | Výsledek | Zachová odkaz na původní položku. | Zachová původní položku. |
| Kopírovat nebo vložit | Akce | Položka zůstává v původním umístění v úložišti | Položka zůstává v původním umístění v úložišti |

#### <a name="directory-based-projects"></a>Projekty založené na adresáři
Následující tabulka shrnuje operace přetažení (stejně jako vyjmutí/kopírování/vložení), které by měly být provedeny na základě povahy zdrojové položky a modifikačních kláves stisknutých pro cílové projekty založené na adresáři:

| Modifikátor | Kategorie | Zdrojová položka: Odkaz/odkaz | Zdrojová položka: Fyzická`CF_HDROP`položka nebo systém souborů ( ) |
|-----------------|----------| - | - |
| Bez modifikátoru | Akce | Přesunout | Přesunout |
| Bez modifikátoru | Cíl | Zkopíruje položku do cílového umístění | Zkopíruje položku do cílového umístění |
| Bez modifikátoru | Zdroj | Odstraní odkaz na původní položku. | Odstraní odkaz na původní položku. |
| Shift+táhnout | Akce | Přesunout | Přesunout |
| Shift+táhnout | Cíl | Zkopíruje položku do cílového umístění | Zkopíruje položku do cílového umístění |
| Shift+táhnout | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Shift+táhnout | Výsledek | `DROPEFFECT_MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Ctrl+Táhnout | Akce | Kopírovat | Kopírovat |
| Ctrl+Táhnout | Cíl | Zkopíruje položku do cílového umístění | Zkopíruje položku do cílového umístění |
| Ctrl+Táhnout | Zdroj | Zachová odkaz na původní položku. | Zachová odkaz na původní položku. |
| Ctrl+Táhnout | Výsledek | `DROPEFFECT_COPY`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_COPY`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Ctrl+Shift+Táhnout | | Bez poklesu | Bez poklesu |
| Vyjmout/vložit | Akce | Přesunout | Přesunout |
| Vyjmout/vložit | Cíl | Zkopíruje položku do cílového umístění | Zkopíruje položku do cílového umístění |
| Vyjmout/vložit | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Vyjmout/vložit | Výsledek | Položka zůstává v původním umístění v úložišti | Položka je odstraněna z původního umístění v úložišti. |
| Kopírovat nebo vložit | Akce | Kopírovat | Kopírovat |
| Kopírovat nebo vložit | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění |
| Kopírovat nebo vložit | Zdroj | Zachová původní položku. | Zachová původní položku. |
| Kopírovat nebo vložit | Výsledek | Položka zůstává v původním umístění v úložišti | Položka zůstává v původním umístění v úložišti |

#### <a name="mixed-target-projects"></a>Projekty se smíšenými cíli
Následující tabulka shrnuje operace přetažení (stejně jako vyjmutí/kopírování/vložení), které by měly být provedeny na základě povahy zdrojové položky a modifikačních kláves stisknutých pro projekty se smíšeným cílem:

| Modifikátor | Kategorie | Zdrojová položka: Odkaz/odkaz | Zdrojová položka: Fyzická`CF_HDROP`položka nebo systém souborů ( ) |
| --- | --- | --- | --- |
| Bez modifikátoru | Akce | Přesunout | Přesunout |
| Bez modifikátoru | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění |
| Bez modifikátoru | Zdroj | Odstraní odkaz na původní položku. | Odstraní odkaz na původní položku. |
| Bez modifikátoru | Výsledek | `DROPEFFECT_ MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_ MOVE`je vrácena `::Drop` jako akce z a položka je odstraněna z původního umístění v úložišti |
| Shift+táhnout | Akce | Přesunout | Přesunout |
| Shift+táhnout | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění |
| Shift+táhnout | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Shift+táhnout | Výsledek | `DROPEFFECT_ MOVE`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_ MOVE`je vrácena `::Drop` jako akce z a položka je odstraněna z původního umístění v úložišti |
| Ctrl+Táhnout | Akce | Kopírovat | Kopírovat |
| Ctrl+Táhnout | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění |
| Ctrl+Táhnout | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl+Táhnout | Výsledek | `DROPEFFECT_ COPY`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_ COPY`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Ctrl+Shift+Táhnout | Akce | Odkaz | Odkaz |
| Ctrl+Shift+Táhnout | Cíl | Přidá odkaz na původní položku. | Přidá odkaz na původní zdrojové položky. |
| Ctrl+Shift+Táhnout | Zdroj | Zachová odkaz na původní položku. | Zachová původní položku. |
| Ctrl+Shift+Táhnout | Výsledek | `DROPEFFECT_ LINK`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti | `DROPEFFECT_ LINK`je vrácena `::Drop` jako akce od a položka zůstává v původním umístění v úložišti |
| Vyjmout/vložit | Akce | Přesunout | Přesunout |
| Vyjmout/vložit | Cíl | Zkopíruje položku do cílového umístění | Zkopíruje položku do cílového umístění |
| Vyjmout/vložit | Zdroj | Odstraní odkaz na původní položku. | Odstraní položku z původního umístění. |
| Vyjmout/vložit | Výsledek | Položka zůstává v původním umístění v úložišti | Položka je odstraněna z původního umístění v úložišti. |
| Kopírovat nebo vložit | Akce | Kopírovat | Kopírovat |
| Kopírovat nebo vložit | Cíl | Přidá odkaz na původní položku. | Zkopíruje položku do cílového umístění |
| Kopírovat nebo vložit | Zdroj | Zachová původní položku. | Zachová původní položku. |
| Kopírovat nebo vložit | Výsledek | Položka zůstává v původním umístění v úložišti | Položka zůstává v původním umístění v úložišti |

Tyto podrobnosti je třeba vzít v úvahu při implementaci přetažení v **Průzkumníku řešení**:

- Návrh pro více scénářů výběru.

- Názvy souborů (úplná cesta) musí být jedinečné v celém cílovém projektu nebo přetažení by nemělo být povoleno.

- Názvy složek musí být jedinečné (bez rozlišování velkých a malých písmen) na úrovni, na které jsou vynechány.

- Existují rozdíly v chování mezi soubory, které jsou otevřené nebo uzavřené v době přetažení (není uvedeno ve výše uvedených scénářích).

- Soubory nejvyšší úrovně se chovají mírně odlišně než soubory ve složkách.

Dalším problémem, který je třeba si uvědomit, je, jak zpracovat operace přesunutí u položek, které mají otevřené návrháře nebo editory. Očekávané chování je následující (to platí pro všechny typy projektů):

1. Pokud otevřený editor nebo návrhář nemá žádné neuložené změny, okno editoru/návrháře by mělo být tiše uzavřeno.

2. Pokud otevřený editor/návrhář má neuložené změny, pak zdroj přetažení by měl počkat na pokles dojít a pak požádejte uživatele o uložení nepotvrzené změny v otevřených dokumentech před zavřením okna s výzvou podobnou následující:

    ```
    ==========================================================
         One or more open documents have unsaved changes.
    Do you want to save uncommitted changes before proceeding?
                      [Yes]  [No]  [Cancel]
    ==========================================================
    ```

To dává uživateli možnost uložit nedokončenou práci před cíl vytvoří své kopie. Byla přidána nová metoda, `IVsHierarchyDropDataSource2::OnBeforeDropNotify` která umožňuje toto zpracování.

Cíl pak zkopíruje stav položky tak, jak je v úložišti (bez neuložených změn v editoru, pokud uživatel zvolil **ne).** Po dokončení kopírování cíle (v `IVsHierarchyDropDataSource::Drop`) je zdroji dána možnost dokončit část operace `IVsHierarchyDropDataSource::OnDropNotify`přesunutí odstranění (v).

Všechny editory s neuloženými změnami by měly zůstat otevřené. U těchto dokumentů s neuloženými změnami to znamená, že bude provedena kopie části operace přesunutí, ale odstraněná část bude přerušena. Ve scénáři více násobnývýběr, když uživatel zvolí **Ne**, ty dokumenty s neuložené změny by neměly být uzavřeny nebo odebrány, ale ty bez neuložených změn by měly být uzavřeny a odebrány.