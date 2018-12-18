---
title: Vzory běžných ovládacích prvků
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2de92d2b6083fd587dc38a67e189fa9ca24b660d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53052142"
---
# <a name="common-control-patterns-for-visual-studio"></a>Vzory běžných ovládacích prvků pro sadu Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Běžné ovládací prvky

### <a name="overview"></a>Přehled
 Běžné ovládací prvky tvoří většinu uživatelského rozhraní v sadě Visual Studio. Většina běžných ovládacích prvků používaná v rozhraní sady Visual Studio by měly dodržovat [pokyny pro Windows Desktop interakci](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Tento dokument je určený k sadě Visual Studio a popisuje zvláštní situace nebo podrobnosti, které rozšiřují tyto pokyny pro Windows.

#### <a name="common-controls-in-this-topic"></a>Běžné ovládací prvky v tomto tématu

-   [Posuvníky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

-   [Vstupní pole](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

-   [Pole se seznamem a rozevírací seznamy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

-   [Zaškrtávací políčka](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

-   [Přepínací tlačítka](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

-   [Skupiny snímků](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

-   [Textových ovládacích prvků](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

-   [Tlačítka a hypertextových odkazů](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

-   [Zobrazení stromu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Vizuální styl
 První věc, kterou vzít v úvahu při používání stylů pro ovládací prvky se určuje, zda ovládací prvky se použije v uživatelském rozhraní s motivem. Ovládací prvky ve standardní uživatelské rozhraní jsou – s motivem uživatelského rozhraní a musí dodržovat [stylu Normální Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), což znamená, že nejsou opětovné použití šablon a by se měla objevit v jejich výchozí vzhled ovládacího prvku.

-   **Dialogová okna Standard (nástroj):** není s motivem. Provést znovu – šablony. Použijte výchozí styl základního ovládacího prvku.

-   **Nástroje systému windows, editory dokumentu, návrhové ploše a dialogová okna s motivem:** použít specializované s motivem vzhled pomocí služby barvu.

###  <a name="BKMK_Scrollbars"></a> Posuvníky
 Postupujte podle posuvníky [běžné vzory interakcí pro posuvník Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) pokud jejich rozšířená o informace o obsahu, jako například v editoru kódu.

###  <a name="BKMK_InputFields"></a> Vstupní pole
 Chování typické interakce, postupujte [pokyny pro Windows Desktop pro textová pole](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

-   Vstupních polí by neměly být ve stylu v dialogových oknech nástroje. Použijte základní styl vnitřní ovládací prvek.

-   S motivem vstupních polí byste měli použít pouze ve s motivem dialogová okna a okna nástrojů.

#### <a name="specialized-interactions"></a>Specializované interakce

-   Pole jen pro čtení bude mít šedé (zakázáno) pozadí ale popředí výchozí (aktivní).

-   Povinné pole by měly mít  **\<vyžaduje >** jako vodoznaky v nich. Barva pozadí s výjimkou ve výjimečných případech byste neměli měnit.

-   Chyba ověřování: viz [oznámení a postup pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

-   K zobrazení celého obsahu, ne na šířku okna, ve kterém jsou uvedeny ani libovolně odpovídala délce dlouhé pole, jako je například cesta by měla mít velikost vstupních polí. Délka mohlo by to znamenat uživateli omezení jde o tom, kolik znaky jsou povoleny v poli.

     ![Šířku ovládacího prvku nesprávný vstupní pole](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl") **nesprávný vstupní pole délky: není pravděpodobné, že název bude takto dlouhé.**

     ![Opravte šířku ovládacího prvku vstupního pole](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl") **opravte vstupní délka pole: vstupní pole je rozumné šířku pro očekávaný obsah.**

###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Pole se seznamem a rozevírací seznamy
 Pro typické interakce chování, postupujte [Windows Desktop pokyny pro rozevírací seznamy a pole se seznamem](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

-   V dialogových oknech nástrojů provést znovu – šablony ovládacího prvku. Použijte základní styl vnitřní ovládací prvek.

-   Postupujte podle standardní motivy pro ovládací prvky s motivem uživatelského rozhraní, pole se seznamem a rozevírací seznamy.

#### <a name="layout"></a>Rozložení
 Pole se seznamem a rozevírací seznamy by měl být dimenzovány pro zobrazení celého obsahu, ne na šířku okna, ve kterém jsou uvedeny ani libovolně odpovídala délce dlouhé pole, jako je například cesta.

 ![Nesprávný rozevírací&#45;dolů rozložení](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")

 **Délka nesprávná pole pro ovládací prvek rozevírací seznam**

 ![Správné rozevírací&#45;dolů rozložení](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")

 **Délka správné pole pro ovládací prvek rozevírací seznam**

###  <a name="BKMK_CheckBoxes"></a> Zaškrtávací políčka
 Chování typické interakce, postupujte [pokyny pro Windows Desktop pro zaškrtávací políčka](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

-   V dialogových oknech nástrojů provést znovu – šablony ovládacího prvku. Použijte základní styl vnitřní ovládací prvek.

-   Zaškrtávací políčka v uživatelském rozhraní s motivem, postupujte podle standardní motivy pro ovládací prvky.

#### <a name="specialized-interactions"></a>Specializované interakce

-   Interakce se zaškrtávacím políčkem musí nikdy vyvolat přes pop dialogové okno nebo přejít do jiné oblasti.

-   Zarovnejte zaškrtávací políčka se standardními hodnotami první řádek textu.

     ![Zarovnání nesprávné zaškrtávací políčko](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign") **nesprávné zaškrtávací políčko zarovnání: zaškrtávací políčko, které jsou zaměřeny na text.**

     ![Opravte zaškrtávací políčko zarovnání](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign") **opravte zaškrtávací políčko zarovnání: zaškrtávací políčko je v souladu s účaří prvního řádku textu.**

###  <a name="BKMK_RadioButtons"></a> Přepínací tlačítka
 Chování typické interakce, postupujte [pokyny pro Windows Desktop pro přepínací tlačítka](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl
 V dialogových oknech nástrojů to není styl přepínací tlačítka. Použijte základní styl vnitřní ovládací prvek.

#### <a name="specialized-interactions"></a>Specializované interakce
 Není nutné použít blok skupiny k uzavření možnosti přepínače.

###  <a name="BKMK_GroupFrames"></a> Skupiny snímků
 Chování typické interakce, postupujte [Windows Desktop pokyny pro skupinu snímků](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl
 V dialogových oknech nástrojů to není styl skupiny snímků. Použijte základní styl vnitřní ovládací prvek.

#### <a name="layout"></a>Rozložení

-   Není nutné pro používání skupinového rámečku uzavřít přepínač možnosti, pokud je třeba spravovat skupiny rozdíl v těsné rozložení.

-   Nikdy nepoužívejte skupinového rámečku pro jeden ovládací prvek.

-   Někdy je nepřijatelné využívat vodorovná čára místo rámce kontejneru skupiny.

##  <a name="BKMK_TextControls"></a> Textových ovládacích prvků

### <a name="labels"></a>Popisky

#### <a name="active-label-state"></a>Stav Active popisek

##### <a name="utility-standard-dialogs"></a>Nástroj dialogových oken (standard))

-   Obecně platí postupujte podle pokynů Windows Desktop pro popisky ovládacího prvku.

-   V dialogových oknech nástrojů popisky by se zobrazit tučné, Barva písma a text standardní prostředí. Zobrazit [písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

-   Symbol tří teček musí vždy následovat popisky.

##### <a name="signature-themed-dialogs"></a>Podpis (s motivem) dialogová okna)
 Ovládací prvky popisek může být tučné písmo nebo světle šedá.

#### <a name="disabled-label-state"></a>Stav Zakázáno popisek
 Popisky by měly odrážet vzhled ovládacího prvku, které jsou přidruženy. Například pokud přidružený ovládací prvek je zakázaný, pak popisek by se zobrazit šedé a zakázané. To obvykle zařizuje služba operačního systému a vyžaduje žádné speciální zacházení.

#### <a name="dynamic-labels"></a>Dynamické popisky
 Dynamické popisky mění v závislosti na aktuální výběr. Kdykoli je to možné, použití dynamické popisků v rozložení záznamů master/detail umožňující uživateli snáze pochopit, že je zobrazené informace relevantní pro konkrétní výběr a ne obecné informace.

 ![Dynamické popisek použitý s dynamickým obsahem](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")

 **Příkladem dynamického popisek použitý s dynamickým obsahem**

#### <a name="instructional-text"></a>Návodný text
 Některé prvky rozhraní výhod instruktážní text umožňující uživateli snáze pochopit účel uživatelského rozhraní nebo označíte, jakou akci chcete provést.

-   Návodný text je nejčastěji používané v horní části dialogových oknech, ale se mohou objevit v jiných oblastech poskytnout pokyny pro seskupení komplexního ovládacího prvku.

-   Návodný text je jako neinteraktivní, ale může obsahovat hypertextové odkazy na témata nápovědy.

-   Použijte pokyny opatrně a pouze v případě potřeby.

##### <a name="formatting"></a>Formátování
 Návodný text by měl být prostředí písmo textu standardního ovládacího prvku (bez s motivem). Zobrazit [písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Podrobnosti o psaní pokyny najdete v tématu [uživatelského rozhraní text a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Návodný text formátování](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")

 **Návodný text v dialogovém okně Visual Studio**

#### <a name="informational-text"></a>Informační text
 Informační text je text, který poskytuje další informace o uživateli. Může být statická nebo dynamická nebo použít jako oznámení. Je vždy jen pro čtení, ale pokud je to vhodné uživatel chce mít možnost Kopírovat informace, dynamický text musí být umístěné ve kontejneru ovládacího prvku, jako je jen pro čtení textového pole.

##### <a name="dynamic-context-specific-text"></a>Dynamický text (konkrétní)
 Dynamický informační text se změní v závislosti na kontextu, například když uživatel přepne fokus. Často, ale ne vždy dynamický obsah je spárovaná s popiskem, dynamické.

 ![Dynamický informační text](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")

 **Dynamický informační text se změní v závislosti na kontextu.**

##### <a name="formatting"></a>Formátování
 Existují dva způsoby, jak zobrazit jen pro čtení textových polí: buď přímo v Uživatelském rozhraní povrchu (viz výše) nebo obsažené v jiném ovládacím prvku, jako je například skupina rámce nebo textového pole. Buď je správná, v závislosti na situaci. Záleží funkce návrháře a zjistěte, jak k zobrazení informací jen pro čtení.

 Text může být jen pro čtení textového pole. To obvykle naznačuje, že obsah lze vybrat a kopírovat, i když nelze upravit.

 ![Informační text formátování pro čtení&#45;pouze pole](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")

 **Informační text formátování pro pole jen pro čtení**

#### <a name="watermarks"></a>Vodoznaky
 Pomocí jiné volby slov mohou být stejné, je rozdíl mezi vodoznaky a pokyny, vodoznaky jsou nahrazeny obsahu při/okno ovládacího prvku není prázdná a neustále instruktážní text zůstane viditelný.

 Vodoznaky se použije při ovládacího prvku okno nebo je prázdný. Tyto určit, co je potřeba provést k vyplnění oblasti a může zahrnovat odkazy na akce otevřete příslušné windows, jako je například zdroj přetažení.

##### <a name="visual-style"></a>Vizuální styl

- Vodoznaky by měl být zarovnaný na střed vodorovně v okně.

- Vodoznaky by měl být zarovnaný na System center nejsou zarovnané vlevo.

- Vodoznaky může svisle na střed nebo umístěny v horní části oblasti. Pokud je umístěný v horní části oblasti, musí být dostatek místa na výše uvedené tak, aby se odlišuje vodoznak.

- Použití `Environment.GrayText` barvu písma token a standardní prostředí. Hypertextové odkazy by měl použít standardního hypertextového odkazu sdílet tokeny: `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, a `Environment.PanelHyperlinkDisabled`.

- Vodoznaky nelze vybrat na pozadí

- Pokud je to možné zahrnout odkazy vodoznak umožňující uživateli začít pracovat.

  ![Vodoznak textu v okně návrháře](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")

  ![Vodoznak textu v panelu nástrojů](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")

  **Příklady vodoznakového textu v sadě Visual Studio**

##  <a name="BKMK_ButtonsAndHyperlinks"></a> Tlačítka a hypertextových odkazů

### <a name="overview"></a>Přehled
 Ovládací prvky tlačítka a odkaz (hypertextové odkazy) by měly dodržovat [základní pokyny k Desktopu Windows na hypertextové odkazy](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) za využití, formulaci, změny velikosti a mezery.

### <a name="choosing-between-buttons-and-links"></a>Volba mezi tlačítka a odkazy
 Tradičně tlačítka se používají pro akce a hypertextové odkazy byly vyhrazeny pro navigaci. Tlačítka lze ve všech případech ale role odkazů došlo k rozbalení v sadě Visual Studio tak, že jsou zaměnitelné více v některých tlačítka a odkazy.

 Kdy použít příkazová tlačítka:

- Primární příkazy

- Zobrazení okna použitá ke shromažďování vstupu nebo rozhodování, a to i v případě, že jsou sekundární příkazy

- Destruktivní nebo nevratná akce

- Tlačítka závazku v rámci průvodců a toků

  Vyhněte se příkazových tlačítek v oknech nástrojů, nebo pokud potřebujete více než dvě slova pro popisek. Odkazy můžou mít delší popisky.

  Kdy použít odkazy:

- Navigace k jinému oknu, dokumentu nebo webové stránky

- Situace, které vyžadují delší popisek nebo krátká věta popisující cílem akce

- Úzkou prostory, ve kterém by tlačítko zahlcovat uživatelského rozhraní, za předpokladu, že akce není destruktivní nebo nevratné

- Deaktivace zdroje, výrazná sekundární příkazy v situacích, kdy existuje mnoho příkazů

#### <a name="examples"></a>Příklady
 ![Informační panel odkazy příkaz následující za zprávou stav](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")

 **Příkaz odkazů použité v informačním panelu po stavová zpráva**

 ![Odkazů použité v místní nabídce CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")

 **Odkazů použité v místní nabídce CodeLens**

 ![Odkazy používá jako sekundární příkazy](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")

 **Odkazů použité pro sekundární příkazy, kde by tlačítka přilákat příliš mnoho pozornost**

### <a name="common-buttons"></a>Běžné tlačítka

#### <a name="text"></a>Text
 Postupujte podle pokynů na zápis v [uživatelského rozhraní text a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Vizuální styl

##### <a name="standard-dialogs"></a>Standardní dialogová okna
 Většina tlačítek v sadě Visual Studio se zobrazí v standardní dialogová okna a by neměl být ve stylu. Standardní vzhled tlačítek odrážejí určený operační systém.

##### <a name="themed"></a>S motivem
 V některých případech slouží tlačítka v rámci upravený uživatelského rozhraní a tato tlačítka musí být navržen tak, odpovídajícím způsobem. Zobrazit [dialogová okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) o ovládací prvky s motivem.

### <a name="special-buttons"></a>Speciální tlačítka

#### <a name="browse-buttons"></a>Projděte... tlačítka
 **[Procházet...]**  tlačítka se používají v mřížkách, dialogová okna a okna nástrojů a dalších nemodální prvky uživatelského rozhraní. Zobrazí se ovládacího prvku pro výběr, který pomáhá uživateli při vyplňování hodnotu do ovládacího prvku. Existují dvě varianty toto tlačítko, dlouhé a krátké.

 ![Dlouhé &#91;Procházet... &#93; tlačítko](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")

 **Dlouhé tlačítko [Procházet...]**

 ![Krátký tlačítko se třemi tečkami&#45;pouze &#91;Procházet... &#93; tlačítko](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")

 **Tlačítko jen tlačítko se třemi tečkami short [...]**

 Kdy použít jen pro tlačítko se třemi tečkami krátký tlačítko:

- Pokud existuje více než jeden dlouhý **[Procházet...]**  tlačítko v dialogovém okně, například pokud několik polí Povolit pro procházení. Používat krátké **[...]**  tlačítko pro každý z nich matoucí přístupové klíče vytvořené v této situaci vyhnout (**& Procházet** a **B & rocházet** v dialogovém okně stejné).

- V dialogovém okně úzkou nebo neexistuje žádný přiměřené umísťovat dlouhé tlačítko.

- Je-li na tlačítko se zobrazí v ovládacím prvku grid.

  Pokyny, pomocí tlačítka:

- Nepoužívejte přístupový klíč. Pro přístup k ní pomocí klávesnice, musí uživatel karty sousedící ovládacího prvku. Ujistěte se, že je pořadí tak, aby žádné tlačítko pro procházení spadá ihned po pole bude vyplněn. Nikdy nepoužívejte podtržítka pod první období.

- Nastavení Microsoft Active Accessibility (MSAA) **název** vlastnost **Procházet...**  (včetně na tři tečky), který obrazovky čtenáři budou číst ho jako "Procházet" a "tečka – tečka – tečka" nebo "období období období." Pro spravované ovládací prvky, to znamená, že nastavení **AccessibleName** vlastnost.

- Nikdy nepoužívejte trojtečka **[...]**  tlačítko pro všechno, co s výjimkou procházení akce. Například, pokud potřebujete **[nový …]**  tlačítko, ale nemají dostatek volného místa pro text, pak dialogového okna musí být přepracován.

##### <a name="sizing-and-spacing"></a>Dimenzování a mezery
 ![Změna velikosti &#91;Procházet... &#93; tlačítka](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")

 **Tlačítka pro změnu velikosti [Procházet...]**

 ![Mezery &#91;Procházet... &#93; tlačítka](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")

 **Mezery mezi tlačítka [Procházet...]**

#### <a name="graphical-buttons"></a>Grafické tlačítka
 Některá tlačítka by měla vždy použít grafické image a nikdy obsahovat text ušetřit místo a vyhnout se potíže s lokalizací. Často používají v jiných seřaditelné seznamy a pole výběr.

> [!NOTE]
>  Uživatelé mají na kartě tato tlačítka (neexistují žádné přístupové klíče), takže je umístit v rozumné pořadí. Mapování vlastnosti název tlačítka na akci, která je potřebná tak, aby čtečky obrazovky správně interpretovat akce tlačítka.

|||
|-|-|
|Přidejte|![Grafické tlačítko "Přidat"](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|
|odebrat|![Grafické tlačítko "Remove"](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|
|Přidat vše|![Grafické tlačítko "Přidat vše"](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|
|Odebrat vše|![Grafické "Odstranit vše" tlačítko](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|
|Přesunout nahoru|![Grafické tlačítko "Nahoru"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|
|Přesunout dolů|![Grafické "tlačítko Přesunout dolů"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|
|Odstranit|![Grafické tlačítko "Odstranit"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Dimenzování a mezery
 Změny velikosti pro grafické tlačítka je stejná jako zkrácené **[Procházet...]**  tlačítko (26 × 23 pixelů):

 ![Tlačítko a nemusíte průhlednou barvu zobrazující](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")

 **Vzhled grafického obrázku na tlačítku a nemusíte průhlednou barvu zobrazující**

### <a name="hyperlinks"></a>Hypertextové odkazy
 Hypertextové odkazy se skvěle hodí pro navigaci na základě akce, jako je otevření tématu nápovědy, modální dialogové okno nebo průvodce. Pokud hypertextový odkaz se používá pro příkaz, je vždy zobrazit viditelné a výrazné změny v uživatelském rozhraní. Obecně platí akce, které se zavázali k akci (třeba uložit, zrušit a odstranit) se lépe předávají pomocí tlačítka.

#### <a name="writing-style"></a>Styl psaní
 Postupujte podle [Windows Desktop pokyny pro text v uživatelském rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Nepoužívejte "Přečtěte si další informace o," "Řekněte mi více o" nebo "Get s tímto vám pomůže" frázového. Místo toho věta text nápovědy odkazu z hlediska primární otázku zodpoví technický obsah nápovědy. Například "**jak mohu přidat server do Průzkumníka serveru?**"

#### <a name="visual-style"></a>Vizuální styl

-   Hypertextové odkazy vždy používejte [VSColor službu](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Pokud není správně ve stylu hypertextového odkazu, bliká červená, pokud je aktivní nebo ukazuje na jinou barvu po přístupu.

-   Nezahrnují podtržení v ovládacím prvku nejsou uložené stavu, dokud není odkaz na fragment věty úplné větě, jako v vodoznak.

-   Podtržení by se neměl zobrazit při najetí myší. Místo toho zpětná vazba pro uživatele, že je odkaz aktivní je změna mírné barvy a kurzoru příslušný odkaz.

##  <a name="BKMK_TreeViews"></a> Zobrazení stromu

### <a name="overview"></a>Přehled
 Zobrazení stromu poskytují způsob, jak uspořádat komplexní seznamy do skupin nadřazených a podřízených. Uživatele můžete rozbalit nebo sbalit nadřazené skupiny, které chcete zobrazit nebo skrýt základní podřízené položky. Poskytnout další akce lze vybrat každou položku v zobrazení stromu.

 Toto téma popisuje podmínky použití, správné návrhu a funkci stromová zobrazení.

#### <a name="in-this-topic"></a>V tomto tématu

-   [Vizuální styl](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

-   [Interakce](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

###  <a name="BKMK_TreeViewVisualStyle"></a> Vizuální styl

#### <a name="expanders"></a>Rozšíření
 Ovládací prvky zobrazení stromu by měl odpovídat rozšíření návrh používá Windows a Visual Studio. Chcete-li zobrazit nebo skrýt základní položky, používají jednotlivé uzly ovládacího prvku expander. Použití ovládacího prvku expander poskytuje konzistenci pro uživatele, kteří se mohou vyskytnout jiného stromu zobrazení v rámci Windows a Visual Studio.

 ![Opravte ovládací prvek stromového zobrazení](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Správné: správný styl zobrazení uzlu stromové struktury pomocí ovládacího prvku expander**

 ![Nesprávný stromové zobrazení uzlů](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")

 **Chyba: nesprávný styl stromovém zobrazení**

#### <a name="selection"></a>Výběr
 Když je vybrán uzel ve stromovém zobrazení, zvýraznění by měl rozšířit na celou šířku ovládací prvek stromového zobrazení. Díky tomu uživatelé se tak jasně identifikovat položky, které jste vybrali. Výběr barvy by měly odrážet aktuální motiv sady Visual Studio.

 ![Opravte ovládací prvek stromového zobrazení](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")

 **Správné: zvýraznění z vybraného uzlu odpovídá celé jeho šířce ovládací prvek stromového zobrazení.**

 ![Nesprávný stromové zobrazení zvýraznění](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")

 **Chyba: zvýraznění vybraný uzel není vhodná pro celou šířku ovládací prvek stromového zobrazení.**

#### <a name="icons"></a>Ikony
 Ikony by měla sloužit pouze v ovládacích prvcích stromů zobrazení Pokud podílí na vizuální určení rozdílů mezi položkami. Obecně platí ikony, které byste měli použít pouze ve heterogenní seznamy, ve kterých ikony nesou informaci k rozlišení mezi typy prvků. V homogenní seznamu pomocí ikon, často se dají považovat za šumu a mělo by se vyhnout. V takovém případě ikona skupiny (nadřazené) sdělí typem položek v něm. Výjimkou z tohoto pravidla by Pokud ikonu je dynamický a slouží k určení stavu.

#### <a name="scroll-bars"></a>Posuvníky
 Posuvníky vždy skryt, pokud se obsah vešel ovládací prvek stromového zobrazení. Je přijatelné pro posuvníky se seznamy skrytých nebo poloprůhledného posuvného okna a zobrazí, když okno obsahující stromové zobrazení má fokus nebo při přechodu ze stromu zobrazení samotný.

 ![Stromové zobrazení s posuvníky](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")

 **Protože obsah překročil omezení ovládací prvek stromového zobrazení, zobrazí se i vodorovné a svislé posuvníky.**

###  <a name="BKMK_TreeViewInteractions"></a> Interakce

#### <a name="context-menus"></a>Kontextové nabídky
 Uzel stromu zobrazení může odhalit podnabídky možnosti v kontextové nabídce. Obvykle k tomu dojde, když uživatel má klikli pravým tlačítkem myši položku nebo stisknutím klávesy nabídky na Windows klávesnice s zvolené položky. Je důležité, že uzel získá fokus a je vybrán. To pomáhá uživateli určit která položka patří podnabídky.

 ![Nabídka uzlu a kontext vybraného stromu](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")

 **Byla vybrána položka, která se má generovat fokus místní nabídky zisky upozornit uživatele, která položka.**

#### <a name="keyboard"></a>Klávesnice
 Ve stromovém zobrazení by měla poskytnout možnost vybrat položky a rozbalení/sbalení uzlů pomocí klávesnice. Tím se zajistí, že splňuje navigace naše požadavky na usnadnění přístupu.

##### <a name="tree-view-control"></a>Ovládací prvek stromového zobrazení
 Visual Studio ovládacích prvků strom postupujte podle běžných navigaci pomocí klávesnice:

-   **Šipka nahoru:** vybrat položky přesunutím směrem nahoru

-   **Šipky dolů:** vybrat položky přesunete dolů stromu

-   **Šipka doprava:** rozbalte uzel ve stromu

-   **Šipka doleva:** Sbalit uzel ve stromu

-   **Zadejte klíč:** iniciovat, načíst, spustit vybranou položku

##### <a name="trid-tree-view-and-grid-view"></a>Trid (stromové zobrazení a zobrazení mřížky)
 Trid ovládacího prvku je komplexní ovládací prvek obsahující stromové zobrazení v mřížce. Rozšíření, sbalování a procházení stromu by měly dodržovat stejné klávesových příkazů jako stromové zobrazení, s těmito přídavky:

- **Šipka doprava:** rozbalte uzel. Po rozbalení uzlu pokračováním, že přejdete na nejbližší sloupec na pravé straně. Na konci řádku, který by se měla zastavit navigace.

- **Karta:** Navigates na nejbližší buňku na pravé straně.  Na konci řádku navigace pokračuje na další řádek.

- **Shift + Tab:** Navigates na nejbližší buňku na levé straně.  Na začátku řádku, bude nadále navigace buňku vpravo na předchozím řádku.

  ![Trid ovládací prvek v sadě Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")

  **Trid ovládací prvek v sadě Visual Studio**
