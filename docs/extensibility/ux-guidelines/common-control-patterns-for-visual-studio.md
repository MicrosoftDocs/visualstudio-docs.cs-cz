---
title: Běžné vzory ovládacích prvků pro Visual Studio | Microsoft Docs
description: Přečtěte si, jak běžné ovládací prvky sady Visual Studio následují podle pokynů pro interakci s desktopy pro Windows a o speciálních situacích, které tyto pokyny rozšiřují
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899300"
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

     ![Nesprávná délka vstupního pole: je pravděpodobné, že název bude dlouhý.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Nesprávná délka vstupního pole: je pravděpodobné, že název bude dlouhý.

     ![Správná délka vstupního pole: vstupní pole je vhodnou šířkou pro očekávaný obsah.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Správná délka vstupního pole: vstupní pole je vhodnou šířkou pro očekávaný obsah.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Pole se seznamem a rozevírací seznamy
V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro rozevírací seznamy a pole se seznamem](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neprovádějte znovu šablonu ovládacího prvku. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní motivů se pole se seznamem a rozevírací seznamy řídí standardními pro ovládací prvky.

#### <a name="layout"></a>Layout
Pole se seznamem a rozevírací seznamy by měly být velikosti, aby odpovídaly šířce okna, ve kterém jsou zobrazeny, ani libovolně odpovídat délce dlouhého pole, jako je například cesta.

![Nesprávné: Šířka rozevíracího seznamu je pro obsah, který se zobrazí, moc dlouhá.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Nesprávné: Šířka rozevíracího seznamu je pro obsah, který se zobrazí, moc dlouhá.

![Správně: rozevírací seznam má velikost, aby bylo možné růst překladu, ale ne zbytečně dlouho.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Správně: rozevírací seznam má velikost, aby bylo možné růst překladu, ale ne zbytečně dlouho.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Zaškrtávací políčka
V případě typických chování interakce postupujte podle [pokynů pro plochu Windows pro instalaci zaškrtávacích políček](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neprovádějte znovu šablonu ovládacího prvku. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní s motivem se zaškrtávací políčka dodržujte standardní pro ovládací prvky.

#### <a name="specialized-interactions"></a>Specializované interakce

- Interakce se zaškrtávacím políčkem nesmí nikdy odložit dialog ani přejít do jiné oblasti.

- Zaškrtávací políčka zarovnejte se směrným plánem prvního řádku textu.

     ![Nesprávné: zaškrtávací políčko je na textu zarovnané na střed.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Nesprávné: zaškrtávací políčko je na textu zarovnané na střed.

     ![Správné: zaškrtávací políčko je zarovnáno s prvním řádkem textu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Správné: zaškrtávací políčko je zarovnáno s prvním řádkem textu.

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

To uživateli umožňuje vybrat text uvnitř pole, ale nikoli ho upravit. Tato textová pole jsou ohraničována obvyklou 3D chílovou `ButtonShadow` výplní.

Textové pole se může stát aktivní (upravitelné), když uživatel změní přidružený ovládací prvek, například zaškrtnutím nebo zrušením zaškrtnutí políčka nebo výběrem nebo zrušením výběru přepínačů. Například na stránce Možnosti  **&gt; nástrojů** zobrazené níže se textové pole  Domovská stránka stane aktivní, když není zaškrtnuté políčko Použít výchozí.

![Textové pole jen pro čtení s neaktivními a aktivními stavy](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Textové pole jen pro čtení s neaktivními a aktivními stavy

### <a name="using-text-in-dialogs"></a>Použití textu v dialogových oknech

Klíčové pokyny pro text v dialogových oknech:

- Popisky textových polí, seznamových polí a rámců v nethemed dialogech začínají slovesem, počátečním velkým písmenem pouze u prvního slova a končí dvojtečkou.

    > Textové ovládací prvky v dialogových oknech s motivy se řídí pokyny pro desktopové uživatelské prostředí [Windows](/windows/desktop/uxguide/top-violations) a neukončují koncovou interpunkci s výjimkou otazníků v odkazech nápovědy.

- Popisky zaškrtávacích políček a tlačítek možností začínají slovesem, počátečním velkým písmenem pouze u prvního slova a nemají koncovou interpunkci.

- Popisky tlačítek, nabídek, položek nabídky a karet mají u každého slova počáteční velká písmena (velká písmena).

- Terminologie popisků by měla být v jiných dialogových oknech konzistentní s podobnými popisky.

- Pokud je to možné, pište nebo schvalte text před tím, než se předá vývojáři k implementaci, zapiste nebo schvalte.

- Všechny ovládací prvky by měly mít popisky s výjimkou zvláštních okolností, kdy je tabulátor dostačující.
V případě potřeby použijte pomocná text.

### <a name="helper-text"></a>Text pomocné pomoci

Je součástí dialogů, které uživateli pomůžou pochopit účel dialogového okna nebo určit, jakou akci se má provést. Pomocný text by se měl používat jenom v případě potřeby, aby nedocházelo k nepotřebné jednoduché dialogové okny. Dvě varianty textu pomocníka jsou dialog a vodoznak.

Sledujte běžná místa pro pomocných textů a buďte při zavádění nových oblastí selektivně. Mezi běžné scénáře pro text pomocné pomoci, které se můžou zobrazit, jsou tyto:

- Pomocná text v dialogových oknech, který vám poskytne další pokyny k interakci s komplexním dialogem.

- Text vodoznaku v prázdných oknech nástrojů nebo dialogových oknech s vysvětlením, proč není viditelný žádný obsah.

- Podokno popisu, například v dolní části **okno Vlastnosti**.

- Text vodoznaku v prázdném editoru, který vysvětluje, jakou akci by měl uživatel provést, aby mohl začít.

### <a name="dialog-helper-text"></a>Text pomocníka dialogového okna

Návrhář uživatelského prostředí může pomoct určit, kdy je vhodný pomocná text. Návrhář může definovat, kde se zobrazí pomocná text a jeho obecný obsah. Pomoc s uživatelem může napsat nebo upravit skutečný text.

### <a name="watermarks"></a>Vodoznaky

Dialogy využívají mírně odlišné pokyny pro vodoznaky. Vzhledem k tomu, že dialogové okno může být přetíženo mnoha prvky uživatelského rozhraní (popisky, text nápovědy, tlačítka a další ovládací prvky kontejneru s textem), zejména pokud jsou zobrazeny v černé barvě, vodoznaky lépe vyniknou v tmavě šedé barvě (VSColor: `ButtonShadow` ). Uvnitř ovládacího prvku se obvykle zobrazuje vodoznak, například seznam s bílým pozadím (VSColor: `Window` ).

- Text se zobrazí v tmavě šedé barvě (VSColor: `ButtonShadow` ). Pokud se však vodoznak zobrazuje na pozadí se střední šedou nebo jinou barvou (VSColor: ) a existuje obavy o jeho čitelnost, přejděte k černému textu `ButtonFace` (VSColor: `WindowText` ).

- Vodoznaky je možné zarovnaně na střed nebo vyprázdnit doleva. Při rozhodování o sladění použijte standardní pravidla návrhu. Vodoznak není možné vybrat na pozadí.

![Příklad textu vodoznaku](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Příklad textu vodoznaku

### <a name="context-specific-dynamic-text"></a>Kontextový (dynamický) text

Dynamický text lze použít jedním ze dvou způsobů v dialogovém okně nebo v ne moderované uživatelském rozhraní: jako dynamický popisek nebo jako dynamický obsah.

- Dynamický popisek: Dynamický text se běžně používá na popisných panelech, které pro vybranou položku nabízejí více informací, například v dialogovém okně, které obsahuje seznam prvků a vlastností pro prvky zobrazené v mřížce vpravo. Popisek mřížky vlastností může být dynamický, takže když je na levé straně vybraná položka, zobrazí se v mřížce vpravo informace o konkrétní položce.

- Dynamický text: Může být užitečný v případech, kdy potřebujete zobrazit konkrétní informace, a ne obecné informace tímto způsobem, ale měli byste věnovat pozor, abyste ho nevyužily příliš.

Pokud chcete, aby uživatelé měli možnost kopírovat informace, dynamický text by měl být v textovém poli jen pro čtení.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Tlačítka a hypertextové odkazy

### <a name="overview"></a>Přehled
Tlačítka a ovládací prvky propojení (hypertextové odkazy) by měly dodržovat základní pokyny k používání, formulaci, velikosti a mezerám v hypertextových odkazech na plochu [Windows.](/windows/desktop/uxguide/ctrl-links)

### <a name="choosing-between-buttons-and-links"></a>Volba mezi tlačítky a odkazy
Tlačítka se tradičně používala pro akce a hypertextové odkazy, které jsou vyhrazené pro navigaci. Tlačítka lze použít ve všech případech, ale role odkazů byla v systému Visual Studio tak, aby tlačítka a odkazy byly za některých podmínek zaměnitelné.

Kdy použít příkazová tlačítka:

- Primární příkazy

- Zobrazení oken používaných ke shromažďování vstupu nebo rozhodování, i když se to jsou sekundární příkazy

- Destruktivní nebo nevratné akce

- Tlačítka závazku v průvodcích a tocích stránek

Vyhněte se příkazovým tlačítkům v oknech nástrojů nebo pokud pro popisek potřebujete více než dvě slova. Odkazy mohou mít delší popisky.

 Kdy použít odkazy:

- Navigace do jiného okna, dokumentu nebo webové stránky

- Situace, které k popisu záměru akce vyžadují delší nebo krátkou větu

- Úzké prostory, kde by tlačítko zahltí uživatelské rozhraní za předpokladu, že akce není destruktivní nebo nevratná

- Zrušte důraz na sekundární příkazy v situacích, kdy existuje mnoho příkazů.

#### <a name="examples"></a>Příklady
![Odkazy na příkazy použité na informačním panelu za stavovou zprávou](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Odkazy na příkazy použité na informačním panelu za stavovou zprávou

![Odkazy použité v automaticky otevíraného okně CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Odkazy použité v místní nabídce CodeLens

![Odkazy používané pro sekundární příkazy, kde by tlačítka přilákala příliš velkou pozornost](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Odkazy používané pro sekundární příkazy, kde by tlačítka přilákala příliš velkou pozornost

### <a name="common-buttons"></a>Běžná tlačítka

#### <a name="text"></a>Text
Postupujte podle pokynů pro psaní v textu [uživatelského rozhraní a terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Vizuální styl

##### <a name="standard-unthemed"></a>Standardní (bez náhonů)
Většina tlačítek v Visual Studio se zobrazí v dialogových oknech nástrojů a neměla by mít styl. Měly by odrážet standardní vzhled tlačítek, který určuje operační systém.

##### <a name="themed"></a>Tématickém
V některých případech mohou být tlačítka použita v uživatelském rozhraní se stylem a tato tlačítka musí mít odpovídající styl. Informace [o ovládacích](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) prvcích s informačními prvky najdete v tématu Dialogová okna.

### <a name="special-buttons"></a>Speciální tlačítka

#### <a name="browse-buttons"></a>Procházet... Tlačítka
**[Procházet...]** Tlačítka se používají v mřížkách, dialogových oknech a oknech nástrojů a dalších ne moderované prvky uživatelského rozhraní. Zobrazí výběr, který uživateli pomůže vyplnit hodnotu do ovládacího prvku. Existují dvě varianty tohoto tlačítka: dlouhé a krátké.

![Dlouhé tlačítko [Procházet...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Dlouhé tlačítko [Procházet...]

![Krátké tlačítko pouze se třemi tečkami](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Krátké tlačítko pouze se třemi tečkami

Kdy použít krátké tlačítko jen se třemi tečkami:

- Pokud je v dialogovém okně více než jedno dlouhé tlačítko **[Procházet...],** například když procházení umožňuje několik polí. Použijte krátké **tlačítko pro každý** z nich, abyste se vyhnuli matoucím přístupových klíčům vytvořeným v této situaci (&**Procházet** a B **&řádky** ve stejném dialogovém okně).

- V úzkém dialogovém okně nebo v případě, že není vhodné umístit dlouhé tlačítko.

- Pokud se tlačítko zobrazí v ovládacím prvku mřížky

Pokyny pro použití tlačítka:

- Nepoužívejte přístupový klíč. Pro přístup k klávesnici musí uživatel použít tabulátor ze sousedního ovládacího prvku. Ujistěte se, že pořadí ovládacích karet je takové, aby jakékoli tlačítko pro procházení spadne hned za pole, které vyplní. Podtržítka nikdy nepoužívejte podtržítka pod prvním obdobím.

- Nastavte vlastnost MSAA (Microsoft Active Accessibility) (MSAA) **Name** na **Browse...** (včetně tří tlací), aby ji čtečky obrazovky četly jako "Procházet" a ne "dot-dot-dot" nebo "period-period-period". U spravovaných ovládacích prvků to znamená nastavení **vlastnosti AccessibleName.**

- Nikdy nepoužívejte tlačítko se třemi **tečkami ( )** pro cokoli kromě akce procházení. Pokud například potřebujete tlačítko **[Nový...],** ale nemáte dostatek místa pro text, je potřeba dialogové okno přepracované.

##### <a name="sizing-and-spacing"></a>Nastavení velikosti a mezer
![Tlačítka pro změnu velikosti [Procházet...]: standardní verze je 75 × 23 pixelů, krátká verze je 26 × 23 pixelů.](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Tlačítka pro změnu velikosti [Procházet...]

![Mezery mezi tlačítky [Procházet...]: mezery mezi souvisejícím ovládacím tlačítkem a standardním tlačítkem Procházet 7 pixelů, mezery mezi souvisejícím ovládacím tlačítkem a krátké tlačítko Procházet 5 pixelů](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Mezery [Procházet...] – tlačítka

#### <a name="graphical-buttons"></a>Grafická tlačítka
Některá tlačítka by měla vždy používat grafický obrázek a nikdy by neměla obsahovat text, který šetří místo a zabraňuje problémům s lokalizací. Často se používají ve výběrech polí a dalších seřaditelných seznamech.

> [!NOTE]
> Uživatelé musí na tato tlačítka přechádovat tabulátor (neexistují žádné přístupové klíče), takže je umístěte v rozumném pořadí. Namapovat vlastnost tlačítka na akci, která se má provést, aby čtečky obrazovky správně `name` interpretují akci tlačítka.

| Funkce | Tlačítko |
| --- | --- |
| Přidání | ![Grafické tlačítko Přidat](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Odebrat | ![Grafické tlačítko Odebrat](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Přidat vše | ![Grafické tlačítko Přidat vše](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Odebrat vše | ![Grafické tlačítko Odebrat vše](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Přesunout nahoru | ![Grafické tlačítko Přesunout nahoru](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Přesunout dolů | ![Grafické tlačítko Přesunout dolů](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Odstranit | ![Grafické tlačítko Odstranit](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Nastavení velikosti a mezer
Velikost grafických tlačítek je stejná jako u krátké verze tlačítka **[Browse...]** (26 × 23 pixelů):

![Vzhled grafického obrázku na tlačítku, se zobrazenou transparentní barvou a bez ní](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Vzhled grafického obrázku na tlačítku, se zobrazenou transparentní barvou a bez ní

### <a name="hyperlinks"></a>Hypertextové odkazy
Hypertextové odkazy jsou vhodné pro akce založené na navigaci, jako je otevření tématu nápovědy, modálního dialogového okna nebo průvodce. Pokud se pro příkaz používá hypertextový odkaz, měl by se vždy zobrazit viditelná a patrná změna uživatelského rozhraní. Obecně platí, že akce, které se potvrdí k akci (například Uložit, Zrušit a Odstranit), se lépe komunikují pomocí tlačítka.

#### <a name="writing-style"></a>Styl psaní
Postupujte podle [pokynů k ploše Windows pro text uživatelského rozhraní.](/windows/desktop/uxguide/text-ui) Nepoužívejte fráze "Další informace o", "Řekněte mi více o" nebo "Získat pomoc s tímto". Místo toho fráze Text odkazu nápovědy z hlediska primární otázky zodpovězené obsahem nápovědy. Příklad:**Návody server do Průzkumník serveru?**

#### <a name="visual-style"></a>Vizuální styl

- Hypertextové odkazy by měly vždy [používat službu VSColor.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService) Pokud hypertextový odkaz nemá správný styl, bude při aktivním odkazu blikat červeně nebo se po návštěvě zobrazí jiná barva.

- Pokud odkaz není fragment věty v celé větě, například ve vodoznaku, nezahrňte podtržení do stavu odpočinku ovládacího prvku.

- Při najetí myší by se neměly zobrazovat podtržení. Místo toho je zpětná vazba od uživatele, že je odkaz aktivní, drobná změna barvy a vhodný kurzor odkazu.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Stromová zobrazení

Stromová zobrazení poskytují způsob uspořádání složitých seznamů do skupin nadřazený-podřízený. Uživatel může rozbalit nebo sbalit nadřazené skupiny a zobrazit nebo skrýt podkladové podřízené položky. Každou položku ve stromovém zobrazení je možné vybrat a poskytnout tak další akci.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Styl vizuálu stromového zobrazení

#### <a name="expanders"></a>Rozšíření
Ovládací prvky stromového zobrazení by měly odpovídat návrhu rozšíření používanému ve Windows a Visual Studio. Každý uzel používá ovládací prvek rozbalení k zobrazení nebo skrytí podkladových položek. Použití ovládacího prvku rozbalení zajišťuje konzistenci pro uživatele, kteří se mohou setkat s různými stromová zobrazeními ve Windows a Visual Studio.

![Správně: Správný styl uzlu stromového zobrazení pomocí ovládacího prvku rozbalení](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Správně: Správný styl uzlu stromového zobrazení pomocí ovládacího prvku rozbalení

![Nesprávná: nesprávný styl uzlu stromového zobrazení](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Nesprávná: nesprávný styl uzlu stromového zobrazení

#### <a name="selection"></a>Výběr
Když ve stromovém zobrazení vyberete uzel, mělo by se zvýraznění zvětšit na celou šířku ovládacího prvku stromového zobrazení. To pomáhá uživatelům jasně určit, kterou položku vybrali. Barvy výběru by měly odrážet aktuální Visual Studio motiv.

![Správně: Zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Správně: Zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.

![Špatně: Zvýraznění vybraného uzlu se nevejde na celou šířku ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Špatně: Zvýraznění vybraného uzlu se nevejde na celou šířku ovládacího prvku stromového zobrazení.

#### <a name="icons"></a>Ikony
Ikony by se měly používat jenom v ovládacích prvcích stromového zobrazení, pokud pomáhají vizuálně identifikovat rozdíly mezi položkami. Obecně platí, že ikony by se měly používat pouze v heterogenních seznamech, ve kterých Ikony nesou informace k rozlišení typů prvků. V homogenním seznamu pomocí ikon je často možné naznačovat šum a měli byste se jim vyhnout. V takovém případě může ikona skupiny (nadřazená) vyjádřit typ položek v ní. Výjimkou z tohoto pravidla je, pokud je ikona dynamická a slouží k označení stavu.

#### <a name="scroll-bars"></a>Posuvníky
Posuvníky by měly být vždy skryté, pokud se obsah vejde do ovládacího prvku stromového zobrazení. Posuvníky mohou být skryté nebo částečně průhledné v posouvání a zobrazí se, když je okno obsahující stromové zobrazení zaostřeno nebo když najedete myší na samotné stromové zobrazení.

![Zobrazí se svislé i vodorovné posuvníky, protože obsah překročil limity ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Zobrazí se svislé i vodorovné posuvníky, protože obsah překročil limity ovládacího prvku stromového zobrazení.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interakce stromového zobrazení

#### <a name="context-menus"></a>Místní nabídky
Uzel stromového zobrazení může zobrazit možnosti podnabídky v místní nabídce. K tomu obvykle dochází, když uživatel klikne pravým tlačítkem na položku nebo stiskne klávesu Nabídky na klávesnici Windows s vybranou položkou. Je důležité, aby uzel získal fokus a byl vybrán. To pomáhá uživateli určit, do které položky podnabídka patří.

![Položka, která vygeneroval místní nabídku, získá fokus, který uživateli oznámí, která položka byla vybrána.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Položka, která vygeneroval místní nabídku, získá fokus, který uživateli oznámí, která položka byla vybrána.

#### <a name="keyboard"></a>Klávesnice
Stromové zobrazení by mělo poskytovat možnost vybrat položky a rozbalit/sbalit uzly pomocí klávesnice. Tím se zajistí, že navigace splňuje naše požadavky na přístupnost.

##### <a name="tree-view-control"></a>Ovládací prvek Stromové zobrazení
Visual Studio stromové struktury by měly dodržovat běžnou navigaci pomocí klávesnice:

- **Šipka nahoru:** Výběr položek přesunutím stromu nahoru

- **Šipka dolů:** Výběr položek přesunutím dolů ve stromu

- **Šipka doprava:** Rozbalení uzlu ve stromu

- **Šipka doleva:** Sbalení uzlu ve stromu

- **Enter key (Zadat klíč):** Spuštění, načtení a spuštění vybrané položky

##### <a name="trid-tree-view-and-grid-view"></a>Trid (stromové zobrazení a zobrazení mřížky)
Ovládací prvek trid je složitý ovládací prvek, který obsahuje stromové zobrazení v mřížce. Rozbalení, sbalení a navigace ve stromu by měly respektovat stejné příkazy klávesnice jako stromové zobrazení s následujícími doplňky:

- **Šipka doprava:** Rozbalte uzel. Po rozbalení uzlu by měl pokračovat v navigaci na nejbližší sloupec na pravé straně. Navigace by se měla zastavit na konci řádku.

- **Karta:** Přejde na nejbližší buňku na pravé straně.  Na konci řádku pokračuje navigace k dalšímu řádku.

- **Shift + Tab:** Přejde na nejbližší buňku vlevo.  Na začátku řádku pokračuje navigace na buňku nejvíce vpravo na předchozím řádku.

![Ovládací prvek trid v Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ovládací prvek trid v Visual Studio
