---
title: Běžné vzory ovládacích prvku pro sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698712"
---
# <a name="common-control-patterns-for-visual-studio"></a>Vzory běžných ovládacích prvků pro Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Běžné ovládací prvky

### <a name="overview"></a>Přehled
Běžné ovládací prvky tvoří většinu uživatelského rozhraní v sadě Visual Studio. Nejběžnější ovládací prvky používané v rozhraní sady Visual Studio by měly dodržovat [pokyny pro interakci na ploše systému Windows](/windows/desktop/uxguide/controls). Toto téma je specifické pro Visual Studio a zahrnuje zvláštní situace nebo podrobnosti, které rozšiřují tyto pokyny systému Windows.

#### <a name="common-controls-in-this-topic"></a>Běžné ovládací prvky v tomto tématu

- [Posuvníky](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Vstupní pole](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Pole se seznamem a rozevírací seznamy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Políčka](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Přepínače](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Skupinové rámce](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Ovládací prvky textu](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Tlačítka a hypertextové odkazy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Stromové pohledy](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Vizuální styl
První věc, kterou je třeba zvážit při stylingovládacích prvků je, zda ovládací prvky budou použity v tematou uI. Ovládací prvky ve standardním uživatelském rozhraní jsou uživatelské rozhraní bez motivů a musí se řídit [normálním stylem plochy systému Windows](/windows/desktop/uxguide/controls), což znamená, že nejsou znovu přeloženy a měly by se zobrazit ve výchozím vzhledu ovládacího prvku.

- **Standardní (utility) dialogy:** není tématika. Nepřepojuj šablonu. Použijte základní výchozí nastavení stylu ovládacího prvku.

- **Okna nástrojů, editory dokumentů, návrhové povrchy a tematou dialogová okna:** Použijte speciální tematou vzhled pomocí služby barev.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Posuvníky
 Posuvníky by se měly řídit [běžnými vzory interakce pro posuvníky Windows,](/windows/desktop/Controls/about-scroll-bars) pokud nejsou rozšířeny o informace o obsahu, jako v editoru kódu.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Vstupní pole
 Pro typické chování interakce postupujte podle [pokynů pro plochu systému Windows pro textová pole](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Vizuální styl

- Vstupní pole by neměla být stylizována v dialogových oknech nástroje. Použijte základní styl vnitřní ovládacího prvku.

- Tématová vstupní pole by měla být používána pouze v tematých dialogových oknech a oknech nástrojů.

#### <a name="specialized-interactions"></a>Specializované interakce

- Pole jen pro čtení budou mít šedé (zakázané) pozadí, ale výchozí (aktivní) popředí.

- Povinná pole ** \<** by měla mít požadované>jako vodoznaky v nich. Barvu pozadí byste neměli měnit s výjimkou vzácných situací.

- Ověření chyb: Viz [Oznámení a průběh pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Vstupní pole by měla být dimenzována tak, aby odpovídala obsahu, ne odpovídala šířce okna, ve kterém jsou zobrazena, ani by měla libovolně odpovídat délce dlouhého pole, jako je cesta. Délka může být pro uživatele údaj o omezení, kolik znaků je povoleno v poli.

     ![Nesprávná délka vstupního pole: je nepravděpodobné, že název bude tak dlouhý.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Nesprávná délka vstupního pole: je nepravděpodobné, že název bude tak dlouhý.

     ![Správná délka vstupního pole: vstupní pole má přiměřenou šířku pro očekávaný obsah.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Správná délka vstupního pole: vstupní pole má přiměřenou šířku pro očekávaný obsah.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Pole se seznamem a rozevírací seznamy
Pro typické chování interakce postupujte podle [pokynů pro plochu systému Windows pro rozevírací seznamy a pole se seznamem](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech nástroje nepřehozujete ovládací prvek znovu. Použijte základní styl vnitřní ovládacího prvku.

- V tematizovaném ujmu postupujte podle pole se seznamem a rozevíracích seznamů podle standardních témat ovládacích prvků.

#### <a name="layout"></a>Rozložení
Pole se seznamem a rozevírací seznamy by měly být dimenzovány tak, aby odpovídaly obsahu, aby neodpovídaly šířce okna, ve kterém jsou zobrazeny, ani libovolně odpovídaly délce dlouhého pole, jako je cesta.

![Nesprávné: rozevírací šířka je příliš dlouhá pro obsah, který se zobrazí.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Nesprávné: rozevírací šířka je příliš dlouhá pro obsah, který se zobrazí.

![Správně: rozevírací možnost je dimenzována tak, aby umožňovala růst překladů, ale ne zbytečně dlouhá.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Správně: rozevírací možnost je dimenzována tak, aby umožňovala růst překladů, ale ne zbytečně dlouhá.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Políčka
Pro typické chování interakce postupujte podle [pokynů pro plochu systému Windows pro zaškrtávací políčka](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech nástroje nepřehozujete ovládací prvek znovu. Použijte základní styl vnitřní ovládacího prvku.

- V tematizovaném uj., zaškrtávací políčka postupujte podle standardního tématu pro ovládací prvky.

#### <a name="specialized-interactions"></a>Specializované interakce

- Interakce se zaškrtávací políčko nesmí nikdy otevřít dialog nebo přejít do jiné oblasti.

- Zaškrtávací políčka zarovná se účaří prvního řádku textu.

     ![Nesprávné: zaškrtávací políčko je vystředěno na text.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Nesprávné: zaškrtávací políčko je vystředěno na text.

     ![Správně: zaškrtávací políčko je zarovnáno s prvním řádkem textu.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Správně: zaškrtávací políčko je zarovnáno s prvním řádkem textu.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Přepínače
Pro typické chování interakce postupujte podle [pokynů pro přepínací tlačítka na ploše systému Windows](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Vizuální styl
V dialogových oknech nástroje nepoužívejte přepínací tlačítka. Použijte základní styl vnitřní ovládacího prvku.

#### <a name="specialized-interactions"></a>Specializované interakce
Není nutné používat skupinový rámeček k uzavření voleb rádia, pokud nepotřebujete zachovat skupinové rozlišení v těsném rozložení.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Skupinové rámce
Pro typické chování interakce postupujte podle [pokynů pro skupinové rámce systému Windows Desktop](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Vizuální styl
V dialogových oknech nástrojů nestylové skupinové rámečky. Použijte základní styl vnitřní ovládacího prvku.

#### <a name="layout"></a>Rozložení

- Není nutné používat skupinový rámeček k uzavření voleb rádia, pokud nepotřebujete zachovat skupinové rozlišení v těsném rozložení.

- Nikdy nepoužívejte skupinový rámec pro jeden ovládací prvek.

- Někdy je přijatelné použít vodorovné pravidlo namísto kontejneru skupinového rámce.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Ovládací prvky textu

### <a name="static-text-fields"></a>Statická textová pole

Statické textové pole obsahuje informace jen pro čtení a uživatel je nemůže vybrat. Nepoužívejte jej pro jakýkoli text, který by uživatel chtěl zkopírovat do schránky. Statický text jen pro čtení však může změnit tak, aby odrážel změnu stavu. V níže uvedeném příkladu se statický text Výstupní název pod skupinou Informace změní tak, aby odrážel všechny změny provedené v textovém poli Kořenový obor názvů nad ním.

Existují dva způsoby zobrazení statických textových informací.

Statický text může být sám o sobě v dialogovém okně bez jakéhokoli uzavření, pokud nedojde ke konfliktu seskupení. Rozhodněte se, zda jsou další řádky krabice opravdu nezbytné. Příkladem je zobrazení cesty k adresáři v oddílu vytvořeném skupinovým řádkem, jak je znázorněno níže:

![Statické informace o textu v ovládacích prvcích textu](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "Zobrazení statickou text.png")<br />Statické informace o textu v ovládacích prvcích textu

V dialogovém okně, kde existují jiné seskupené oblasti a uzavření informací by pomohlo čitelnost a když oddíl může být skrytý nebo zobrazen (jako v podokně popis **okna vlastnosti)** nebo chcete-li být konzistentní s podobným ui, umístěte statický text uvnitř pole. Toto skupinové pole by mělo být `ButtonShadow`jedno pravidlo a barevné s :

![Statický text v okně Vlastnosti](../../extensibility/ux-guidelines/media/PropertiesWindow.png "VlastnostiWindow.png")<br />Statický text v okně Vlastnosti

### <a name="read-only-text-box"></a>Textové pole jen pro čtení

To umožňuje uživateli vybrat text uvnitř pole, ale ne upravovat. Tato textová pole jsou ohraničena obvyklým 3D `ButtonShadow` dlátem s výplní.

Textové pole se může stát aktivním (upravitelným), když uživatel změní přidružený ovládací prvek, například zaškrtnutí/zrušení zaškrtnutí políčka nebo výběr/zrušení výběru přepínacího tlačítka. Například na stránce **Možnosti nástrojů &gt; ** zobrazené níže se textové pole Na domovské **stránce** aktivuje, když není zaškrtnuto políčko **Použít výchozí.**

![Textové pole jen pro čtení s neaktivními a aktivními stavy](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Textové pole jen pro čtení s neaktivními a aktivními stavy

### <a name="using-text-in-dialogs"></a>Použití textu v dialogových oknech

Hlavní směry textu v dialogových oknech:

- Popisky textových polí, seznamů a rámečků v dialogových oknech bez tématikou začínají slovesem, mají počáteční velké písmeno pouze pro první slovo a končí dvojtečkou.

    > Textové ovládací prvky v tematických dialogových oknech postupujte podle [pokynů pro uživatelské prostředí pro plochu systému Windows](/windows/desktop/uxguide/top-violations) a nezabírají koncovou interpunkci, s výjimkou otazníků v odkazech nápovědy.

- Popisky zaškrtávacích políček a přepínačů začínají slovesem, počátečním velkým písmenem pouze pro první slovo a nemají koncovou interpunkci.

- Popisky tlačítek, nabídek, položek nabídky a karet mají počáteční velká písmena pro každé slovo (případ nadpisu).

- Terminologie popisků by měla být konzistentní s podobnými popisky v jiných dialogových oknech.

- Pokud je to možné, mají zapisovač /editor napsat nebo schválit text před tím, než přejde vývojářpro implementaci.

- Všechny ovládací prvky by měly mít popisky s výjimkou zvláštních okolností, za kterých je tabulátor y dostatečné.
V případě potřeby použijte pomocné texty.

### <a name="helper-text"></a>Pomocné texty

Zahrnuty v dialogových oknech pomoci uživateli pochopit účel dialogového okna nebo označit, které akce provést. Pomocný text by měl být používán pouze v případě potřeby, aby se zabránilo zahlcení jednoduchých dialogových oken. Dvě varianty pomocného textu jsou dialog a vodoznak.

Postupujte podle běžných umístění pro pomocné text a být selektivní při zavádění nových oblastí. Běžné scénáře pro pomocné texty jsou:

- Pomocný text v dialogových oknech, aby další směr o tom, jak pracovat se složitým dialogem.

- Vodoznak textu v prázdných oknech nástrojů nebo dialogových oknech, které vysvětlují, proč není zobrazen žádný obsah.

- Podokno popisu, například v dolní části **okna Vlastnosti**.

- Vodoznak text v prázdném editoru, aby vysvětlil, jaké akce by měl uživatel provést, aby mohli začít.

### <a name="dialog-helper-text"></a>Text pomocníka dialogu

Návrhář uživatelského prostředí může pomoci určit, kdy je vhodný text pomocníka. Návrhář může definovat, kde se zobrazí pomocný text, stejně jako jeho obecný obsah. Uživatelská pomoc může psát / upravovat skutečný text.

### <a name="watermarks"></a>Vodoznaky

Dialogová okna využívají mírně odlišné pokyny pro vodoznak. Vzhledem k tomu, že se dialogové okno může jevit zaneprázdněné mnoha prvky uživatelského rozhraní (popisky, text nápovědy, `ButtonShadow`tlačítka a další ovládací prvky kontejneru s textem), zejména pokud se zobrazují černě, vodoznaky lépe vystupují v tmavě šedé barvě (VSColor: ). Obvykle se uvnitř ovládacího prvku zobrazí vodoznak jako seznam `Window`s bílým pozadím (VSColor: ).

- Text se zobrazí tmavě šedě (VSColor: `ButtonShadow`). Pokud se však vodoznak objeví na středně šedém `ButtonFace`nebo jiném barevném (VSColor: ) pozadí a `WindowText`existují obavy o jeho čitelnost, jděte s černým textem (VSColor: ).

- Vodoznaky mohou být vystředěny nebo zapuštěny doleva. Při rozhodování o zarovnání použijte standardní pravidla návrhu. Vodoznak nelze vybrat na pozadí.

![Příklad textu vodoznaku](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Příklad textu vodoznaku

### <a name="context-specific-dynamic-text"></a>Kontextově specifický (dynamický) text

Dynamický text lze použít jedním ze dvou způsobů v dialogovém okně nebo nemodálním uzemním: buď jako dynamický popisek, nebo jako dynamický obsah.

- Dynamický popisek: dynamické použití dynamického textu je v popisných panelech, které nabízejí více informací pro vybranou položku, například v dialogovém okně, které obsahuje seznam prvků a vlastností pro tyto prvky zobrazené v mřížce vpravo. Popisek mřížky vlastností může být dynamický, takže když je položka vybrána vlevo, mřížka vpravo zobrazuje informace pro tuto konkrétní položku.

- Dynamický text: může být užitečný v případech, kdy potřebujete zobrazit konkrétní informace a ne obecné informace tímto způsobem, ale je třeba dbát na to, abyste je nepoužívali nadměrně.

Pokud chcete, aby uživatelé měli možnost kopírovat informace, dynamický text by měl být v textovém poli jen pro čtení.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Tlačítka a hypertextové odkazy

### <a name="overview"></a>Přehled
Tlačítka a ovládací prvky odkazů (hypertextové odkazy) by se měly řídit [základními pokyny pro použití,](/windows/desktop/uxguide/ctrl-links) formulaci, velikost a mezery na ploše systému Windows Desktop.

### <a name="choosing-between-buttons-and-links"></a>Výběr mezi tlačítky a odkazy
Tlačítka byla tradičně používána pro akce a hypertextové odkazy byly vyhrazeny pro navigaci. Tlačítka mohou být použity ve všech případech, ale role odkazů byla rozšířena v sadě Visual Studio tak, aby tlačítka a odkazy jsou zaměnitelné za určitých podmínek.

Kdy použít příkazová tlačítka:

- Primární příkazy

- Zobrazení oken používaných ke shromažďování vstupů nebo rozhodování, i když se jedná o sekundární příkazy

- Destruktivní nebo nevratné akce

- Tlačítka závazků v rámci průvodců a toků stránek

Vyhněte se příkazových tlačítek v oknech nástrojů, nebo pokud potřebujete více než dvě slova pro popisek. Odkazy mohou mít delší popisky.

 Kdy použít odkazy:

- Navigace do jiného okna, dokumentu nebo webové stránky

- Situace, které vyžadují delší popisek nebo krátkou větu k popisu záměru akce

- Stísněné prostory, kde by tlačítko zahltilo uI, za předpokladu, že akce není destruktivní nebo nevratné

- Odstranění zdůraznění sekundárních příkazů v situacích, kdy existuje mnoho příkazů

#### <a name="examples"></a>Příklady
![Příkazové odkazy použité na informačním panelu za stavovou zprávou](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Příkazové odkazy použité na informačním panelu za stavovou zprávou

![Odkazy použité v místní přiskupovacím panelu CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Odkazy použité v místní přiskupovacím panelu CodeLens

![Odkazy používané pro sekundární příkazy, kde by tlačítka přitahovala příliš velkou pozornost](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Odkazy používané pro sekundární příkazy, kde by tlačítka přitahovala příliš velkou pozornost

### <a name="common-buttons"></a>Běžná tlačítka

#### <a name="text"></a>Text
Postupujte podle pokynů pro psaní v [textu a terminologii ui](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Vizuální styl

##### <a name="standard-unthemed"></a>Standardní (bez tématiky)
Většina tlačítek v sadě Visual Studio se zobrazí v dialogových oknech nástroje a neměla by být stylizována. Měly by odrážet standardní vzhled tlačítek, jak je diktován operačním systémem.

##### <a name="themed"></a>Tématickém
V některých případech mohou být tlačítka použita v rámci stylizovaného ui a tato tlačítka musí být správně stylizována. Informace o tematých ovládacích prvcích naleznete v [části Dialogy.](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

### <a name="special-buttons"></a>Speciální tlačítka

#### <a name="browse-buttons"></a>Procházet... Tlačítka
**[Procházet...]** tlačítka se používají v mřížkách, dialogových oknech a oknech nástrojů a dalších nemodálních prvcích uživatelského rozhraní. Zobrazí výběr, který pomáhá uživateli při vyplňování hodnoty do ovládacího prvku. Existují dvě varianty tohoto tlačítka, dlouhé a krátké.

![Dlouhé tlačítko [Procházet...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Dlouhé tlačítko [Procházet...]

![Tlačítko jen pro tři tečky je krátké [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Tlačítko jen pro tři tečky je krátké [...]

Kdy použít krátké tlačítko pouze se třemi tečkami:

- Pokud je v dialogovém okně více než jedno dlouhé tlačítko **[Procházet...],** například když procházení umožňuje několik polí. Použijte krátké **tlačítko [...]** pro každý, aby se zabránilo matoucí přístupové klávesy vytvořené touto situací** (&Procházet** a **B&řádek** ve stejném dialogu).

- V těsném dialogu, nebo když není rozumné místo, aby dlouhé tlačítko.

- Pokud se tlačítko zobrazí v ovládacím prvku mřížky.

Pokyny pro použití tlačítka:

- Nepoužívejte přístupový klíč. Chcete-li k němu přistupovat pomocí klávesnice, musí uživatel kartu z přilehlého ovládacího prvku. Ujistěte se, že pořadí polí je takové, že jakékoli tlačítko procházet spadá ihned za pole, které bude vyplnit. Nikdy nepoužívejte podtržítko pod první periodou.

- Nastavte vlastnost **Název** funkce Microsoft Active Accessibility (MSAA) na **procházet...** (včetně tři tečky), aby ji programy pro čtení z obrazovky četly jako "Procházet" a nikoli jako "tečka-tečka" nebo "tečka období". Pro spravované ovládací prvky to znamená nastavení vlastnosti **AccessibleName.**

- Nikdy nepoužívejte tlačítko tři tečky **[...]** pro nic jiného než procházet akci. Pokud například potřebujete tlačítko **[New...],** ale nemáte dostatek místa pro text, je třeba dialogové okno přepracovat.

##### <a name="sizing-and-spacing"></a>Dimenzování a rozestupy
![Dimenzování [Procházet...] tlačítka: standardní verze je 75x23 pixelů, krátká verze je 26x23 pixelů](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Změna velikosti [Procházet...] tlačítka

![Mezery [Procházet...] tlačítka: mezery mezi souvisejícím ovládacím prvkem a standardním tlačítkem Procházet 7 pixelů, mezery mezi souvisejícím ovládacím prvkem a krátkým tlačítkem Procházet 5 pixelů](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Mezery [Procházet...] tlačítka

#### <a name="graphical-buttons"></a>Grafická tlačítka
Některá tlačítka by měla vždy používat grafický obrázek a nikdy obsahovat text pro úsporu místa a vyhnout se problémům s lokalizací. Ty se často používají v polích výběru a dalších seřaditelných seznamech.

> [!NOTE]
> Uživatelé musí kartu na tato tlačítka (nejsou k dispozici žádné přístupové klávesy), takže je umístěte v rozumném pořadí. Namapujte `name` vlastnost tlačítka na akci, kterou provede, aby programy pro čtení z obrazovky správně interpretovaly akci tlačítka.

| Funkce | Tlačítko |
| --- | --- |
| Přidat | ![Grafické tlačítko "Přidat"](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Odebrat | ![Grafické tlačítko "Odebrat"](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Přidat vše | ![Grafické tlačítko "Přidat vše"](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Odebrat vše | ![Grafické tlačítko "Odebrat vše"](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Přesunout nahoru | ![Grafické tlačítko "Přesunout nahoru"](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Přesunout dolů | ![Grafické tlačítko "Přesunout dolů"](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Odstranit | ![Grafické tlačítko "Smazat"](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Dimenzování a rozestupy
Velikost grafických tlačítek je stejná jako u krátké verze tlačítka **[Procházet...]** (26 x 23 pixelů):

![Vzhled grafického obrázku na tlačítku, se zobrazenou průhlednou barvou a bez ní](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Vzhled grafického obrázku na tlačítku, se zobrazenou průhlednou barvou a bez ní

### <a name="hyperlinks"></a>Hypertextové odkazy
Hypertextové odkazy jsou vhodné pro akce založené na navigaci, jako je otevření tématu nápovědy, modální dialog nebo průvodce. Pokud hypertextový odkaz se používá pro příkaz, by měl vždy zobrazit viditelné a znatelné změny v ui. Obecně platí, že akce, které se zavazují k akci (například Uložit, Zrušit a Odstranit), jsou lépe komunikovány pomocí tlačítka.

#### <a name="writing-style"></a>Styl psaní
Text uživatelského rozhraní naleznete v [pokynech k ploše systému Windows](/windows/desktop/uxguide/text-ui). Nepoužívejte formulace "Další informace o tom", "Řekněte mi o tom" nebo "Získat s tímto pomoc". Místo toho fráze Text nápovědy odkaz z hlediska primární otázku odpověděl obsah nápovědy. Například "**Jak přidám server do Průzkumníka serveru?**"

#### <a name="visual-style"></a>Vizuální styl

- Hypertextové odkazy by měly vždy používat [službu VSColor .](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService) Pokud hypertextový odkaz není stylizován správně, bliká červeně, když je aktivní, nebo po návštěvě zobrazí jinou barvu.

- Nezahrnujte podtržení v klidovém stavu ovládacího prvku, pokud odkaz není fragment věty v rámci celé věty, jako ve vodoznaku.

- Podtržení by se při najetí by se nemělo zobrazovat při najetých písmenech. Místo toho zpětná vazba pro uživatele, že odkaz je aktivní je mírné změny barvy a příslušný kurzor odkazu.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Stromové pohledy

Stromová zobrazení poskytují způsob uspořádání složitých seznamů do nadřazených skupin. Uživatel může rozbalit nebo sbalit nadřazené skupiny, aby odhalil nebo skryl podkladové podřízené položky. Každá položka ve stromovém zobrazení může být vybrána tak, aby poskytovala další akci.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Vizuální styl stromového zobrazení

#### <a name="expanders"></a>Expandéry
Ovládací prvky stromového zobrazení by měly odpovídat návrhu expandéru používanému systémem Windows a visual studio. Každý uzel používá ovládací prvek expanderu k odhalení nebo skrytí podkladových položek. Použití ovládacího prvku expandéru poskytuje konzistenci pro uživatele, kteří mohou setkat s různými zobrazeními stromu v systému Windows a sady Visual Studio.

![Správně: správný styl uzlu stromového zobrazení pomocí ovládacího prvku expanderu](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Správně: správný styl uzlu stromového zobrazení pomocí ovládacího prvku expanderu

![Nesprávné: nesprávný styl uzlu stromového zobrazení](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Nesprávné: nesprávný styl uzlu stromového zobrazení

#### <a name="selection"></a>Výběr
Pokud je uzel vybrán ve stromovém zobrazení, zvýraznění by se mělo rozšířit na celou šířku ovládacího prvku stromového zobrazení. To pomáhá uživatelům jasně určit, kterou položku vybrali. Barvy výběru by měly odrážet aktuální motiv sady Visual Studio.

![Správně: zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Správně: zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.

![Nesprávné: Zvýraznění vybraného uzlu neodpovídá celé šířce ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Nesprávné: Zvýraznění vybraného uzlu neodpovídá celé šířce ovládacího prvku stromového zobrazení.

#### <a name="icons"></a>Ikony
Ikony by měly být použity pouze v ovládacích prvcích zobrazení stromu, pokud pomáhají vizuálně identifikovat rozdíly mezi položkami. Obecně platí, že ikony by měly být používány pouze v heterogenních seznamech, ve kterých ikony nesou informace k rozlišení typů prvků. V homogenním seznamu pomocí ikon lze často považovat za šum a je třeba se jim vyhnout. V takovém případě může ikona skupiny (nadřazená položka) sdělit typ položek v ní. Výjimkou z tohoto pravidla by bylo, pokud je ikona dynamická a používá se k označení stavu.

#### <a name="scroll-bars"></a>Posuvníky
Posuvníky by měly být vždy skryté, pokud obsah zapadá do ovládacího prvku stromového zobrazení. Je přijatelné, aby posuvníky byly skryté nebo poloprůhledné v posuvitelném okně a zobrazily se, když má okno obsahující stromové zobrazení fokus nebo při přechodu samotného zobrazení stromu.

![Svislé i vodorovné posuvníky jsou zobrazeny, protože obsah překročil limity ovládacího prvku stromového zobrazení.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Svislé i vodorovné posuvníky jsou zobrazeny, protože obsah překročil limity ovládacího prvku stromového zobrazení.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interakce stromového zobrazení

#### <a name="context-menus"></a>Místní nabídky
Uzel stromového zobrazení může odhalit možnosti podnabídky v místní nabídce. Obvykle k tomu dochází, když uživatel klepne pravým tlačítkem myši na položku nebo stiskne klávesu Nabídka na klávesnici systému Windows s vybranou položkou. Je důležité, aby uzel získá fokus a je vybrán. To pomáhá uživateli určit, ke které položce podnabídka patří.

![Položka, která vygenerovala kontextovou nabídku, získá fokus, aby upozornila uživatele, která položka byla vybrána.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Položka, která vygenerovala kontextovou nabídku, získá fokus, aby upozornila uživatele, která položka byla vybrána.

#### <a name="keyboard"></a>Klávesnice
Stromové zobrazení by mělo poskytovat možnost výběru položek a rozbalení/sbalení uzlů pomocí klávesnice. Tím je zajištěno, že navigace splňuje naše požadavky na přístupnost.

##### <a name="tree-view-control"></a>Ovládací prvek stromového zobrazení
Ovládací prvky stromu sady Visual Studio by měly podle běžných navigačních prvků klávesnice:

- **Šipka nahoru:** Výběr položek posunutím do stromu

- **Šipka dolů:** Výběr položek posunutím dolů po stromě

- **Šipka doprava:** Rozbalení uzlu ve stromu

- **Šipka doleva:** Sbalení uzlu ve stromu

- **Zadejte klíč:** Zahájit, načíst, spustit vybranou položku

##### <a name="trid-tree-view-and-grid-view"></a>Trid (stromové zobrazení a zobrazení mřížky)
Ovládací prvek trid je komplexní ovládací prvek, který obsahuje stromové zobrazení v rámci mřížky. Rozbalení, sbalení a navigace ve stromu by měly respektovat stejné příkazy klávesnice jako stromové zobrazení s následujícími dodatky:

- **Šipka doprava:** Rozbalte uzel. Po rozbalení uzlu by měl pokračovat v navigaci k nejbližšímu sloupci vpravo. Navigace by se měla zastavit na konci řádku.

- **Karta:** Přejde na nejbližší buňku vpravo.  Na konci řádku navigace pokračuje na další řádek.

- **Shift + Karta:** Přejde na nejbližší buňku vlevo.  Na začátku řádku navigace pokračuje do buňky zcela vpravo v předchozím řádku.

![Ovládací prvek trid v sadě Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Ovládací prvek trid v sadě Visual Studio
