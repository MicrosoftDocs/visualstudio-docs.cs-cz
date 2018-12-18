---
title: Vzory běžných ovládacích prvků pro sadu Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e10fdcea9819c34735f285c78a0e2ebb0650f64a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512314"
---
# <a name="common-control-patterns-for-visual-studio"></a>Vzory běžných ovládacích prvků pro sadu Visual Studio
##  <a name="BKMK_CommonControls"></a> Běžné ovládací prvky  
  
### <a name="overview"></a>Přehled  
Běžné ovládací prvky tvoří většinu uživatelského rozhraní v sadě Visual Studio. Většina běžných ovládacích prvků používaná v rozhraní sady Visual Studio by měly dodržovat [pokyny pro Windows Desktop interakci](/windows/desktop/uxguide/controls). Toto téma je specifické pro Visual Studio a zahrnuje speciální situace nebo podrobnosti, které rozšiřují tyto pokyny pro Windows.  
  
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
První věc, kterou vzít v úvahu při používání stylů pro ovládací prvky se určuje, zda ovládací prvky se použije v uživatelském rozhraní s motivem. Ovládací prvky ve standardní uživatelské rozhraní jsou – s motivem uživatelského rozhraní a musí dodržovat [stylu Normální Windows Desktop](/windows/desktop/uxguide/controls), což znamená, že nejsou opětovné použití šablon a by se měla objevit v jejich výchozí vzhled ovládacího prvku.  
  
-   **Dialogová okna Standard (nástroj):** není s motivem. Nemáte šablonu znovu. Použijte výchozí styl základního ovládacího prvku.  
  
-   **Nástroje systému windows, editory dokumentu, návrhové ploše a dialogová okna s motivem:** použít specializované s motivem vzhled pomocí služby barvu.  
  
###  <a name="BKMK_Scrollbars"></a> Posuvníky  
 Postupujte podle posuvníky [běžné vzory interakcí pro Windows posuvníky](/windows/desktop/Controls/about-scroll-bars) není-li, že jste doplněné o informace o obsahu, jako jsou v editoru kódu.  
  
###  <a name="BKMK_InputFields"></a> Vstupní pole  
 Chování typické interakce, postupujte [pokyny pro Windows Desktop pro textová pole](/windows/desktop/uxguide/ctrl-text-boxes).  
  
#### <a name="visual-style"></a>Vizuální styl  
  
-   Vstupních polí by neměly být ve stylu v dialogových oknech nástroje. Použijte základní styl vnitřní ovládací prvek.  
  
-   S motivem vstupních polí byste měli použít pouze ve s motivem dialogová okna a okna nástrojů.  
  
#### <a name="specialized-interactions"></a>Specializované interakce  
  
-   Pole jen pro čtení bude mít šedé (zakázáno) pozadí ale popředí výchozí (aktivní).  
  
-   Povinné pole by měly mít  **\<vyžaduje >** jako vodoznaky v nich. Barva pozadí s výjimkou ve výjimečných případech byste neměli měnit.  
  
-   Chyba ověřování: viz [oznámení a postup pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Vstupní pole by měla být dimenzovány pro zobrazení celého obsahu, ne na šířku okna, ve kterém jsou uvedeny ani libovolně odpovídala délce dlouhé pole, třeba cestu. Délka mohlo by to znamenat uživateli omezení jde o tom, kolik znaky jsou povoleny v poli.  
  
     ![Nesprávný vstupní pole délky: není pravděpodobné, že název bude takto dlouhé. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />Nesprávný vstupní pole délky: není pravděpodobné, že název bude takto dlouhé.
  
     ![Opravte délka vstupní pole: vstupní pole je rozumné šířku pro očekávaný obsah. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />Opravte délka vstupní pole: vstupní pole je rozumné šířku pro očekávaný obsah.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Pole se seznamem a rozevírací seznamy  
Pro typické interakce chování, postupujte [Windows Desktop pokyny pro rozevírací seznamy a pole se seznamem](/windows/desktop/uxguide/ctrl-drop).  
  
#### <a name="visual-style"></a>Vizuální styl  
  
-   V dialogových oknech nástrojů nemusíte znovu šablony ovládacího prvku. Použijte základní styl vnitřní ovládací prvek.  
  
-   Postupujte podle standardní motivy pro ovládací prvky s motivem uživatelského rozhraní, pole se seznamem a rozevírací seznamy.  
  
#### <a name="layout"></a>Rozložení  
Pole se seznamem a rozevírací seznamy by měl být dimenzovány pro zobrazení celého obsahu, ne na šířku okna, ve kterém jsou uvedeny ani libovolně odpovídala délce dlouhé pole, třeba cestu.  
  
![Nesprávný: šířka rozevíracího seznamu je příliš dlouhý pro obsah, který se zobrazí. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />Nesprávný: šířka rozevíracího seznamu je příliš dlouhý pro obsah, který se zobrazí.
  
![Správné: rozevíracího seznamu přizpůsoben pro povolit pro růst překladu, ale dlouhé zbytečně. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />Správné: rozevíracího seznamu přizpůsoben pro povolit pro růst překladu, ale dlouhé zbytečně. 
  
###  <a name="BKMK_CheckBoxes"></a> Zaškrtávací políčka  
Chování typické interakce, postupujte [pokyny pro Windows Desktop pro zaškrtávací políčka](/windows/desktop/uxguide/ctrl-check-boxes).  
  
#### <a name="visual-style"></a>Vizuální styl  
  
-   V dialogových oknech nástrojů nemusíte znovu šablony ovládacího prvku. Použijte základní styl vnitřní ovládací prvek.  
  
-   Zaškrtávací políčka v uživatelském rozhraní s motivem, postupujte podle standardní motivy pro ovládací prvky.  
  
#### <a name="specialized-interactions"></a>Specializované interakce  
  
-   Interakce se zaškrtávacím políčkem musí nikdy vyvolat přes pop dialogové okno nebo přejít do jiné oblasti.  
  
-   Zarovnejte zaškrtávací políčka se standardními hodnotami první řádek textu.  
  
     ![Nesprávný: zaškrtávací políčko je na střed textu. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />Nesprávný: zaškrtávací políčko je na střed textu.
  
     ![Správné: zaškrtávací políčko je v souladu s první řádek textu. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />Správné: zaškrtávací políčko je v souladu s první řádek textu.
  
###  <a name="BKMK_RadioButtons"></a> Přepínací tlačítka  
Chování typické interakce, postupujte [pokyny pro Windows Desktop pro přepínací tlačítka](/windows/desktop/uxguide/ctrl-radio-buttons).  
  
#### <a name="visual-style"></a>Vizuální styl  
V dialogových oknech nástrojů to není styl přepínací tlačítka. Použijte základní styl vnitřní ovládací prvek.  
  
#### <a name="specialized-interactions"></a>Specializované interakce  
Není nutné pro používání skupinového rámečku uzavřít přepínač možnosti, pokud je třeba spravovat skupiny rozdíl v těsné rozložení.  
  
###  <a name="BKMK_GroupFrames"></a> Skupiny snímků  
Chování typické interakce, postupujte [Windows Desktop pokyny pro skupinu snímků](/windows/desktop/uxguide/ctrl-group-boxes).  
  
#### <a name="visual-style"></a>Vizuální styl  
V dialogových oknech nástrojů styl skupiny snímků. Použijte základní styl vnitřní ovládací prvek.  
  
#### <a name="layout"></a>Rozložení  
  
-   Není nutné pro používání skupinového rámečku uzavřít přepínač možnosti, pokud je třeba spravovat skupiny rozdíl v těsné rozložení.  
  
-   Nikdy nepoužívejte skupinového rámečku pro jeden ovládací prvek.  
  
-   Někdy je nepřijatelné využívat vodorovná čára místo rámce kontejneru skupiny.  
  
##  <a name="BKMK_TextControls"></a> Textových ovládacích prvků

### <a name="static-text-fields"></a>Pole statického textu

Statické textové pole prezentuje informace jen pro čtení a nejde ho vybrat uživatelem. Nepoužívejte ho pro libovolný text, který uživatel může chtít zkopírovat do schránky. Jen pro čtení statický text však můžete změnit tak, aby odrážel změnu stavu. V příkladu níže je název výstupního statický text v rámci změny skupiny informace tak, aby odrážela všechny změny provedené v textovém poli kořenové Namespace nad ním.

Existují dva způsoby, jak zobrazit informace o statický text.

Statický text může být na vlastní, v dialogovém okně bez jakékoli členství ve skupině v případě nedojde ke konfliktu seskupení. Rozhodněte, pokud jsou nadbytečné řádky pole nezbytně nutné. Příkladem je zobrazení cestu k adresáři části vytvořené skupiny řádku, jak je znázorněno níže:  

![Informace o statický text v textových ovládacích prvků](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informace o statický text v textových ovládacích prvků

V dialogovém okně, kde existují další seskupené oblasti a členství ve skupině informací by pomohl čitelnost a kdy může oddíl skrytí nebo zobrazení (jako v **okno vlastností** podokno s popisem) nebo chcete být v souladu s podobným uživatelským rozhraním Umístěte statický text v poli. Toto pole skupiny by měl být jednoho pravidla a barvou `ButtonShadow`:

![Statický text v okně Vlastnosti](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Statický text v okně Vlastnosti

### <a name="read-only-text-box"></a>Textového pole určeného jen pro čtení

To umožňuje uživateli vybrat text v poli, ale nikoli upravovat. Tato textová pole jsou obrysy označující podle obvyklých 3D hranaté s `ButtonShadow` výplně.

Textové pole může být aktivní (Upravit), když uživatel změní na příslušný ovládací prvek, jako je kontrola/zrušením zaškrtnutí políčka zaškrtávací políčko nebo výběrem nebo zrušením výběru přepínače. Například v **nástroje &gt; možnosti** stránky zobrazené níže **domovskou stránku** textového pole, aktivují, když **použít výchozí** zaškrtávací políčko je zaškrtnuté políčko.

![Jen pro čtení textového pole zobrazuje aktivní a neaktivní stavy](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Jen pro čtení textového pole zobrazuje aktivní a neaktivní stavy

### <a name="using-text-in-dialogs"></a>Pomocí textu v dialogových oknech

Klíče pokynů v dialogových oknech text:

-   Popisky pro textová pole, pole se seznamem a snímků v dialogových oknech unthemed začínat sloveso, mít počáteční velké pouze první slovo a končit dvojtečkou.

    > Postupujte podle textových ovládacích prvků v dialogových oknech s motivem [splnit pravidla pro klasické pracovní plochy Windows](/windows/desktop/uxguide/top-violations) a nemusí provádět žádné koncové interpunkce, s výjimkou otazníky v odkazy na nápovědu.

-   Popisky pro možnost tlačítka a zaškrtávací políčka začínat sloveso, počáteční velká na pouze první slovo a mají bez koncové interpunkce.

-   Popisky tlačítek, nabídek, položky nabídky a karty mít počáteční velká písmena jednotlivých slov (všechna první písmena velká).

-   Popisek terminologie by měl být konzistentní s podobně jako popisky v dalších dialogových oknech.

-   Pokud je to možné mají zapisovače/editor, zapsat nebo schválit text předtím, než je pak nahlášena vývojáři pro implementaci.

-   Všechny ovládací prvky by měl mít popisky s výjimkou zvláštních okolností v tabulátor, které je dostačující.
Použití pomocné rutiny textu v případě potřeby.

### <a name="helper-text"></a>Pomocné rutiny, textu

Zahrnuté v dialogových oknech umožňující uživateli snáze pochopit účel dialogového okna nebo označíte, jakou akci chcete provést. Pomocné rutiny text by měla sloužit pouze v případě potřeby k nezahlcujte jednoduché dialogová okna. Dvě varianty pomocné rutiny, textu se dialogové okno a vodoznak.

Postupujte podle společné umístění pro pomocné rutiny, textu a pečlivě při zavádění nové oblasti. Časté scénáře pro text pomocné rutiny jsou:

-   Pomocné rutiny text v dialogových oknech, poskytnout další směr o tom, jak pracovat s komplexní dialogové okno.

-   Vodoznakového textu v oknech nástrojů prázdný nebo dialogová okna, který vysvětluje, proč se nezobrazuje žádný obsah.

-   Podokno popisu, v dolní části, jako jsou **okno vlastností**.

-   Vodoznak text v prázdné editoru, a popisují, jaká akce by měl uživatel provést začít.
  
### <a name="dialog-helper-text"></a>Dialogové okno text pomocné rutiny

Návrhář uživatelského prostředí může pomoct zjistit, zda text pomocné rutiny odpovídající. Návrhář můžete definovat, kde text pomocné rutiny se zobrazí stejně jako jeho obecné obsah. Uživatelská asistence může zápisu nebo upravit vlastní text.

### <a name="watermarks"></a>Vodoznaky

Dialogová okna výhod mírně odlišné vodoznak pokyny. Vzhledem k tomu dialogové okno se může objevit zaneprázdněný mnoho prvků uživatelského rozhraní (popisky, text nápovědy, tlačítka a další ovládací prvky kontejneru s textem), zejména pokud se zobrazí v ostatních případech černě, vodoznaky výraznější v tmavě šedé (VSColor: `ButtonShadow`). Obvykle se zobrazí v ovládacím prvku jako seznam s bílým pozadím vodoznak (VSColor: `Window`).

-   Text se zobrazí v tmavě šedé (VSColor: `ButtonShadow`). Nicméně pokud se zobrazí vodoznak na střední šedé nebo jiné barevné (VSColor: `ButtonFace`) na pozadí a je týkají o jeho čitelnost, přejděte pomocí černého textového (VSColor: `WindowText`).

-   Vodoznaky může být zarovnaný na střed nebo Zarovnané vlevo. Platí standardní pravidla při rozhodování o zarovnání. Vodoznak se nedá vybrat na pozadí.

![Příklad vodoznakového textu](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Příklad vodoznakového textu

### <a name="context-specific-dynamic-text"></a>Kontextové text (dynamické)

Dynamický text může být použité jednu ze dvou způsobů v dialogovém okně nebo nemodální uživatelského rozhraní: buď jako dynamické popisek nebo dynamický obsah.

-   Dynamické popisek: popisný panelech, které nabízejí další informace o položce vybrané v dialogovém okně, který obsahuje seznam prvků a vlastností pro tyto elementy zobrazí v mřížce doprava, jako je běžně používá dynamický text. Popisek pro vlastnost grid může být dynamický, tak, aby po výběru položky na levé straně mřížky doprava informacemi pro tuto konkrétní položku.

-   Dynamický text: může být užitečné v případech, kdy je třeba zobrazit konkrétní informace a ne pro obecný tímto způsobem, ale mělo dbát plánování.

Pokud chcete, aby uživatelé měli možnost Kopírovat informace, které, dynamické text by měl být jen pro čtení textového pole.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Tlačítka a hypertextových odkazů  
  
### <a name="overview"></a>Přehled  
Ovládací prvky tlačítka a odkaz (hypertextové odkazy) by měly dodržovat [základní pokyny k Desktopu Windows na hypertextové odkazy](/windows/desktop/uxguide/ctrl-links) za využití, formulaci, změny velikosti a mezery.  
  
### <a name="choosing-between-buttons-and-links"></a>Volba mezi tlačítka a odkazy  
Tradičně tlačítka se používají pro akce a hypertextové odkazy byly vyhrazeny pro navigaci. Tlačítka lze ve všech případech ale role odkazů došlo k rozbalení v sadě Visual Studio tak, že jsou zaměnitelné více v některých tlačítka a odkazy.  
  
Kdy použít příkazová tlačítka:  
  
-   Primární příkazy  
  
-   Zobrazení okna použitá ke shromažďování vstupu nebo rozhodování, a to i v případě, že jsou sekundární příkazy  
  
-   Destruktivní nebo nevratná akce  
  
-   Tlačítka závazku v rámci průvodců a toků  
  
Vyhněte se příkazových tlačítek v oknech nástrojů, nebo pokud potřebujete více než dvě slova pro popisek. Odkazy můžou mít delší popisky.  
  
 Kdy použít odkazy:  
  
-   Navigace k jinému oknu, dokumentu nebo webové stránky  
  
-   Situace, které vyžadují delší popisek nebo krátká věta popisující cílem akce  
  
-   Úzkou prostory, ve kterém by tlačítko zahlcovat uživatelského rozhraní, za předpokladu, že akce není destruktivní nebo nevratné  
  
-   Deaktivace zdroje, výrazná sekundární příkazy v situacích, kdy existuje mnoho příkazů  
  
#### <a name="examples"></a>Příklady  
![Příkaz odkazů použité v informačním panelu po stavovou zprávu](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />Příkaz odkazů použité v informačním panelu po stavová zpráva
  
![Odkazů použité v místní nabídce CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />Odkazů použité v místní nabídce CodeLens
  
![Odkazů použité pro sekundární příkazy, kde by tlačítka přilákat příliš mnoho pozornost](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />Odkazů použité pro sekundární příkazy, kde by tlačítka přilákat příliš mnoho pozornost
  
### <a name="common-buttons"></a>Běžné tlačítka  
  
#### <a name="text"></a>Text  
Postupujte podle pokynů na zápis v [uživatelského rozhraní text a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Vizuální styl  
  
##### <a name="standard-unthemed"></a>Standard (unthemed)  
Většina tlačítek v sadě Visual Studio se zobrazí v dialogových oknech nástrojů a by neměl být ve stylu. Standardní vzhled tlačítek odrážejí určený operační systém.  
  
##### <a name="themed"></a>S motivem  
V některých případech slouží tlačítka v rámci upravený uživatelského rozhraní a tato tlačítka musí být navržen tak, odpovídajícím způsobem. Zobrazit [dialogová okna](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) o ovládací prvky s motivem.  
  
### <a name="special-buttons"></a>Speciální tlačítka  
  
#### <a name="browse-buttons"></a>Tlačítka Procházet...  
**[Procházet...]**  tlačítka se používají v mřížkách, dialogová okna a okna nástrojů a dalších nemodální prvky uživatelského rozhraní. Zobrazí se ovládacího prvku pro výběr, který pomáhá uživateli při vyplňování hodnotu do ovládacího prvku. Existují dvě varianty toto tlačítko, dlouhé a krátké.  
  
![Na dlouhé [...] Procházet](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />Dlouhé tlačítko [Procházet...]
  
![Tlačítko jen tlačítko se třemi tečkami short [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />Tlačítko jen tlačítko se třemi tečkami short [...]
  
Kdy použít jen pro tlačítko se třemi tečkami krátký tlačítko:  
  
-   Pokud existuje více než jeden dlouhý **[Procházet...]**  tlačítko v dialogovém okně, například pokud několik polí Povolit pro procházení. Používat krátké **[...]**  tlačítko pro každý z nich matoucí přístupové klíče vytvořené v této situaci vyhnout (**& Procházet** a **B & rocházet** v dialogovém okně stejné).  
  
-   V dialogovém okně úzkou nebo neexistuje žádný přiměřené umísťovat dlouhé tlačítko.  
  
-   Je-li na tlačítko se zobrazí v ovládacím prvku grid.  
  
Pokyny, pomocí tlačítka:  
  
-   Nepoužívejte přístupový klíč. Pro přístup k ní pomocí klávesnice, musí uživatel karty sousedící ovládacího prvku. Ujistěte se, že je pořadí tak, aby žádné tlačítko pro procházení spadá ihned po pole bude vyplněn. Nikdy nepoužívejte podtržítka pod první období.  
  
-   Nastavení Microsoft Active Accessibility (MSAA) **název** vlastnost **Procházet...**  (včetně na tři tečky), který obrazovky čtenáři budou číst ho jako "Procházet" a "tečka – tečka – tečka" nebo "období období období." Pro spravované ovládací prvky, to znamená, že nastavení **AccessibleName** vlastnost.  
  
-   Nikdy nepoužívejte trojtečka **[...]**  tlačítko pro všechno, co s výjimkou procházení akce. Například, pokud potřebujete **[nový …]**  tlačítko, ale nemají dostatek volného místa pro text, pak dialogového okna musí být přepracován.  
  
##### <a name="sizing-and-spacing"></a>Dimenzování a mezery  
![Tlačítka pro změnu velikosti [Procházet...]: standardní verze je 75 × 23 pixelů, zkrácený je 26 × 23 pixelů](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />Tlačítka pro změnu velikosti [Procházet...]
  
![Tlačítka [Procházet...] mezery: mezery mezi související ovládací prvek a standardní tlačítko 7 pixelů procházet, mezery mezi související ovládací prvek a krátký procházet tlačítko 5 pixelů](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />Mezery mezi tlačítka [Procházet...]
  
#### <a name="graphical-buttons"></a>Grafické tlačítka  
Některá tlačítka by měla vždy použít grafické image a nikdy obsahovat text ušetřit místo a vyhnout se potíže s lokalizací. Často používají v jiných seřaditelné seznamy a pole výběr.  
  
> **Poznámka:** uživatelé mají na kartě tato tlačítka (neexistují žádné přístupové klíče), takže je umístit v rozumné pořadí. Mapování `name` vlastnosti tlačítka na akci, která je potřebná tak, aby čtečky obrazovky správně interpretovat akce tlačítka.  
  
| Funkce | Tlačítko |  
| --- | --- |  
| Přidejte | ![Grafické tlačítko "Přidat"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| odebrat | ![Grafické tlačítko "Remove"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| Přidat vše | ![Grafické tlačítko "Přidat vše"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| Odebrat vše | ![Grafické "Odstranit vše" tlačítko](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| Přesunout nahoru | ![Grafické tlačítko "Nahoru"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| Přesunout dolů | ![Grafické "tlačítko Přesunout dolů"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| Odstranit | ![Grafické tlačítko "Odstranit"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Dimenzování a mezery  
Změny velikosti pro grafické tlačítka je stejná jako zkrácené **[Procházet...]**  tlačítko (26 × 23 pixelů):  
  
![Vzhled grafického obrázku na tlačítku a nemusíte průhlednou barvu zobrazující](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />Vzhled grafického obrázku na tlačítku a nemusíte průhlednou barvu zobrazující
  
### <a name="hyperlinks"></a>Hypertextové odkazy  
Hypertextové odkazy se skvěle hodí pro navigaci na základě akce, jako jsou otevření tématu nápovědy, modální dialogové okno nebo průvodce. Pokud hypertextový odkaz se používá pro příkaz, je vždy zobrazit viditelné a výrazné změny v uživatelském rozhraní. Obecně platí akce, které se zavázali k akci (třeba uložit, zrušit a odstranit) se lépe předávají pomocí tlačítka.  
  
#### <a name="writing-style"></a>Styl psaní  
Postupujte podle [Windows Desktop pokyny pro text v uživatelském rozhraní](/windows/desktop/uxguide/text-ui). Nepoužívejte "Přečtěte si další informace o," "Řekněte mi více o" nebo "Get s tímto vám pomůže" frázového. Místo toho věta text nápovědy odkazu z hlediska primární otázku zodpoví technický obsah nápovědy. Například "**jak mohu přidat server do Průzkumníka serveru?**"  
  
#### <a name="visual-style"></a>Vizuální styl  
  
-   Hypertextové odkazy vždy používejte [VSColor službu](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Pokud není správně ve stylu hypertextového odkazu, bliká červená, pokud je aktivní nebo ukazuje na jinou barvu po přístupu.  
  
-   Nezahrnují podtržení v ovládacím prvku není odkaz na fragment věty úplné větě, stejně jako v vodoznak, aby byla stavu.  
  
-   Podtržení by se neměl zobrazit při najetí myší. Místo toho zpětná vazba pro uživatele, že je odkaz aktivní je změna mírné barvy a kurzoru příslušný odkaz.  
  
##  <a name="BKMK_TreeViews"></a> Zobrazení stromu  
  
Zobrazení stromu poskytují způsob, jak uspořádat komplexní seznamy do skupin nadřazených a podřízených. Uživatele můžete rozbalit nebo sbalit nadřazené skupiny, které chcete zobrazit nebo skrýt základní podřízené položky. Poskytnout další akce lze vybrat každou položku v zobrazení stromu.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Stromové zobrazení vizuálního stylu  
  
#### <a name="expanders"></a>Rozšíření  
Ovládací prvky zobrazení stromu by měl odpovídat rozšíření návrh používá Windows a Visual Studio. Chcete-li zobrazit nebo skrýt základní položky, používají jednotlivé uzly ovládacího prvku expander. Použití ovládacího prvku expander poskytuje konzistenci pro uživatele, kteří se mohou vyskytnout jiného stromu zobrazení v rámci Windows a Visual Studio.  
  
![Správné: správný styl zobrazení uzlu stromové struktury pomocí ovládacího prvku expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Správné: správný styl zobrazení uzlu stromové struktury pomocí ovládacího prvku expander
  
![Chyba: nesprávný styl stromovém zobrazení](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />Chyba: nesprávný styl stromovém zobrazení
  
#### <a name="selection"></a>Výběr  
Když je vybrán uzel ve stromovém zobrazení, zvýraznění by měl rozšířit na celou šířku ovládací prvek stromového zobrazení. Díky tomu uživatelé se tak jasně identifikovat položky, které jste vybrali. Výběr barvy by měly odrážet aktuální motiv sady Visual Studio.  
  
![Správné: zvýraznění z vybraného uzlu odpovídá celé jeho šířce ovládací prvek stromového zobrazení. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Správné: zvýraznění z vybraného uzlu odpovídá celé jeho šířce ovládací prvek stromového zobrazení.
  
![Chyba: zvýraznění z vybraného uzlu nevejde celé jeho šířce ovládací prvek stromového zobrazení. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />Chyba: zvýraznění z vybraného uzlu nevejde celé jeho šířce ovládací prvek stromového zobrazení.
  
#### <a name="icons"></a>Ikony  
Ikony by měla sloužit pouze v ovládacích prvcích stromů zobrazení Pokud podílí na vizuální určení rozdílů mezi položkami. Obecně platí ikony, které byste měli použít pouze ve heterogenní seznamy, ve kterých ikony nesou informaci k rozlišení mezi typy prvků. V homogenní seznamu pomocí ikon, často se dají považovat za šumu a mělo by se vyhnout. V takovém případě ikona skupiny (nadřazené) sdělí typem položek v něm. Výjimkou z tohoto pravidla by Pokud ikonu je dynamický a slouží k určení stavu.  
  
#### <a name="scroll-bars"></a>Posuvníky  
Posuvníky vždy skryt, pokud se obsah vešel ovládací prvek stromového zobrazení. Je přijatelné pro posuvníky se seznamy skrytých nebo poloprůhledného posuvného okna a zobrazí, když okno obsahující stromové zobrazení má fokus nebo při přechodu ze stromu zobrazení samotný.  
  
![Protože obsah překročil omezení ovládací prvek stromového zobrazení, zobrazí se i vodorovné a svislé posuvníky. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />Protože obsah překročil omezení ovládací prvek stromového zobrazení, zobrazí se i vodorovné a svislé posuvníky.
  
###  <a name="BKMK_TreeViewInteractions"></a> Stromové zobrazení interakce  
  
#### <a name="context-menus"></a>Kontextové nabídky  
Uzel stromu zobrazení může odhalit podnabídky možnosti v kontextové nabídce. Obvykle k tomu dojde, když uživatel má klikli pravým tlačítkem myši položku nebo stisknutím klávesy nabídky na Windows klávesnice s zvolené položky. Je důležité, že uzel získá fokus a je vybrán. To pomáhá uživateli určit která položka patří podnabídky.  
  
![Byla vybrána položka, která se má generovat fokus místní nabídky zisky upozornit uživatele, která položka. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />Byla vybrána položka, která se má generovat fokus místní nabídky zisky upozornit uživatele, která položka.
  
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
Trid ovládacího prvku je komplexní ovládací prvek, který obsahuje zobrazení stromu v mřížce. Rozšíření, sbalování a procházení stromu by měly dodržovat stejné klávesových příkazů jako stromové zobrazení, s těmito přídavky:  
  
-   **Šipka doprava:** rozbalte uzel. Po rozbalení uzlu pokračováním, že přejdete na nejbližší sloupec na pravé straně. Na konci řádku, který by se měla zastavit navigace.  
  
-   **Karta:** Navigates na nejbližší buňku na pravé straně.  Na konci řádku navigace pokračuje na další řádek.  
  
-   **Shift + Tab:** Navigates na nejbližší buňku na levé straně.  Na začátku řádku, bude nadále navigace buňku vpravo na předchozím řádku.  
  
![Trid ovládací prvek v sadě Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Trid ovládací prvek v sadě Visual Studio