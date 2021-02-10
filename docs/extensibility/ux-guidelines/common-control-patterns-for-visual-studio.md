---
title: Běžné vzory ovládacích prvků pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak běžné ovládací prvky sady Visual Studio následují podle pokynů pro interakci s desktopy pro Windows a o speciálních situacích, které tyto pokyny rozšiřují
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ab8f04ff885f4b57d24cb3bc0eb449859fca6271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952184"
---
# <a name="common-control-patterns-for-visual-studio"></a>Vzory běžných ovládacích prvků pro Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Běžné ovládací prvky

### <a name="overview"></a>Přehled
Běžné ovládací prvky tvoří většinu uživatelského rozhraní v aplikaci Visual Studio. Nejběžnější ovládací prvky používané v rozhraní sady Visual Studio by měly dodržovat [pokyny pro interakci s plochou pro Windows](/windows/desktop/uxguide/controls). Toto téma je specifické pro Visual Studio a popisuje zvláštní situace nebo podrobnosti, které rozšiřují tyto pokyny pro Windows.

#### <a name="common-controls-in-this-topic"></a>Běžné ovládací prvky v tomto tématu

- [Posuvníky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Vstupní pole](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Pole se seznamem a rozevírací seznamy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Zaškrtávací políčka](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Přepínače](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Skupinové rámečky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Textové ovládací prvky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Stromová zobrazení](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Vizuální styl
První věc, kterou je třeba vzít v úvahu při určení stylu, je, zda budou ovládací prvky použity v uživatelském rozhraní motivů. Ovládací prvky ve standardním uživatelském rozhraní jsou netematické uživatelské rozhraní a musí dodržovat [normální styl desktopu Windows](/windows/desktop/uxguide/controls), což znamená, že nejsou znovu šablonované a měly by se zobrazit ve výchozím vzhledu ovládacího prvku.

- **Dialogová okna standardní (nástroj):** ne motiv. Nevytvářejte znovu šablonu. Použijte výchozí hodnoty základního stylu ovládacího prvku.

- Okna **nástrojů, editory dokumentů, návrhové plochy a dialogy s motivy:** Použijte specializovaný vzhled motivu pomocí barevné služby.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Posuvníky
 Pokud se posuvníky nerozšiřují s informacemi o obsahu, jako v editoru kódu, by se měly pořídit [běžné vzory interakce pro posuvníky Windows](/windows/desktop/Controls/about-scroll-bars) .

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Vstupní pole
 V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro textová pole](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Vizuální styl

- Vstupní pole by se neměla stylovat v dialogových oknech nástrojů. Pro ovládací prvek použijte vnitřní základní styl.

- Vstupní pole motivu by se měla používat jenom v dialogových oknech a oknech motivů.

#### <a name="specialized-interactions"></a>Specializované interakce

- Pole jen pro čtení budou mít šedé (zakázané) pozadí, ale výchozí (aktivní) popředí.

- Požadovaná pole by měla být **\<Required>** v rámci těchto mezí. Barvy pozadí byste neměli měnit s výjimkou případů ve vzácných situacích.

- Ověření chyby: viz [oznámení a průběh pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Vstupní pole by měla být velikost, aby se vešla na obsah, a ne na šířku okna, ve kterém jsou zobrazené, ani libovolně odpovídat délce dlouhého pole, jako je třeba cesta. Délka může být náznakem uživatele s omezením, kolik znaků je v poli povoleno.

     ![Nesprávná délka vstupního pole: je pravděpodobné, že název bude dlouhý.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 – 01_IncorrectInputFieldControl")<br />Nesprávná délka vstupního pole: je pravděpodobné, že název bude dlouhý.

     ![Správná délka vstupního pole: vstupní pole je vhodnou šířkou pro očekávaný obsah.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 – 02_CorrectInputFieldControl")<br />Správná délka vstupního pole: vstupní pole je vhodnou šířkou pro očekávaný obsah.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Pole se seznamem a rozevírací seznamy
V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro rozevírací seznamy a pole se seznamem](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neprovádějte znovu šablonu ovládacího prvku. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní motivů se pole se seznamem a rozevírací seznamy řídí standardními pro ovládací prvky.

#### <a name="layout"></a>Layout
Pole se seznamem a rozevírací seznamy by měly být velikosti, aby odpovídaly šířce okna, ve kterém jsou zobrazeny, ani libovolně odpovídat délce dlouhého pole, jako je například cesta.

![Nesprávné: Šířka rozevíracího seznamu je pro obsah, který se zobrazí, moc dlouhá.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 – 03_IncorrectDropDownLayout")<br />Nesprávné: Šířka rozevíracího seznamu je pro obsah, který se zobrazí, moc dlouhá.

![Správně: rozevírací seznam má velikost, aby bylo možné růst překladu, ale ne zbytečně dlouho.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 – 04_CorrectDropDownLayout")<br />Správně: rozevírací seznam má velikost, aby bylo možné růst překladu, ale ne zbytečně dlouho.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Zaškrtávací políčka
V případě typických chování interakce postupujte podle [pokynů pro plochu Windows pro instalaci zaškrtávacích políček](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neprovádějte znovu šablonu ovládacího prvku. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní s motivem se zaškrtávací políčka dodržujte standardní pro ovládací prvky.

#### <a name="specialized-interactions"></a>Specializované interakce

- Interakce se zaškrtávacím políčkem nesmí nikdy odložit dialog ani přejít do jiné oblasti.

- Zaškrtávací políčka zarovnejte se směrným plánem prvního řádku textu.

     ![Nesprávné: zaškrtávací políčko je na textu zarovnané na střed.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 – 05_IncorrectCheckBoxAlign")<br />Nesprávné: zaškrtávací políčko je na textu zarovnané na střed.

     ![Správné: zaškrtávací políčko je zarovnáno s prvním řádkem textu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 – 06_CorrectCheckBoxAlign")<br />Správné: zaškrtávací políčko je zarovnáno s prvním řádkem textu.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Přepínače
V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro přepínače](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Vizuální styl
V dialogových oknech nástrojů nepoužívejte přepínací tlačítka. Pro ovládací prvek použijte vnitřní základní styl.

#### <a name="specialized-interactions"></a>Specializované interakce
Není nutné používat skupinový rámeček k uzavření možností přepínačů, pokud nepotřebujete zachovat rozlišení skupiny v těsném rozložení.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Skupinové rámečky
V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro skupiny](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Vizuální styl
V dialogových oknech nástroje neseskupujte styly. Pro ovládací prvek použijte vnitřní základní styl.

#### <a name="layout"></a>Layout

- Není nutné používat skupinový rámeček k uzavření možností přepínačů, pokud nepotřebujete zachovat rozlišení skupiny v těsném rozložení.

- Nikdy nepoužívejte skupinový rámeček pro jeden ovládací prvek.

- Někdy je přijatelné použít místo kontejneru rámce skupiny horizontální pravidlo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Textové ovládací prvky

### <a name="static-text-fields"></a>Statická textová pole

Statické textové pole prezentuje informace jen pro čtení a uživatel ho nemůže vybrat. Nepoužívejte ho pro libovolný text, který uživatel může chtít zkopírovat do schránky. Statický text jen pro čtení se ale může změnit, aby odrážel změnu stavu. V následujícím příkladu se změní název výstupního statického textu v informační skupině tak, aby odrážel všechny změny provedené v textovém poli kořenového oboru názvů nad ním.

Existují dva způsoby, jak zobrazit statické textové informace.

Statický text může být vlastní v dialogu bez jakéhokoli zahrnutí, pokud nedochází ke konfliktu seskupení. Rozhodněte, zda jsou nadbytečné řádky pole skutečně nezbytné. Příkladem je zobrazení cesty k adresáři v rámci oddílu vytvořeného řádkem skupiny, jak je znázorněno níže:

![Statické textové informace v ovládacích prvcích textu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Statické textové informace v ovládacích prvcích textu

V dialogovém okně, kde existují jiné seskupené oblasti a informace o jejich omezení, a když může být oddíl skrytý nebo zobrazený (jako v podokně popis **okno Vlastnosti** ) nebo pokud chcete být konzistentní s podobným uživatelským rozhraním, umístěte statický text do pole. Toto skupinové pole by mělo být jediné pravidlo a mělo by se vybarvit `ButtonShadow` :

![Statický text v okno Vlastnosti](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statický text v okno Vlastnosti

### <a name="read-only-text-box"></a>Textové pole jen pro čtení

To umožňuje uživateli vybrat text v poli, ale nemůže ho upravovat. Tato textová pole jsou ohraničena normálním 3D hrotem s `ButtonShadow` výplní.

Textové pole může být aktivní (upravitelný), když uživatel změní přidružený ovládací prvek, například zaškrtnutí nebo zrušení zaškrtnutí políčka nebo výběr nebo zrušení výběru přepínacího tlačítka. Například na stránce **&gt; Možnosti nástrojů** zobrazené níže se bude textové pole **domovské stránky** aktivní, když není zaškrtnuto políčko **použít výchozí** .

![Textové pole jen pro čtení, které zobrazuje neaktivní a aktivní stavy](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Textové pole jen pro čtení, které zobrazuje neaktivní a aktivní stavy

### <a name="using-text-in-dialogs"></a>Používání textu v dialogových oknech

Klíčové pokyny pro text v dialogových oknech:

- Popisky pro textová pole, seznamy a rámečky v nezobrazených dialogových oknech začínají příkazem, mají počáteční kapitál jenom na prvním slově a končí dvojtečkou.

    > Ovládací prvky textu v dialogových oknech se řídí [pokyny pro desktopové prostředí systému Windows](/windows/desktop/uxguide/top-violations) a neobsahují interpunkci s výjimkou otazníků v odkazech Nápověda.

- Popisky pro zaškrtávací políčka a tlačítka začínají na začátku příkazu, počátečního kapitálu jenom na prvním slově a nemají žádnou koncovou interpunkci.

- Popisky tlačítek, nabídek, položek nabídek a karet mají počáteční velká písmena pro každé slovo (případ nadpisu).

- Terminologie popisků by měla být v souladu s podobnými popisky v jiných dialogových oknech.

- Pokud je to možné, je nutné, aby autor nebo editor napsal nebo schválil text před tím, než je vývojář pro implementaci.

- Všechny ovládací prvky by měly mít popisky s výjimkou zvláštních okolností, kdy je tabulátory dostatečné.
V případě potřeby použijte text nápovědy.

### <a name="helper-text"></a>Text nápovědy

Tato dialogová okna vám pomůžou uživateli pochopit účel dialogu nebo určit, kterou akci chcete provést. Pomocný text by měl být použit pouze v případě potřeby, aby nedocházelo k jednoduchým dialogům. Dvě varianty textu nápovědy jsou dialog a vodotisk.

Řiďte se běžnými umístěními pro pomocný text a vybírejte v úvodu do nových oblastí. Obvyklé scénáře pro pomocný text:

- Text nápovědy v dialogových oknech, který poskytuje další směr pro interakci se složitým dialogem.

- Text vodoznaku ve prázdných oknech nástrojů nebo dialogových oknech pro vysvětlení, proč není obsah viditelný

- Podokno popisu, podobně jako v dolní části **okno Vlastnosti**.

- Text vodoznaku v prázdném editoru, který vysvětluje, jakou akci by měl uživatel trvat, než začne.

### <a name="dialog-helper-text"></a>Pomocný text dialogového okna

Návrhář zkušeností uživatelů může pomoci určit, kdy je text pomocníka vhodný. Návrhář může definovat, kde se zobrazí text pomocníka i jeho obecný obsah. Uživatelská pomoc může zapisovat a upravovat skutečný text.

### <a name="watermarks"></a>Vodoznaky

Dialogová okna využívají mírně odlišná pravidla pro vodoznak. Vzhledem k tomu, že se dialogové okno může zobrazit jako zaneprázdněný mnoha prvky uživatelského rozhraní (popisky, text nápovědy, tlačítka a další ovládací prvky kontejneru s textem), zejména když se zobrazí černě, jsou vodoznaky lépe v tmavé šedé (VSColor: `ButtonShadow` ). Obvykle se vodoznak zobrazuje uvnitř ovládacího prvku, jako je například pole seznamu s bílým pozadím (VSColor: `Window` ).

- Text se zobrazí tmavě šedá (VSColor: `ButtonShadow` ). Pokud se ale vodoznak zobrazuje na středním šedém nebo na pozadí (VSColor: `ButtonFace` ) a je obavy o jeho čitelnost, Projděte si černý text (VSColor: `WindowText` ).

- Vodoznaky je možné zarovnat na střed nebo Zarovnat vlevo. Použijte pravidla pro standardní návrh při rozhodování o zarovnání. Meze nelze vybrat na pozadí.

![Příklad textu vodoznaku](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Příklad textu vodoznaku

### <a name="context-specific-dynamic-text"></a>Konkrétní kontextový (dynamický) text

Dynamický text lze v dialogovém okně nebo v nemodálním uživatelském rozhraní použít jedním ze dvou způsobů: buď jako dynamický popisek, nebo jako dynamický obsah.

- Dynamický popisek: běžné použití dynamického textu je v popisných panelech, které nabízí další informace pro vybranou položku, například v dialogovém okně, které obsahuje seznam prvků a vlastností pro tyto prvky zobrazené v mřížce vpravo. Popisek pro mřížku vlastností může být dynamický, takže když je na levé straně vybraná položka, mřížka vpravo zobrazuje informace pro tuto konkrétní položku.

- Dynamický text: může být užitečný v případech, kdy potřebujete zobrazovat konkrétní informace a ne Obecné informace tímto způsobem, ale měli byste se přitom starat o nenadměrné využití.

Pokud chcete, aby uživatelé měli možnost Kopírovat informace, dynamický text by měl být v textovém poli jen pro čtení.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Tlačítka a hypertextové odkazy

### <a name="overview"></a>Přehled
Tlačítka a ovládací prvky odkazů (hypertextové odkazy) by se měly řídit [základními pokyny pro stolní počítače s Windows na základě odkazů](/windows/desktop/uxguide/ctrl-links) na použití, určení velikosti a mezer.

### <a name="choosing-between-buttons-and-links"></a>Výběr mezi tlačítky a odkazy
Pro akce a Hypervazby se tradičně použila tlačítka pro navigaci. Tlačítka mohou být použita ve všech případech, ale role odkazů byla v aplikaci Visual Studio rozbalena, takže tlačítka a odkazy jsou v některých podmínkách lépe zaměnitelné.

Kdy použít příkazová tlačítka:

- Primární příkazy

- Zobrazení oken používaných ke shromáždění vstupu nebo výběru, i když se jedná o sekundární příkazy

- Destruktivní nebo nevratné akce

- Tlačítka závazku v rámci průvodců a toků stránek

Nepoužívejte příkazová tlačítka v oknech nástrojů, nebo pokud potřebujete více než dvě slova pro popisek. Odkazy mohou mít delší popisky.

 Kdy použít odkazy:

- Navigace do jiného okna, dokumentu nebo webové stránky

- Situace, které vyžadují delší označení nebo krátkou větu k popisu záměru akce

- Těsné mezery, kde by tlačítko zahlceno uživatelským rozhraním za předpokladu, že akce není destruktivní nebo nevratná

- Zrušení zvýraznění sekundárních příkazů v situacích, kdy existuje mnoho příkazů

#### <a name="examples"></a>Příklady
![Odkazy na příkazy použité na informačním panelu po stavové zprávě](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 – 01_CommandLinkInfobar")<br />Odkazy na příkazy použité na informačním panelu po stavové zprávě

![Odkazy používané v překryvném okně CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 – 02_LinksInCodeLens")<br />Odkazy používané v překryvném okně CodeLens

![Odkazy používané pro sekundární příkazy, ve kterých by tlačítka mohla mít větší pozornost.](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 – 03_LinksAsSecondaryCommands")<br />Odkazy používané pro sekundární příkazy, ve kterých by tlačítka mohla mít větší pozornost.

### <a name="common-buttons"></a>Společná tlačítka

#### <a name="text"></a>Text
Postupujte podle pokynů pro psaní v [textu uživatelského rozhraní a terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Vizuální styl

##### <a name="standard-unthemed"></a>Standardní (neexistují)
Většina tlačítek v aplikaci Visual Studio se zobrazí v dialogových oknech nástroje a neměla by být ve stylu. Měly by odrážet standardní vzhled tlačítek podle operačního systému.

##### <a name="themed"></a>S motivem
V některých případech mohou být tlačítka použita v uživatelském rozhraní se stylem a tato tlačítka musí být vhodně nastavena. Informace o ovládacích prvcích tematických prvků naleznete v [dialogových oknech](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Speciální tlačítka

#### <a name="browse-buttons"></a>Procházet... tlačítka
**[Procházet...]** tlačítka se používají v Gridech, dialogových oknech a oknech nástrojů a jiných nemodálních prvcích uživatelského rozhraní. Zobrazují výběr, který pomáhá uživateli při naplňování hodnoty do ovládacího prvku. Toto tlačítko má dvě varianty, dlouhé a krátké.

![Tlačítko dlouhého [Procházet...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 – 04_BrowseLong")<br />Tlačítko dlouhého [Procházet...]

![Tlačítko krátkého znaku [...] jen pro tři tečky](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 – 05_BrowseShort")<br />Tlačítko krátkého znaku [...] jen pro tři tečky

Kdy použít krátké tlačítko se třemi tečkami:

- V případě, že v dialogovém okně existuje více než jedno dlouhé tlačítko **[Procházet...]** , například když několik polí umožňuje procházení. Použijte tlačítko short **[...]** pro každý, aby nedocházelo k odepření přístupových klíčů, které byly vytvořeny v této situaci (**&procházet** a **B&ocházet** ve stejném dialogovém okně).

- V těsném dialogovém okně nebo v případě, že není přijatelné místo pro vložení dlouhého tlačítka.

- Pokud se tlačítko zobrazí v ovládacím prvku mřížky.

Pokyny pro použití tlačítka:

- Nepoužívejte přístupový klíč. Chcete-li k němu přistupovat pomocí klávesnice, musí uživatel z sousedícího ovládacího prvku kartu. Ujistěte se, že je pořadí karet tak, že jakékoli tlačítko pro procházení spadá hned za pole, které bude vyplňovat. Nikdy nepoužívejte podtržítko pod první tečkou.

- Nastavte vlastnost **název** rozhraní Microsoft Active ACCESSIBILITY (MSAA) na **Procházet...** (včetně tří teček), aby se čtenáři obrazovky načetly jako "Procházet", a ne "tečka-tečka-tečka" nebo "perioda-period-period". U spravovaných ovládacích prvků to znamená nastavení vlastnosti s **přístupným přístupem** .

- Nikdy nepoužívejte tlačítko se třemi tečkami **[...]** pro cokoli s výjimkou akce procházení. Například pokud potřebujete tlačítko **[New...]** , ale nemáte dostatek místa pro text, je nutné změnit návrh dialogu.

##### <a name="sizing-and-spacing"></a>Velikost a mezery
![Změna velikosti [Procházet...] tlačítka: standardní verze je 75x23 pixelů, krátká verze je 26x23 pixelů.](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 – 06_BrowseSizing")<br />Změna velikosti tlačítek [Procházet...]

![Mezery mezi tlačítky [Procházet...]: mezery mezi souvisejícím ovládacím prvkem a standardním tlačítkem pro procházení 7 pixelů, mezery mezi souvisejícím ovládacím prvkem a krátkým tlačítkem procházet 5 pixelů](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 – 07_BrowseSpacing")<br />Mezery [Procházet...] tlačítka

#### <a name="graphical-buttons"></a>Grafická tlačítka
Některá tlačítka by měla vždy používat grafický obraz a nikdy vkládat text do úspory místa a vyhnout se tak problémům s lokalizací. Tyto prvky se často používají v seznamech pro pole a v dalších seznamech s řazením.

> [!NOTE]
> Uživatelé musí mít k těmto tlačítkům kartu (nejsou k dispozici žádné přístupové klávesy), proto je umístěte do rozumné objednávky. Namapujte `name` vlastnost tlačítka na akci, kterou provede, aby čtenáři obrazovky správně interpretoval akci tlačítka.

| Funkce | Tlačítko |
| --- | --- |
| Přidání | ![Grafické tlačítko Přidat](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 – 08_ButtonAdd") |
| Odebrat | ![Grafické tlačítko odebrat](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 – 09_ButtonRemove") |
| Přidat vše | ![Grafické tlačítko Přidat vše](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 – 10_ButtonAddAll") |
| Odebrat vše | ![Grafické tlačítko "Odebrat vše"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 – 11_ButtonRemoveAll") |
| Přesunout nahoru | ![Grafické tlačítko "přesunout nahoru"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 – 12_ButtonMoveUp") |
| Přesunout dolů | ![Grafické tlačítko "přesunout dolů"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 – 13_ButtonMoveDown") |
| Odstranit | ![Grafické tlačítko "odstranit"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 – 14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Velikost a mezery
Velikost grafických tlačítek je stejná jako u krátké verze tlačítka **[Procházet...]** (26x23 pixelů):

![Vzhled tlačítka u grafického obrázku na tlačítku s a bez průhledné barvy](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 – 15_GraphicalButtonSpacing")<br />Vzhled tlačítka u grafického obrázku na tlačítku s a bez průhledné barvy

### <a name="hyperlinks"></a>Hypertextové odkazy
Hypertextové odkazy jsou vhodné pro akce založené na navigaci, jako je otevření tématu nápovědy, modálního dialogového okna nebo průvodce. Je-li pro příkaz použit hypertextový odkaz, měl by vždy zobrazovat viditelné a znatelné změny uživatelského rozhraní. Obecně platí, že akce, které potvrzují akci (například uložit, zrušit a odstranit), jsou lépe sděleny pomocí tlačítka.

#### <a name="writing-style"></a>Styl psaní
Postupujte podle [pokynů pro stolní počítače s Windows pro text uživatelského rozhraní](/windows/desktop/uxguide/text-ui). Nepoužívejte "Další informace o", "Řekněte mi více o" nebo "získat pomoc s touto formulací". Místo toho odkazová Nápověda text odkazuje na primární otázku zodpovězenou obsahem Nápověda. Například "**návody přidat server do Průzkumník serveru?**"

#### <a name="visual-style"></a>Vizuální styl

- Hypertextové odkazy by měly vždy používat [službu VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Pokud hypertextový odkaz není správně ve stylu, při jeho zobrazení dojde k jeho červenému blikání nebo po navštívení jiné barvy.

- Nezahrne podtržení v ovládacím prvku, pokud se nejedná o fragment věty v rámci úplné věty, jako je například v horní části.

- Podtržení by se neměl zobrazovat při najetí myší. Místo toho je zpětná vazba pro uživatele, že je aktivní odkaz, mírně zvýrazněna barvou a odpovídajícím kurzorem odkazu.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Stromová zobrazení

Stromová zobrazení slouží jako způsob uspořádání komplexních seznamů do skupin nadřazených a podřízených objektů. Uživatel může rozbalit nebo sbalit nadřazené skupiny a zobrazit nebo skrýt podkladové podřízené položky. Každou položku v rámci stromového zobrazení lze vybrat k zajištění dalších akcí.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Vizuální styl zobrazení stromu

#### <a name="expanders"></a>Rozšíření
Ovládací prvky stromového zobrazení by měly odpovídat návrhu rozšíření používanému v systémech Windows a Visual Studio. Každý uzel používá ovládací prvek rozšíření k zobrazení nebo skrytí podkladových položek. Použití ovládacího prvku rozšíření poskytuje konzistenci pro uživatele, kteří mohou narazit na různá stromová zobrazení v rámci systému Windows a sady Visual Studio.

![Oprava: správný styl uzlu stromového zobrazení pomocí ovládacího prvku rozšíření](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 – 1_TreeViewCorrect")<br />Oprava: správný styl uzlu stromového zobrazení pomocí ovládacího prvku rozšíření

![Nesprávné: nesprávný styl uzlu stromového zobrazení](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 – 2_TreeViewIncorrect1")<br />Nesprávné: nesprávný styl uzlu stromového zobrazení

#### <a name="selection"></a>Výběr
Když je vybrán uzel ve stromovém zobrazení, zvýraznění by se mělo rozšířit na celou šířku ovládacího prvku stromového zobrazení. To pomáhá uživatelům jasně určit, která položka byla vybrána. Barvy výběru by měly odrážet aktuální motiv sady Visual Studio.

![Správné: zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 – 1_TreeViewCorrect")<br />Správné: zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.

![Nesprávné: zvýraznění vybraného uzlu se nevejde na celou šířku ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 – 3_TreeViewIncorrect2")<br />Nesprávné: zvýraznění vybraného uzlu se nevejde na celou šířku ovládacího prvku stromového zobrazení.

#### <a name="icons"></a>Ikony
Ikony by měly být použity pouze v ovládacích prvcích stromového zobrazení, pokud je pomáhají vizuálně identifikovat rozdíly mezi položkami. Obecně by měly být ikony použity pouze v heterogenních seznamech, ve kterých ikony přenášejí informace pro odlišení typů prvků. V homogenním seznamu pomocí ikon se často považují za šum a je třeba se jim vyhnout. V takovém případě může ikona skupiny (nadřazená položka) vyjádřit typ položek v rámci tohoto případu. Výjimkou z tohoto pravidla by byla, pokud je ikona dynamická a používá se k označení stavu.

#### <a name="scroll-bars"></a>Posuvníky
Pokud se obsah vejde do ovládacího prvku stromového zobrazení, měly by být vždy skryté posuvníky. Je přijatelné, aby byly posuvníky skryty nebo částečně transparentní v rolovacím okně a zobrazily se v případě, že okno obsahující stromové zobrazení má fokus, nebo když najedete myší na samotný stromové zobrazení.

![Zobrazí se svislé i vodorovné posuvníky, protože obsah překročil limity ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 – 4_Scrollbars")<br />Zobrazí se svislé i vodorovné posuvníky, protože obsah překročil limity ovládacího prvku stromového zobrazení.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interakce stromového zobrazení

#### <a name="context-menus"></a>Místní nabídky
Uzel zobrazení stromu může zobrazit možnosti podnabídky v místní nabídce. K tomu obvykle dochází, když uživatel klikne pravým tlačítkem myši na položku nebo stisknete klávesu nabídky na klávesnici Windows s vybranou položkou. Je důležité, aby uzel získal fokus a byl vybrán. To pomáhá uživateli zjistit, do které položky Tato nabídka patří.

![Položka, která má vytvořit kontextovou nabídku, získá fokus a upozorní uživatele, která položka byla vybrána.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 – 5_ContextMenu")<br />Položka, která má vytvořit kontextovou nabídku, získá fokus a upozorní uživatele, která položka byla vybrána.

#### <a name="keyboard"></a>Klávesnice
Stromové zobrazení by mělo poskytovat možnost výběru položek a rozbalení/sbalení uzlů pomocí klávesnice. Tím se zajistí, že navigace splní naše požadavky na přístupnost.

##### <a name="tree-view-control"></a>Ovládací prvek stromového zobrazení
Ovládací prvky stromové struktury sady Visual Studio by měly následovat po běžné navigaci pomocí klávesnice:

- **Šipka nahoru:** Výběr položek přesunutím stromu

- **Šipka dolů:** Výběr položek přesunutím stromové struktury dolů

- **Šipka vpravo:** Rozbalí uzel ve stromové struktuře.

- **Šipka doleva:** Sbalení uzlu ve stromové struktuře

- **Zadejte klíč:** Iniciovat, načíst, spustit vybranou položku

##### <a name="trid-tree-view-and-grid-view"></a>TrID (zobrazení stromu a zobrazení mřížky)
Ovládací prvek trid je komplexní ovládací prvek, který obsahuje stromové zobrazení v rámci mřížky. Rozbalení, sbalení a navigace ve stromu by mělo respektovat stejné příkazy klávesnice jako stromové zobrazení, a to s následujícími přídavky:

- **Šipka vpravo:** Rozbalte uzel. Po rozbalení uzlu by měl pokračovat v přechodu na nejbližší sloupec na pravé straně. Navigace by se měla zastavit na konci řádku.

- **Karta:** Přejde na nejbližší buňku napravo.  Na konci řádku pokračuje navigace na dalším řádku.

- **SHIFT + TAB:** Přejde na nejbližší buňku vlevo.  Na začátku řádku pokračuje navigace do buňky úplně vpravo v předchozím řádku.

![Ovládací prvek trid v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 – 6_Trid")<br />Ovládací prvek trid v aplikaci Visual Studio
