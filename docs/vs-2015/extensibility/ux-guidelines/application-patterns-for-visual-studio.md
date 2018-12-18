---
title: Vzory aplikací
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ed68602-4e28-46fe-b39f-f41979b308a2
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b0deaad86e5b14bfd0dee4d73c9ceb51916231ff
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060398"
---
# <a name="application-patterns-for-visual-studio"></a>Modely aplikací pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_WindowInteractions"></a> Okno interakce

### <a name="overview"></a>Přehled
 Dva hlavní okno typy používané v sadě Visual Studio jsou editory dokumentu a okna nástrojů. Rare, ale možné, jsou velké nemodální dialogová okna. I když jsou všechny nemodální v prostředí, jaké se používají modely jsou fundamentálně odlišný způsob. Toto téma popisuje rozdíl mezi okny dokumentů, oken nástrojů a nemodální dialogová okna. Modální dialogové okno vzorce jsou popsané v [dialogů](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs).

### <a name="comparing-window-usage-patterns"></a>Porovnávání vzorů využití okna
 **Zdokumentujte windows** téměř vždy zobrazují v rámci dokumentu kontejneru. Díky tomu editor dokumentů "center fáze" uspořádat okna nástrojů doplňkové kolem.

 A **panel nástrojů** se nejčastěji zobrazí sbalený – což může být viditelný, skrytá nebo automaticky skrývaná – okno samostatné, menší proti okraji rozhraní IDE. Ale někdy jsou uvedeny v dokumentu dobře, zrušením **okno/ukotvení** vlastností v okně. Výsledkem je další místo, ale také společné rozhodnutí, jaké řešení: Při pokusu o integrované do sady Visual Studio, musíte se rozhodnout, jestli vaše funkce by měl zobrazit okno nástroje nebo okno dokumentu.

 **Nemodální dialogová okna** nejsou doporučujeme v sadě Visual Studio. Jsou do značné míry jsou – dle definice – plovoucí panely nástrojů a by měla být implementována jako takové. Nemodální dialogová okna jsou povoleny v případech, kde by příliš omezující velikost okna normální nástroj ukotven k okraji okna. Také můžou v případech, kde uživatel by pravděpodobně přesunout dialogového okna do sekundární monitorování.

 Představte si pečlivě o jaký typ kontejneru budete potřebovat. Častá rozhodnutí při použití vzoru návrhu uživatelského rozhraní jsou v následující tabulce.

||Okno dokumentu|Panel nástrojů|Nemodální dialogové okno|
|-|---------------------|-----------------|---------------------|
|**Pozice**|Vždy dobře umístěné v rámci dokumentu a ne dock kolem okraje prostředí IDE. Ho může být "dali" uvolnit odděleně od hlavního okna.|Obecně kartu ukotven kolem okraje prostředí IDE, ale může být přizpůsobené být plovoucí, automaticky skrývaná (nepřipnutých), nebo také ukotvit v rámci dokumentu.|Velké plovoucí okno odděleně od rozhraní IDE.|
|**Potvrdit modelu**|*Zpožděných potvrzení*<br /><br /> Pokud chcete uložit data v dokumentu, musí uživatel zadat příkaz soubor/uložit, uložit jako nebo Uložit vše. Okno dokumentu nemá koncept data v rámci něj se "změněných", pak potvrzené do jednoho z uložit příkazy. Při zavírání okna dokumentu, veškerý obsah jsou uložena na disk nebo ztráty.|*Okamžité potvrzení*<br /><br /> Neexistuje žádné uložit model. Inspektor okna nástrojů, které pomáhají při úpravách souboru soubor musí být otevřený v aktivního editoru nebo návrháře a editoru nebo návrháře vlastní uložit.|*Zpožděné nebo okamžité potvrzení*<br /><br /> Nejčastěji velké nemodálního dialogového okna vyžaduje akci potvrdit změny a umožňuje operace "Storno", který vrátí zpět všechny změny provedené v rámci relace dialogu.  To rozlišuje nemodální dialogové okno z panelu nástrojů v tom, že nástroj windows mají vždy modelu okamžitého potvrzení.|
|**Viditelnost**|*Otevření nebo vytvoření (soubor) a zavřít*<br /><br /> Otevření okna dokumentu se provádí prostřednictvím buď otevřít existující dokument, nebo pomocí šablony vytvoříte nový textový dokument. Neexistuje žádná "Otevřít \<konkrétní editoru >" příkazu.|*Skrytí a zobrazení*<br /><br /> Okna nástrojů jednou instancí může skrytí nebo zobrazení. Obsah a stavy v okně nástroje zachovat, jestli v zobrazení nebo skrytý. Více instancemi nástroje windows může být uzavřen stejně jako skryté. Při zavření okna nástrojů s více instancemi, obsah a stav v rámci panel nástrojů se zahodí.|*Spuštění příkazu*<br /><br /> Dialogová okna jsou spouštěny z příkazu založeného na úlohách.|
|**Instance**|*Více instancemi*<br /><br /> Několik editory je možné otevřít ve stejný čas a úpravy různé soubory, zatímco některé editory umožňují stejný soubor otevřen v editoru více než jeden (pomocí **okno > nové okno** příkaz).<br /><br /> Jeden editor může v době, (Návrhář projektu) úpravy jeden nebo více souborů.|*Jeden nebo více instance*<br /><br /> Obsah změnit odrážejí kontextu (stejně jako v prohlížeči vlastností) nebo nabízených zaměření/kontextu ostatní okna (seznam úkolů, Průzkumník řešení).<br /><br /> Okna nástrojů jednou instancí a s více instancemi by měly být přidružené aktivního okna dokumentu, pokud není k dispozici pádný důvod, proč k.|*Jednou instancí*|
|**Příklady**|**Textových editorů**, jako je například editor kódu<br /><br /> **Návrh povrchy**, jako je například Návrhář formulářů nebo povrchu modelování<br /><br /> **Ovládací prvek rozložení, podobně jako dialogová okna**, jako je například Nástroj Manifest Designer|**Průzkumníka řešení** poskytuje řešení a projekty, které jsou obsaženy v rámci řešení<br /><br /> **Průzkumníka serveru** obsahuje hierarchické zobrazení připojení serverů a dat, které uživatel vybere možnost otevření v okně. Otevření objektu z hierarchie databáze, jako je například dotazu, otevře se okno dokumentu a umožňuje uživateli upravit dotaz.<br /><br /> **Prohlížeč vlastností** zobrazí vlastnosti objektu vybraného v okně dokumentu nebo jiného panelu nástrojů. Vlastnosti se zobrazí v zobrazení hierarchického tabulky nebo v složitějšími ovládacími prvky jako dialogové okno a umožní uživateli nastavit hodnoty těchto vlastností.||

##  <a name="BKMK_ToolWindows"></a> Nástroje systému windows

### <a name="overview"></a>Přehled
 Okna nástrojů podporují uživatelova pracovní, ke které dochází v dokumentu systému windows. Jejich slouží k zobrazení hierarchie, která představuje základní kořenovým objektem, který poskytuje Visual Studio a můžete pracovat s.

 Při zvažování nové okno nástroje v integrovaném vývojovém prostředí, měli Autoři:

-   Použít příslušné úlohy existujícími okny nástrojů a ne vytvořit nové s podobnými funkcemi. Nový nástroj windows musí být vytvořené jenom Pokud nabízejí výrazně odlišné "nástroje" nebo funkce, které nelze integrovat do podobné okna, nebo to zapnutím existujícímu oknu přesouvání rozbočovači.

-   V případě potřeby v horní části okna nástroje, použijte panel standardních příkazů.

-   Bylo v souladu s vzory již existuje v jiné nástroje systému windows pro ovládací prvek prezentace a navigace klávesnicí.

-   Bylo v souladu s prezentace ovládací prvek v jiné nástroje systému windows.

-   Nástroj pro konkrétní dokumenty systém windows bude auto zobrazené, pokud je to možné, takže se zobrazí, pouze když se aktivuje nadřazený dokument.

-   Zkontrolujte, že je jejich obsah okna navigaci pomocí klávesnice (klávesy se šipkami podpory).

#### <a name="tool-window-states"></a>Stavy okno nástroje
 Okna nástrojů Visual Studio mají různé stavy, z nichž některé jsou uživatel aktivoval (jako je funkce automatického skrytí). Ostatní stavy, jako například automatické viditelné, povolit okna nástrojů ve správném kontextu se zobrazí a skryje, když nejsou potřeba. Celkem existuje pět stavů okno nástroje.

- **Ukotvit/připnuté** okna nástrojů lze připojit k libovolné čtyřech stranách oblasti dokumentu. Ikoně připínáčku se zobrazí v záhlaví okna nástrojů. Okno nástroje lze ukotvit vodorovně nebo svisle podél hrany oblasti prostředí a jiné nástroje systému windows a může také být propojeno pomocí karet.

- **Automaticky skrývaná** nepřipnuté okna nástrojů. V okně můžete snímků z pohledu na okraji oblasti dokumentu byste museli opustit na kartě (s názvem panelu nástrojů a jeho ikonu). Panel nástrojů snímky když uživatel najede myší na kartu.

- **Automaticky viditelná** okna nástrojů automaticky zobrazí při spuštění další část uživatelského rozhraní, jako je například editor, nebo získá fokus.

- **Číslo s plovoucí čárkou** mimo rozhraní IDE při najetí myší okna nástrojů. To je užitečné pro konfigurace více monitorů.

- **Dokument s kartami** panely nástrojů lze ukotvit v rámci dokumentu kontejneru. To je užitečné pro velké panel nástrojů, jako je například prohlížeč objektů, potřebujete více prostoru než ukotvení na okraji rámečku umožňuje.

  ![Nástroj pro stavy okna v sadě Visual Studio](../../extensibility/ux-guidelines/media/0702-01-toolwindowstates.png "0702 01_ToolWindowStates")

  **Stavy okno nástroje v sadě Visual Studio**

#### <a name="single-instance-and-multi-instance"></a>Jednou instancí a s více instancemi
 Okna nástrojů jsou jednou instancí nebo s více instancemi. Některá okna nástrojů jednou instancí může být přidružen k aktivního okna dokumentu, zatímco okna nástrojů s více instancemi nemusí. Okna nástrojů s více instancemi reagovat na okno okno/Nový příkaz tak, že vytvoříte novou instanci třídy okna. Následující obrázek ukazuje okno nástroje povolení příkazu nové okno při aktivním instanci okna:

 ![Panel nástrojů, příkazy v sadě Visual Studio umožňuje](../../extensibility/ux-guidelines/media/0702-02-toolwindowenablingcommand.png "0702 02_ToolWindowEnablingCommand")

 **Povolení příkazu 'Nové okno' při aktivním instance okno panelu nástrojů**

 Okna nástrojů jednou instancí můžete skrytí nebo zobrazení, zatímco okna nástrojů s více instancemi může uzavřeno, stejně jako skrytý. Všechna okna nástrojů lze ukotvit, propojeno pomocí karet, s plovoucí desetinnou čárkou nebo nastavte jako podřízeného okna (podobně jako okno dokumentu) rozhraní více dokumentů (MDI). Všechna okna nástrojů, mělo by na odpovídající okno Příkazy pro správu v nabídce okna:

 ![Příkazy pro správu v sadě Visual Studio](../../extensibility/ux-guidelines/media/0702-03-windowmanagementcontrols.png "0702 03_WindowManagementControls")

 **Příkazy pro správu v nabídce okno Visual Studio**

#### <a name="document-specific-tool-windows"></a>Okna nástrojů konkrétní dokumenty
 Některá okna nástrojů jsou navrženy pro měnit v závislosti na daný typ dokumentu. Tato okna průběžně aktualizovat tak, aby odrážely funkce lze použít na okno aktivního dokumentu v integrovaném vývojovém prostředí.

 Příklady oken nástrojů, jejichž obsah změnit tak, aby odrážely vybrané editoru jsou sady nástrojů a osnovy dokumentu. Tato okna zobrazit vodoznak, když má fokus, který neposkytuje kontext do okna editoru.

#### <a name="navigable-list-tool-windows"></a>Panely nástrojů lze procházet seznam
 Některá okna nástrojů zobrazte seznam lze procházet položky, které může uživatel zasahovat. V tomto typu okna je vždy třeba zpětné vazby pro aktuální položku v seznamu, i v případě, že v okně je neaktivní. V seznamu by měla odpovídat **GoToNextLocation** a **GoToPrevLocation** příkazy také změnou aktuálně vybrané položky v okně

 Příklady oken nástrojů lze procházet seznam: v Průzkumníku řešení a v okně Výsledky hledání.

### <a name="tool-window-types"></a>Typy oken nástrojů

#### <a name="common-tool-windows-and-their-functions"></a>Běžné nástroje systému windows a jejich funkce

|Typ|Panel nástrojů|Funkce|
|----------|-----------------|--------------|
|**hierarchie**|Průzkumník řešení|Hierarchický strom, který zobrazí seznam dokumentů obsažených v projektech, různé soubory a položky řešení. Zobrazení položek v rámci projektů je definována balíček, který vlastní typ projektu (například typy založené na odkaz, na základě directory nebo ve smíšeném režimu).|
|**hierarchie**|zobrazení tříd|Hierarchický strom, tříd a různé prvky v pracovní sadě dokumentů, nezávislá soubory sami.|
|**hierarchie**|Průzkumník serveru|Hierarchický strom, který zobrazuje všechna připojení serverů a dat v řešení.|
|**hierarchie**|Osnova dokumentu|Hierarchická struktura aktivní dokument.|
|**Mřížka**|Vlastnosti|Tabulku, která zobrazuje seznam vlastností pro vybraný objekt, spolu s výběr hodnoty upravit tyto vlastnosti.|
|**Mřížka**|Seznam úloh|Mřížka, která umožňuje uživateli vytvoření, úprava nebo odstranění úlohy a komentáře.|
|**Obsah**|Nápověda|Okno, které umožňuje uživatelům přístup k různým metodám získání nápovědy z "Jak na to?" videa k fórům MSDN.|
|**Obsah**|Dynamická nápověda|Okno nástroje, který zobrazuje odkazy na témata pro aktuální výběr nápovědy.|
|**Obsah**|prohlížeč objektů|Sada rámců dvousloupcových seznam komponent hierarchický objekt v levém podokně a objektu, vlastnosti a metody v pravém sloupci.|
|**Dialogové okno**|Najít rozšířené hledání|Dialogové okno, které mu umožní najít nebo najít a nahradit v různých souborů v rámci řešení.|
|**Jiné**|Sada nástrojů|Okno nástroje sloužící k ukládání prvků, které budou umístěny na návrhové ploše, poskytování konzistentního zdroji přetažení pro profesionální návrháře využívající všechny.|
|**Jiné**|Úvodní stránka|Uživatele portálu sady Visual Studio, s přístupem k informačním kanálům Novinky pro vývojáře, sady Visual Studio nápovědy a posledních projektů. Uživatelé můžou také vytvářet vlastní úvodní stránky zkopírováním StartPage.xaml soubor v adresáři program files "Common7\IDE\StartPages\" Visual Studio ke složce StartPages do adresáře dokumentů aplikace Visual Studio a pak buď úpravy XAML ručně nebo ho otevřít v sadě Visual Studio nebo jiného editoru kódu.|
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Automatické hodnoty||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Okamžité||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Výstup|Pokaždé, když máte textové události nebo stavu k deklaraci je možné v okně výstup.|
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Paměť||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Zarážky||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Spuštění||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Dokumenty||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Zásobník volání||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Místní hodnoty||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Hodinky||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Převod do strojového jazyka||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Zaregistruje||
|**Ladicí program:** skupiny systému windows, které jsou specifické pro úlohy ladění a monitorování aktivit|Vlákna||

##  <a name="BKMK_DocumentEditorConventions"></a> Konvence pro dokumenty editoru

### <a name="document-interactions"></a>Interakce dokumentu
 "Dokumentu a" je největší prostor v rámci rozhraní IDE a je, kde uživatel obecně se zaměřuje jejich pozornost k dokončení úloh jsou nápomocen doplňkové nástroje systému windows. Editory dokumentu představují základní jednotky práce, kterou uživatel otevře a uloží v rámci sady Visual Studio. Zachování silné představu o výběr vázané na Průzkumníka řešení nebo jiných oknech aktivní hierarchii. Uživatel by měl být odkazoval na jeden z těchto oken hierarchie a vědět, kde se dokument nachází a jeho vztah k řešení, projektu nebo jiné kořenový objekt poskytovaný balíček sady Visual Studio.

 Úpravy dokumentu vyžaduje konzistentní uživatelské prostředí. Povolit uživatelům zaměřit se na daný úkol místo na okno správy a hledání příkazů, vyberte strategii zobrazení dokumentu, která nejlíp odpovídá uživatelské úlohy pro úpravu tohoto typu dokumentu.

#### <a name="common-interactions-for-the-document-well"></a>Běžné interakce dobře dokumentu

-   Udržovat konzistentní interakce modelu společné **nový soubor** a **otevřít soubor** prostředí.

-   Související funkce do nabídky a související windows aktualizujte, když se otevře okno dokumentu.

-   Příkazy nabídky jsou odpovídajícím způsobem integrovaná v běžných nabídkách, jako **upravit**, **formátu**, a **zobrazení** nabídky. Vyžadovat značné množství specializované příkazy jsou k dispozici, mohou být vytvořeny nové nabídky který se zobrazí, pouze pokud dokument má fokus.

-   Integrovaném panelu nástrojů můžete umístit v horní části editoru. Je to vhodnější než s tím, že samostatných nástrojů, které se zobrazí mimo editor.

-   Vždy zachovat výběr v Průzkumníku řešení nebo podobné aktivní okno hierarchie.

-   Dvojitým kliknutím dokumentů v Průzkumníku řešení by provedly to stejné jako **otevřít**.

-   Pokud více než jeden editor lze použít na typ dokumentu, uživatel by měl možné přepsat nebo obnovit výchozí akce na typ daného dokumentu pomocí **otevřít v** dialogové okno tak, že kliknete pravým tlačítkem na soubor a vyberete **otevřít S** z místní nabídky.

-   Nezačleňujte průvodce v dokumentu kontejneru.

### <a name="user-expectations-for-specific-document-types"></a>Očekávání uživatele pro určité typy dokumentů
 Existuje několik různých typů základní editory dokumentu a každý má sadu interakcí, které jsou konzistentní s ostatními stejného typu.

- **Textový editor:** editor kódu, souborů protokolu

- **Návrhová plocha:** WPF forms designer, Windows forms

- **Editor dialogového okna style:** Manifest Designer Vlastnosti projektu

- **Návrhář modelů:** návrháře postupu provádění, codemap, diagram architektury, průběh

  Existují také několik typů bez editoru, které používají dobře dokumentu. Při jejich neupravujte samotných dokumentech, musí dodržovat standardní interakce pro okna dokumentu.

- **Sestavy:** sestavy IntelliTrace, technologie Hyper-V sestavě sestavy profileru

- **Řídicí panel:** centrum diagnostiky

#### <a name="text-based-editors"></a>Textové editory

-   Dokument se podílí na kartě modelu ve verzi preview, umožňuje zobrazení náhledu dokumentu bez jeho otevření.

-   Strukturu dokumentu může být reprezentován v rámci časového období doprovodný nástroj, jako je například Osnova dokumentu.

-   IntelliSense (v případě potřeby) se chovají konzistentně s dalšími editory kódu.

-   Automaticky otevíraná okna nebo usnadnění uživatelského rozhraní postupujte podle podobných styly a vzory pro existující podobným uživatelským rozhraním, jako je třeba CodeLens.

-   Zprávy týkající se stavu dokumentu se zobrazí v ovládacím prvku informačním panelu v horní části dokumentu nebo ve stavovém řádku.

-   Uživatel musí být možné přizpůsobit vzhled písma a barvy s použitím **nástroje > Možnosti** stránce sdílené písma a barvy stránky nebo jeden konkrétní do editoru.

#### <a name="design-surfaces"></a>Návrhové ploše

-   Prázdný návrháře by měl mít vodoznak na povrchu, jak začít pracovat.

-   Přepínání zobrazení mechanismy bude následovat existující vzorů, jako je například dvojitým kliknutím otevřete editor kódu nebo karty v okně dokumentu, umožní interakci s oběma podokny.

-   Přidání prvků na návrhové ploše by to udělat pomocí nástrojů, pokud není vyžadována možnost vysoce specifické nástrojů.

-   Položky na povrchu se řídí modelem konzistentní výběr.

-   Panely nástrojů vložený obsahovat konkrétní dokumenty příkazy pouze, není běžné příkazy, jako například **Uložit**.

#### <a name="dialog-style-editors"></a>Dialogové okno – vizuální styl editory

-   Rozložení ovládacích prvků by měly dodržovat konvence rozložení normální dialogového okna.

-   Karty v editoru by neměly odpovídat vzhled karty dokumentů, by měl odpovídat jedné ze dvou styly povolené vnitřní kartu.

-   Uživatelé musí být schopen komunikovat s ovládacími prvky pomocí klávesnice. buď aktivace v editoru a procházení tabulátorem přes ovládací prvky nebo pomocí standardních klávesových zkratek.

-   Návrháři používali společné uložit model. Žádné celkové uložit nebo tlačítka potvrzení musí být umístěny na povrchu, i když může být vhodné další tlačítka.

#### <a name="model-designers"></a>Návrháře modelů

-   Prázdný návrháře by měl mít vodoznak na povrchu, jak začít pracovat.

-   Přidání prvků na návrhové ploše by to udělat pomocí panelu nástrojů.

-   Položky na povrchu se řídí modelem konzistentní výběr.

-   Panely nástrojů vložený obsahovat konkrétní dokumenty příkazy pouze, není běžné příkazy, jako například **Uložit**.

-   Legenda se můžou objevit na ploše buď orientační nebo vodoznak.

-   Uživatel musí být možné přizpůsobit vzhled písma a barvy s použitím **nástroje > Možnosti** stránce sdílené písma a barvy stránky nebo jeden konkrétní do editoru.

#### <a name="reports"></a>Sestavy

-   Sestavy jsou obvykle jen informace a není součástí modelu uložit. Však mohou zahrnovat interakcí, jako například odkazy na další relevantní informace nebo oddíly, které rozbalit nebo sbalit.

-   Většina příkazů na ploše by měl být hypertextové odkazy, ne tlačítka.

-   Rozložení by zahrnout hlavičku a postupujte podle pokynů na standardní sestavy rozložení.

#### <a name="dashboards"></a>Řídicí panely

-   Řídicí panely nemají modelu interakce sami, ale sloužit jako znamená, že nabízí celou řadu dalších nástrojů.

-   Není součástí modelu uložit.

-   Uživatelé musí být schopen komunikovat s ovládacími prvky pomocí klávesnice, aktivuje se v editoru a procházíte ovládací prvky nebo pomocí standardních klávesových zkratek.

##  <a name="BKMK_Dialogs"></a> Dialogová okna

### <a name="introduction"></a>Úvod
 Dialogová okna v sadě Visual Studio by měl obvykle podporují jeden samostatná jednotka práce uživatele a potom zrušit.

 Pokud jste určili, že potřebujete dialogové okno, máte tři možnosti, v pořadí podle priority:

1. Integrate funkce do jedné sdílené dialogových oken v sadě Visual Studio.

2. Vytvořte vlastní dialogového okna pomocí vzoru v existující podobné dialogové okno.

3. Vytvořte nové dialogové okno, následující interakce a pokyny pro rozložení.

   Toto téma popisuje, jak zvolit správný dialogové okno vzoru v rámci pracovních postupů sady Visual Studio a běžné konvence pro dialogové okno návrh.

### <a name="themes"></a>Motivy
 Dialogová okna v sadě Visual Studio proveďte jeden z dva základní styly:

#### <a name="standard-unthemed"></a>Standard (unthemed)
 Většina dialogová okna jsou standardní nástroj dialogová okna a musí být unthemed. Není běžné ovládací prvky re šablony nebo pokus o vytvoření stylizované "moderní" tlačítka nebo ovládací prvky. Ovládací prvky a postupujte podle vzhled chrome [standardní pokyny pro interakci Windows Desktop pro dialogová okna](https://msdn.microsoft.com/library/windows/desktop/dn742499\(v=vs.85\).aspx).

#### <a name="themed"></a>S motivem
 Dialogová okna "podpis" specializace může použít motiv. Dialogová okna s motivem mají odlišné vzhled, který také obsahuje některé speciální interakce vzory související se stylem. Motiv dialogového okna pouze v případě, že splňuje tyto požadavky:

- Dialogové okno je běžné možnosti, které budou vidí a můžou používat často nebo mnoha uživateli (třeba **nový projekt** dialogového okna.

- Dialogové okno obsahuje prvky značky viditelného produktu (například **nastavení účtu** dialogového okna).

- Dialogové okno se zobrazí jako nedílnou součástí větší tok, který obsahuje další motivy dialogových oken (například **přidat připojenou službu** dialogového okna).

- Dialogové okno je důležitou součástí prostředí, které hrají roli strategické zvýšení úrovně nebo odlišení těchto verzí produktu.

  Při vytváření s motivem dialog, použití barev příslušné prostředí a postupujte podle správné rozložení a vzory interakcí. (Viz [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md))

### <a name="dialog-design"></a>Dialogové okno návrhu
 Dobře navržené dialogová okna vzít v úvahu následující prvky:

-   Úlohy uživatele se nepodporuje

-   Styl textu dialogového okna, jazyk a terminologie

-   Ovládací prvek výběru a pravidla týkající se uživatelského rozhraní

-   Zarovnání specifikaci a řízení rozložení vizuálu

-   Použití klávesnice

#### <a name="content-organization"></a>Uspořádání obsahu
 Zvažte rozdíly mezi těmito základní typy dialogová okna:

-   [Jednoduché dialogová okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_SimpleDialogs) prezentovat ovládacích prvků v jedné modální okno. Prezentace mohou zahrnovat odchylky vzory komplexní ovládacích prvků, včetně ovládacího prvku pro výběr pole nebo panel nástrojů.

-   [Dialogová okna na základě úrovní](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_LayeredDialogs) se používají k výběru z plochy obrazovky při každé uživatelské rozhraní se skládá z více skupin ovládacích prvků. Dialogové okno seskupení jsou "vrstvy" prostřednictvím ovládací prvky karet, ovládací prvky seznamu nebo tlačítka tak, aby uživatel může zvolit seskupení, které chcete zobrazit v kterémkoli daném okamžiku.

-   [Průvodci](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Wizards) jsou užitečné pro směruje uživatele provede Logická posloupnost kroků směrem k dokončení úlohy. Sekvenční panelů, někdy Úvod do různých pracovních postupů ("větve") závisí na zvolené v předchozí panel nabízí řadu možností.

####  <a name="BKMK_SimpleDialogs"></a> Jednoduché dialogová okna
 Dialogové okno s jednoduchou je prezentace ovládacích prvků v jedné modální okno. Tato prezentace mohou zahrnovat odchylky vzory komplexní ovládacích prvků, jako je například pole ovládacího prvku pro výběr. Jednoduché dialogová okna postupujte podle standardní Obecné rozložení, jakož i všechny konkrétní rozložení potřebné pro komplexní řízení seskupení.

 ![Jednoduché dialogového okna v sadě Visual Studio](../../extensibility/ux-guidelines/media/0704-01-createstrongnamekey.png "0704 01_CreateStrongNameKey")

 **Vytvořit klíč se silným názvem je příkladem jednoduché dialogového okna v sadě Visual Studio.**

####  <a name="BKMK_LayeredDialogs"></a> Vrstvené dialogová okna
 Vrstvené dialogová okna zahrnutí karty, řídicích panelů a vložené stromové struktury. Používají se pro maximalizaci nemovitosti, pokud existuje více skupin ovládacích prvků, které nabízí v každé uživatelské rozhraní. Seskupení jsou rozloženy do vrstev, takže uživatel může určit, které seskupení zobrazíte v daný okamžik.

 V nejjednodušší případ je mechanismus pro přepínání mezi seskupení ovládacím prvkem karta. Nejsou k dispozici několik alternativ. Podívejte se Upřednostňování pořadí a vrstvení pro výběr nejvhodnější style.

 **Nástroje > Možnosti** dialogového okna je příkladem vrstvami dialogového okna pomocí vložených stromové struktury:

 ![Vrstvené dialogového okna v sadě Visual Studio](../../extensibility/ux-guidelines/media/0704-02-toolsoptions.png "0704 02_ToolsOptions")

 **Nástroje > Možnosti je příkladem dialogové okno s vrstvami v sadě Visual Studio.**

####  <a name="BKMK_Wizards"></a> Průvodce
 Průvodců jsou užitečné pro směruje uživatele provede Logická posloupnost kroků při dokončení úkolu. Sekvenční panelů nabízí řadu možností, a uživatel musí pokračovat až do každého kroku, než budete pokračovat k dalšímu. Jakmile jsou k dispozici, výchozí hodnoty dostatečné **Dokončit** tlačítko je povolené.

 Modální průvodci se používají pro úlohy, které:

-   Obsahují větvení, pokrytím různých cest v závislosti na volbu uživatele

-   Obsahuje závislosti mezi kroky, ve kterém následné kroky jsou závislé na uživatelský vstup z předchozích kroků

-   Jsou dostatečně složité, uživatelské rozhraní by měla sloužit k vysvětlení volby, které nabízí a možné výsledky v každém kroku

-   Jsou transakční vyžaduje sadu kroků dokončit v celém rozsahu, než se změny potvrdí

### <a name="common-conventions"></a>Běžné konvence
 K zajištění optimální řešení a funkcí pomocí vaší dialogová okna, postupujte podle těchto konvence na velikost dialogového okna, pozici, standardy, konfigurace ovládacích prvků a zarovnání, uživatelského rozhraní text, záhlaví, ovládací prvek tlačítka a přístupové klíče.

 Pokyny pro specifické rozložení, naleznete v tématu [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="size"></a>Velikost
 Dialogová okna vejít dovnitř minimální rozlišení obrazovky 1024 × 768 a počáteční dialogové okno velikost nesmí překročit 900 x 700 pixelů. Dialogová okna může být umožňující změnu velikosti, ale není povinné.

 Existují dva doporučení pro dialogová okna možností změny velikosti:

1.  Minimální velikost je definovaný v dialogovém okně, který bude optimalizovat pro sada ovládacích prvků bez oříznutí a upravit tak, aby vyhovovaly přiměřené lokalizace růstu.

2.  Že ukládá velikost škálovaných uživatele pro relaci. Například pokud uživatel škáluje dialogové okno pro 150 %, pak následné spuštění dialogového okna se zobrazí na 150 %.

#### <a name="position"></a>Pozice
 Dialogová okna musí být uvedena na střed v rámci rozhraní IDE při prvním spuštění. U jiných možností změny velikosti dialogová okna, není povinné, že poslední pozice dialogové okno nastavit jako trvalý, takže se zobrazí na střed na následné spuštění. Velikost pro dialogová okna umožňující změnu velikosti, by měl nastavit jako trvalý v následné spuštění. Pro umožňující změnu velikosti dialogová okna, které jsou modální není potřeba pozice nastavit jako trvalý. Zobrazení je umístěn na střed v integrovaném vývojovém prostředí eliminuje možnost dialogového okna zobrazuje v nepředvídatelné nebo nepoužitelné pozice, pokud došlo ke změně konfigurace zobrazení uživatele. Pro nemodální dialogová okna, které lze přesunout pozici uživatele by se měl zachovat na následné spuštění, protože dialogového okna lze často jako součást rozsáhlejšího pracovního postupu.

 Při dialogová okna musíte spustit další dialogová okna, by měl nejvyšší dialogové okno kaskádovitě přenést na doprava a dolů z nadřazené položky, aby byla uživateli, na kterou se přejde na nové místo zřejmý.

#### <a name="modality"></a>Modalitě
 Probíhá modální okno znamená, že uživatelé musí dokončit nebo zrušit dialogového okna před pokračováním. Od modálních dialogových oken zablokuje uživateli hlasovou interakci s ostatními částmi prostředí, tok úkolů vaši funkci jejich použití jako opatrně. Při operaci modální je nezbytné, Visual Studio obsahuje sdílené dialogy, které můžete integrovat do vaší funkce. Pokud je nutné vytvořit nové dialogové okno, postupujte podle interakční existující dialogového okna s podobnými funkcemi.

 Když uživatelé musí provést dvě aktivity najednou, jako například **najít** a **nahradit** při zápisu nový kód, by měla být nemodální dialogové okno tak, aby uživatel lze snadno přepínat mezi nimi. Pro tento typ podporuje editor propojené úkolu, který používá Visual Studio obecně okna nástrojů.

#### <a name="control-configuration"></a>Konfigurace ovládacích prvků
 Bylo v souladu s existující konfigurace ovládacích prvků, které provést totéž v sadě Visual Studio.

#### <a name="title-bars"></a>Záhlaví

- Text v záhlaví musí odpovídat názvu příkazu, který je spouští.

- Žádná ikona by měla sloužit v záhlaví dialogového okna. V případech, kdy systém vyžaduje, aby jeden logo sady Visual Studio můžete použijte.

- Dialogová okna by neměl mít minimalizovat nebo maximalizovat tlačítka.

- Tlačítka nápovědy v záhlaví se již nepoužívají. Nepřidávejte je do nového dialogová okna. Pokud existují, by se zobrazit téma nápovědy, koncepčně relevantní pro úlohu.

  ![Záhlaví specifikace pro sadu Visual Studio](../../extensibility/ux-guidelines/media/0704-03-titlebarspecs.png "0704 03_TitleBarSpecs")

  **Specifikace obecných zásad pro záhlaví v dialogových oknech sady Visual Studio.**

#### <a name="control-buttons"></a>Ovládací prvek tlačítka
 Obecně platí **OK**/**zrušit**/**pomáhají** tlačítka by měla být uspořádány vodorovně v pravém dolním rohu dialogového okna. Alternativní svislý zásobník je povolený, pokud dialogové okno má několik tlačítek v dolní části dialogového okna, která bude představovat visual záměně se ovládací prvek tlačítka.

 ![Ovládací prvek tlačítko konfigurace v sadě Visual Studio](../../extensibility/ux-guidelines/media/0704-04-controlbuttonconfig.png "0704 04_ControlButtonConfig")

 **Přijatelné konfigurace pro ovládací prvek tlačítka v dialogových oknech sady Visual Studio**

 Dialogové okno musí obsahovat výchozí ovládací prvek tlačítko. Pokud chcete určit nejlepší příkaz, který použije jako výchozí, vyberte z následujících možností (uvedené v pořadí podle priority):

- Zvolte příkaz nejbezpečnější a nejbezpečnější jako výchozí. To znamená, že zvolíte příkaz nejpravděpodobnější zabraňují úniku dat a vyhnout se přístup k nezamýšleným systému.

- Pokud ke ztrátě dat a zabezpečení nejsou faktory, vyberte výchozí příkaz podle pohodlí. Včetně nejpravděpodobnější příkaz jako výchozí zlepší pracovního postupu uživatele, když dialogové okno podporuje často i opakované úlohy.

  Nepoužívejte trvale destruktivní akce pro výchozí příkaz. Pokud takový příkaz je k dispozici, zvolte příkaz bezpečnější místo jako výchozí.

#### <a name="access-keys"></a>Přístupové klíče
 Nepoužívejte přístupových klíčů pro **OK**/**zrušit**/**pomáhají** tlačítka. Tato tlačítka jsou namapovány na klávesových zkratek ve výchozím nastavení:

|Název tlačítka|Klávesová zkratka|
|-----------------|-----------------------|
|OK|Enter|
|Zrušit|Esc|
|Nápověda|F1|

#### <a name="imagery"></a>Obrázek
 Nepoužívejte imagí v dialogových oknech. Nepoužívejte velké ikony v dialogových oknech kladené čistě kvůli použít místo. Použití imagí pouze v případě, že jsou důležitou součástí takzvané zprávu pro uživatele, například ikon upozornění nebo stavu animace.

###  <a name="BKMK_PrioritizingAndLayering"></a> Nastavení priority a vrstvení

#### <a name="prioritizing-your-ui"></a>Nastavení priority uživatelského rozhraní
 Může být potřeba převést některé prvky uživatelského rozhraní na špici a umístěte pokročilejší chování a možnosti (včetně skrytého příkazů) do dialogových oknech. Přeneste běžně používané funkce na špici podle místa a tím, že je viditelná ve výchozím nastavení v uživatelském rozhraní se popisek s textem když se zobrazí dialogové okno.

#### <a name="layering-your-ui"></a>Vrstvení uživatelské rozhraní
 Pokud jste určili, že dialogové okno je nezbytné, ale související funkce, které chcete pro konkrétního uživatele jde nad rámec co lze zobrazit v dialogovém okně jednoduché, budete muset vrstvy uživatelské rozhraní. Nejběžnější metody vrstev, které používá sada Visual Studio jsou karty a chodbách nebo řídicí panely. V některých případech může být vhodné oblasti, které můžete rozbalit nebo sbalit. Adaptivní uživatelského rozhraní se obecně nedoporučuje v sadě Visual Studio.

 Existují výhody a nevýhody různých metod vrstvení prostřednictvím karty jako ovládací prvky uživatelského rozhraní. Prohlédněte si seznam níže Ujistěte se, že vybíráte vrstvení technika, která odpovídá vaší situaci.

##### <a name="tabbing"></a>Procházení tabulátorem

|Přepínání mechanismus|Výhody a řádném používání|Nevýhody a nesprávné použití|
|-------------------------|------------------------------------|-----------------------------------------|
|Ovládací prvek karty|Logicky seskupit stránkách dialogového okna do související sady<br /><br /> Užitečné pro méně než pět (nebo počet karet, které vyhovují v jednom řádku v dialogovém okně) stránky souvisejících ovládacích prvků v dialogovém okně<br /><br /> Karta popisků musí být krátký: jedno nebo dvě slova, které můžete snadno identifikovat obsah<br /><br /> Běžné systémový styl dialogového okna<br /><br /> Příklad: **Průzkumník souborů > Vlastnosti položek**|Vytváření krátkých popisky může být obtížné<br /><br /> Obecně neškáluje posledních pět záložek v jedné dialogového okna<br /><br /> Nevhodné, pokud máte příliš mnoho karet pro jeden řádek. Použijte alternativní vrstvení<br /><br /> Není rozšiřitelný|
|Navigace postranního panelu|Jednoduché přepínání zařízení, která může obsahovat více kategorií než tabulátory<br /><br /> Seznam bez stromové struktury kategorie (žádná hierarchie)<br /><br /> Rozšiřitelné<br /><br /> Příklad: **přizpůsobit... > přidat – příkaz**|Není vhodné využít vodorovný prostor, pokud je méně než tři skupin<br /><br /> Úkol může být lépe hodí pro rozevírací seznam|
|Ovládací prvek stromu|Umožňuje neomezený počet kategorií<br /><br /> Umožňuje seskupení a/nebo hierarchie kategorií<br /><br /> Rozšiřitelné<br /><br /> Příklad: **nástroje > Možnosti**|Silně vnořené hierarchie může způsobit nadměrné vodorovného posouvání<br /><br /> Visual Studio obsahuje overabundance stromová zobrazení|
|Průvodce|Pomáhá při dokončení úkolu a potřebnými kroky založené na úlohách, sekvenční. Průvodce představuje základní úkol a jednotlivé panely představují dílčí úkoly, které jsou nutné k provedení jedné úlohy.<br /><br /> Užitečné, pokud úloha překročí hranice uživatelského rozhraní, jako když uživatel byste jinak museli používat více editory a nástrojů systému windows k dokončení úlohy<br /><br /> Užitečné, pokud úloha vyžaduje větvení<br /><br /> Užitečné, pokud úloha obsahuje závislosti mezi kroky<br /><br /> Užitečné, pokud několik podobných úloh s jeden rozhodnutí forku lze zobrazit v jedné dialogové okno a snížit počet různých podobně jako dialogová okna.|Nevhodné pro všechny úlohy, které nevyžaduje sekvenčního pracovního postupu<br /><br /> Uživatelům se může stát přetížení a zaměňovat průvodcem s příliš mnoha kroky<br /><br /> Průvodce mají omezenou ze své podstaty plochy obrazovky|

##### <a name="hallways-or-dashboards"></a>Chodbách nebo řídicí panely
 Předsálí a řídicí panely jsou dialogová okna nebo panely, které bude sloužit jako spuštění odkazuje na další dialogová okna a windows. Dobře navržené "dále přes chodbu" okamžitě zobrazí pouze nejběžnější možnosti, příkazy a nastavení, které uživateli umožňují snadno provádět běžné úlohy. Jako dále přes chodbu skutečných poskytuje dveří pro přístup k místnosti za nimi stojí, zde méně běžné uživatelské rozhraní se shromažďují do samostatných "místnosti" (často. Další dialogová okna) související funkce, který je přístupný z hlavní dále přes chodbu.

 Můžete také uživatelské rozhraní, která nabízí všechny funkce dostupné v jedné kolekci místo refaktoring méně běžné funkce do samostatné umístění je jednoduše řídicí panel.

 ![Koncept dále přes chodbu v aplikaci Outlook](../../extensibility/ux-guidelines/media/0704-08-hallway.png "0704 08_Hallway")

 **Koncept dále přes chodbu k vystavení dalšího uživatelského rozhraní v aplikaci Outlook**

##### <a name="adaptive-ui"></a>Adaptivní uživatelského rozhraní
 Zobrazení nebo skrytí uživatelského rozhraní na základě využití nebo místním nahlášené v uživatelském prostředí je jiný způsob prezentace uživatelského rozhraní nezbytné při skrytí další části. To se nedoporučuje v sadě Visual Studio, protože algoritmy pro rozhodování o tom, kdy se má zobrazit nebo skrýt uživatelské rozhraní může být velmi obtížné a pravidla budou vždy chybné některé sady případy.

##  <a name="BKMK_Projects"></a> Projekty

### <a name="projects-in-the-solution-explorer"></a>Projekty v Průzkumníkovi řešení
 Většina projektů jsou klasifikovány jako odkaz na základě, na základě directory nebo smíšený. Všechny tři typy projektů se nepodporuje současně v Průzkumníku řešení. Kořenové uživatelské prostředí při práci s projekty probíhá v tomto okně. I když jsou uzly jiného projektu odkaz, adresáře nebo projekty ve smíšeném režimu typu, je běžný vzor interakce, které bude použito jako výchozí bod před Rozbíhající se do uživatelské specifické pro projekt vzory.

 Projekty by vždy měli:

- Kvůli podpoře možnosti Přidat projekt složek a uspořádávat obsah projektu

- Udržovat konzistentní model pro trvalost projektu

  Projekty musí také udržovat konzistentní interakce modely pro:

- Odebírání projektových položek

- Ukládání dokumentů

- Úpravy vlastností projektu

- Úprava projektu v alternativní zobrazení

- Operace přetažení myší

### <a name="drag-and-drop-interaction-model"></a>Model interakce a přetažení
 Projekty obvykle klasifikovat sami jako odkaz na základě (schopni zachovat pouze odkazy na položky projektu ve službě storage), adresářového (schopni zachovat pouze položky projektu fyzicky uložené v rámci hierarchie projektu), nebo smíšené (schopni zachovat odkazy nebo fyzické položky). Rozhraní IDE obsáhne všechny tři typy projektů současně v rámci **Průzkumníka řešení**.

 Z pohledu přetažení myší, by se měly používat následující vlastnosti pro každý typ projektu v rámci **Průzkumníka řešení**:

- **Na základě odkazu projekt:** klíčovým bodem tedy je, že projekt přetahuje kolem odkaz na položku v úložišti. Když projekt založený na odkaz funguje jako zdroj pro operace přesunutí, odstraňte pouze odkaz na položku z projektu. Položka nesmí ve skutečnosti odstraněna z pevného disku. Když projekt založený na odkaz funguje jako cíl pro operaci přesunutí (nebo kopírování), přidala odkaz na původní zdroj položky přitom si soukromou kopii položky.

- **Na základě adresář projektu:** z přetažení myší hlediska, projekt přetahuje kolem fyzické položky, místo odkazu. Když projekt založený na directory funguje jako zdroj pro operace přesunutí, by měla končit nahoru odstranění fyzické položky z pevného disku a také odebere ji z projektu. Když projekt založený na directory funguje jako cíl pro operaci přesunutí (nebo kopírování), třeba kopii položky zdroje do cílového umístění.

- **Smíšené cílový projekt:** z přetažení myší hlediska, chování tento typ projektu podle povahy položky jsou kvůli usnadnění použití vypsány buď (odkaz na položku ve službě storage) nebo přímo s příslušnou položkou. Správné chování pro odkazy a fyzického zboží jsou popsané výše.

  Kdyby existovalo pouze jednoho typu projektu v **Průzkumníka řešení**, pak by byly jednoduché operace přetažení myší. Protože každý systém projektu má možnost definovat vlastní chování přetažení myší, některé pokyny (založené na chování Průzkumníka Windows přetáhněte myší) byste měli dodržet, aby předvídatelné uživatelské prostředí:

- Verzí bez úprav přetáhnout v operaci **Průzkumníka řešení** (když Ctrl ani posunutí klíče jsou uložené) by mělo vrátit operace přesunu.

- Operaci přetažení SHIFT vrátit také operace přesunu.

- Operaci přetažení CTRL by měl mít za následek operace kopírování.

- Projekt na základě odkazu a smíšené systémů podporuje pojem přidává odkaz (nebo odkaz) k položce zdroje. Pokud tyto projekty se cíl operace přetažení myší (při **Ctrl + Shift** se nachází mimo provoz), mělo by být výsledkem odkaz na položku přidávanou do projektu

  Ne všechny operace přetažení myší jsou rozumné kombinací odkaz založen na základě directory projekty a smíšené. Zejména je problematické předstírají, že umožňuje operace přesunu mezi zdrojovým adresář projektu a odkaz na základě cílový projekt, protože zdrojový projekt na základě directory bude muset odstranit položky zdroje po dokončení přesunutí. Cílový odkaz na základě projekt pak skončili byste s odkazem na odstraněnou položku.

  Také je zavádějící předstírají, že operace kopírování mezi těmito typy projektů povolit, protože cílový projekt na základě reference by neměla provést nezávislé kopie položky zdroje. Podobně Ctrl + Shift přetažením na základě directory cílový projekt by neměl být povolená, protože nelze trvale uložit odkazů projektu založeného na adresář. V případech, kdy se nepodporuje operace přetažení myší integrovaném vývojovém prostředí by měl zakázat rozevírací nabídku a uživateli se bez kurzoru (viz následující tabulka ukazatele).

  Přetáhněte myší chování správně implementovat, zdrojový projekt přetahování potřebuje ke komunikaci jejich povaze (například je odkaz nebo adresářového?) na cílový projekt. Tyto informace je indikován formátu schránky se nabízí ve zdroji. Jako zdroj přetažení (nebo operace kopírování schránky) by měl nabídnout projektu buď **CF_VSREFPROJECTITEM**S nebo **CF_VSSTGPROJECTITEMS** v uvedeném pořadí, v závislosti na tom, jestli je projekt na základě odkazu nebo na základě directory. Obě tyto formáty mají stejný datový obsah, který je podobný Windows **CF_HDROP** naformátovat s tím rozdílem, že jsou seznamy řetězců názvů souborů, namísto double -**NULL** ukončena seznam  **Projref** řetězce (vrácená **IVsSolution::GetProjrefOfItem** nebo **:: GetProjrefOfProject** podle potřeby).

  Jako cíl přetažení (nebo operaci schránky vložit) projektu by měl přijmout **CF_VSREFPROJECTITEMS** a **CF_VSSTGPROJECTITEMS**, když se liší přesné zpracování operace přetažení myší v závislosti na povaze cílový projekt a projekt zdroje. Zdrojový projekt deklaruje jejich povaze tak, zda nabízí **CF_VSREFPROJECTITEMS** nebo **CF_VSSTGPROJECTITEMS**. Cíl rozevírací rozumí vlastní povahy a proto má dostatek informací pro rozhodování, zda přesunutí, kopírování nebo odkaz je třeba provést. Uživatel také upraví, kterou operaci přetažení myší by měl provádět klávesy Ctrl, Shift, nebo jak kláves Ctrl a Shift. Je důležité pro cíl přetažení správně označující, jaké operace se provede předem v jeho **DragEnter** a **DragOver** metody. **Průzkumníka řešení** automaticky určí, zda zdrojového i cílového projektu jsou stejném projektu.

  Přetažení položek projektu napříč instancemi sady Visual Studio (například z jedné instance devenv.exe do jiného) konkrétně není podporován. **Průzkumníka řešení** také přímo to zakáže.

  Uživatel by měl vždy být schopní určit efekt operace přetažení myší výběru nějaké položky, přetažením do cílového umístění a sledování, které z následujících ukazatele myši se nachází před vyřadit položku:

|Ukazatele myši|Příkaz|Popis|
|-------------------|-------------|-----------------|
|![Myš ikonu "žádné přímé"](../../extensibility/ux-guidelines/media/0706-01-mousenodrop.png "0706 01_MouseNoDrop")|Žádné přímé|Položku nelze vyřadit do zadaného umístění.|
|![Ikona "kopie" myši](../../extensibility/ux-guidelines/media/0706-02-mousecopy.png "0706 02_MouseCopy")|Kopírovat|Položka bude zkopírována do cílového umístění.|
|!["Pohybu myši" ikonu](../../extensibility/ux-guidelines/media/0706-03-mousemove.png "0706 03_MouseMove")|Přesunutí|Položka se přesunou do cílového umístění.|
|![Ikona "Přidat odkaz" myši](../../extensibility/ux-guidelines/media/0706-04-mouseaddref.png "0706 04_MouseAddRef")|Přidat odkaz|Odkaz na vybranou položku se přidají do cílového umístění.|

#### <a name="reference-based-projects"></a>Projekty založené na odkaz
 Následující tabulka shrnuje přetažení myší (a také Vyjmout/Kopírovat/vložit) operace, které je třeba provést podle povahy zdroj položky a modifikátor klíče z důvodu projekty založené na odkazovaný cíl:

|||Zdrojová položka: / odkazu|Zdrojová položka: fyzického zboží nebo systém souborů (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Žádné modifikátor|Akce|Přesunutí|Odkaz|
|Žádné modifikátor|Cíl|Přidá odkaz na původní položky|Přidá odkaz na původní položky|
|Žádné modifikátor|Zdroj|Odstraní odkaz na původní položky|Zachová původní položky|
|Žádné modifikátor|Výsledek|**DROPEFFECT_MOVE** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**DROPEFFECT_LINK** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|SHIFT + přetažení|Akce|Přesunutí|Žádné přímé|
|SHIFT + přetažení|Cíl|Přidá odkaz na původní položky|Žádné přímé|
|SHIFT + přetažení|Zdroj|Odstraní odkaz na původní položky|Žádné přímé|
|SHIFT + přetažení|Výsledek|**DROPEFFECT_MOVE** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|Žádné přímé|
|CTRL + přetažení|Akce|Kopírovat|Žádné přímé|
|CTRL + přetažení|Cíl|Přidá odkaz na původní položky|Žádné přímé|
|CTRL + přetažení|Zdroj|Uchovává odkaz na původní položky|Žádné přímé|
|CTRL + přetažení|Výsledek|**DROPEFFECT_COPY** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|Žádné přímé|
|Ctrl + Shift + přetažení|Akce|Odkaz|Odkaz|
|Ctrl + Shift + přetažení|Cíl|Přidá odkaz na původní položky|Přidá odkaz na původní položky|
|Ctrl + Shift + přetažení|Zdroj|Uchovává odkaz na původní položky|Zachová původní položky|
|Ctrl + Shift + přetažení|Výsledek|**DROPEFFECT_LINK** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**DROPEFFECT_LINK** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|Ctrl + Shift + přetažení|Poznámka|Stejné jako chování a přetahování klávesové zkratky v Průzkumníku Windows.||
|Vyjímání a vkládání|Akce|Přesunutí|Odkaz|
|Vyjímání a vkládání|Cíl|Přidá odkaz na původní položky|Přidá odkaz na původní položky|
|Vyjímání a vkládání|Zdroj|Uchovává odkaz na původní položky|Zachová původní položky|
|Vyjímání a vkládání|Výsledek|Položka zůstane v původním umístění v úložišti|Položka zůstane v původním umístění v úložišti|
|Kopírování a vkládání|Akce|Kopírovat|Odkaz|
|Kopírování a vkládání|Zdroj|Přidá odkaz na původní položky|Přidá odkaz na původní položky|
|Kopírování a vkládání|Výsledek|Uchovává odkaz na původní položky|Zachová původní položky|
|Kopírování a vkládání|Akce|Položka zůstane v původním umístění v úložišti|Položka zůstane v původním umístění v úložišti|

#### <a name="directory-based-projects"></a>Projekty založené na adresáři
 Následující tabulka shrnuje přetažení myší (a také Vyjmout/Kopírovat/vložit) operace, které je třeba provést podle povahy zdroj položky a modifikátor klíče z důvodu adresářového cílové projekty:

|||Zdrojová položka: / odkazu|Zdrojová položka: fyzického zboží nebo systém souborů (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Žádné modifikátor|Akce|Přesunutí|Přesunutí|
|Žádné modifikátor|Cíl|Kopie položky na cílovém umístění|Kopie položky na cílovém umístění|
|Žádné modifikátor|Zdroj|Odstraní odkaz na původní položky|Odstraní odkaz na původní položky|
|Žádné modifikátor|Výsledek|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|SHIFT + přetažení|Akce|Přesunutí|Přesunutí|
|SHIFT + přetažení|Cíl|Kopie položky na cílovém umístění|Kopie položky na cílovém umístění|
|SHIFT + přetažení|Zdroj|Odstraní odkaz na původní položky|Odstraní položku z původního umístění|
|SHIFT + přetažení|Výsledek|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|CTRL + přetažení|Akce|Kopírovat|Kopírovat|
|CTRL + přetažení|Cíl|Kopie položky na cílovém umístění|Kopie položky na cílovém umístění|
|CTRL + přetažení|Zdroj|Uchovává odkaz na původní položky|Uchovává odkaz na původní položky|
|CTRL + přetažení|Výsledek|**KOPÍROVÁNÍ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**KOPÍROVÁNÍ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|Ctrl + Shift + přetažení||Žádné přímé|Žádné přímé|
|Vyjímání a vkládání|Akce|Přesunutí|Přesunutí|
|Vyjímání a vkládání|Cíl|Kopie položky na cílovém umístění|Kopie položky na cílovém umístění|
|Vyjímání a vkládání|Zdroj|Odstraní odkaz na původní položky|Odstraní položku z původního umístění|
|Vyjímání a vkládání|Výsledek|Položka zůstane v původním umístění v úložišti|Položka odstraněna z původního umístění ve službě storage|
|Kopírování a vkládání|Akce|Kopírovat|Kopírovat|
|Kopírování a vkládání|Cíl|Přidá odkaz na původní položky|Kopie položky na cílovém umístění|
|Kopírování a vkládání|Zdroj|Zachová původní položky|Zachová původní položky|
|Kopírování a vkládání|Výsledek|Položka zůstane v původním umístění v úložišti|Položka zůstane v původním umístění in úložiště|

#### <a name="mixed-target-projects"></a>Smíšené cílové projekty
 Následující tabulka shrnuje přetažení myší (a také Vyjmout/Kopírovat/vložit) operace, které je třeba provést podle povahy zdroj položky a modifikátor klíče z důvodu smíšené cílové projekty:

|||Zdrojová položka: / odkazu|Zdrojová položka: fyzického zboží nebo systém souborů (CF_HDROP)|
|-|-|----------------------------------|-------------------------------------------------------------|
|Žádné modifikátor|Akce|Přesunutí|Přesunutí|
|Žádné modifikátor|Cíl|Přidá odkaz na původní položky|Kopie položky na cílovém umístění|
|Žádné modifikátor|Zdroj|Odstraní odkaz na původní položky|Odstraní odkaz na původní položky|
|Žádné modifikátor|Výsledek|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a z původního umístění v úložišti se odstraní položka|
|SHIFT + přetažení|Akce|Přesunutí|Přesunutí|
|SHIFT + přetažení|Cíl|Přidá odkaz na původní položky|Kopie položky na cílovém umístění|
|SHIFT + přetažení|Zdroj|Odstraní odkaz na původní položky|Odstraní položku z původního umístění|
|SHIFT + přetažení|Výsledek|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**Přesunout DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a z původního umístění v úložišti se odstraní položka|
|CTRL + přetažení|Akce|Kopírovat|Kopírovat|
|CTRL + přetažení|Cíl|Přidá odkaz na původní položky|Kopie položky na cílovém umístění|
|CTRL + přetažení|Zdroj|Uchovává odkaz na původní položky|Zachová původní položky|
|CTRL + přetažení|Výsledek|**KOPÍROVÁNÍ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**KOPÍROVÁNÍ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|Ctrl + Shift + přetažení|Akce|Odkaz|Odkaz|
|Ctrl + Shift + přetažení|Cíl|Přidá odkaz na původní položky|Přidá odkaz na původní zdroj položky|
|Ctrl + Shift + přetažení|Zdroj|Uchovává odkaz na původní položky|Zachová původní položky|
|Ctrl + Shift + přetažení|Výsledek|**ODKAZ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|**ODKAZ DROPEFFECT_** se vrátí jako akce z **:: vyřadit** a položka zůstane v původním umístění v úložišti|
|Vyjímání a vkládání|Akce|Přesunutí|Přesunutí|
|Vyjímání a vkládání|Cíl|Kopie položky na cílovém umístění|Kopie položky na cílovém umístění|
|Vyjímání a vkládání|Zdroj|Odstraní odkaz na původní položky|Odstraní položku z původního umístění|
|Vyjímání a vkládání|Výsledek|Položka zůstane v původním umístění v úložišti|Položka odstraněna z původního umístění ve službě storage|
|Kopírování a vkládání|Akce|Kopírovat|Kopírovat|
|Kopírování a vkládání|Cíl|Přidá odkaz na původní položky|Kopie položky na cílovém umístění|
|Kopírování a vkládání|Zdroj|Zachová původní položky|Zachová původní položky|
|Kopírování a vkládání|Výsledek|Položka zůstane v původním umístění v úložišti|Položka zůstane v původním umístění v úložišti|

 Tyto podrobnosti brát v úvahu při implementaci přetahování **Průzkumníka řešení**:

- Návrh pro více scénářů výběr.

- Názvy souborů (úplná cesta) musí být jedinečný mezi cílový projekt nebo by se nemělo povolit rozevírací nabídku.

- Názvy složek musí být jedinečné (malá a velká písmena) na úrovni, se vyřazuje.

- Existují rozdíly v chování mezi soubory, které jsou v době (není uvedeno ve výše uvedené scénáře) přetáhněte otevřeno nebo Uzavřeno.

- Soubory nejvyšší úrovně se chovají trochu jinak než soubory ve složkách.

  Dalším problémem je potřeba vědět je způsob zpracování operací přesunu u položek, které se mají otevřít návrháři nebo editoru. Chování je očekávané následujícím způsobem (to platí pro všechny typy projektů):

1. Je-li otevřít Návrhář/editor nemá žádné neuložené změny, pak v okně editoru nebo návrháře je třeba tiše zavřít.

2. Je-li otevřít Návrhář/editor má neuložené změny, zdroj přetažení by měla počkejte seznamu a poté požádat uživatele, aby uložit nepotvrzené změny v otevřených dokumentech před zavřením okna s výzvou podobný následujícímu :

   ```
   ==========================================================
        One or more open documents have unsaved changes.
   Do you want to save uncommitted changes before proceeding?
                     [Yes]  [No]  [Cancel]
   ==========================================================
   ```

   To umožňuje uživateli příležitost k uložení probíhající práci, než cílový vytváří jeho kopie. Nová metoda **IVsHierarchyDropDataSource2::OnBeforeDropNotify** se přidala pro povolení tohoto zpracování.

   Cíl pak zkopíruje stav položky je ve službě storage (bez zahrnutí neuložené změny v editoru, pokud uživatel vybral **ne**). Po dokončení jeho kopírování cílem (v **IVsHierarchyDropDataSource::Drop**), zdroj je příležitost k dokončení odstranění část přesunutím (v **IVsHierarchyDropDataSource::O nDropNotify**).

   Žádné editoru s neuloženými změnami by měl být ponechány otevřené. Pro tyto dokumenty s neuloženými změnami to znamená, že se provede kopírování část v provádění operace přesunutí, ale část delete se přeruší. Ve více výběru scénáře, když uživatel vybere **ne**, by neměly být uzavřeny nebo odebrat tyto dokumenty s neuloženými změnami, ale bez neuložené změny by měla zavřít a odebrat.
