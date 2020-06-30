---
title: Vzory běžných ovládacích prvků
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547443"
---
# <a name="common-control-patterns-for-visual-studio"></a>Vzory běžných ovládacích prvků pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Běžné ovládací prvky

### <a name="overview"></a>Přehled
 Běžné ovládací prvky tvoří většinu uživatelského rozhraní v aplikaci Visual Studio. Nejběžnější ovládací prvky používané v rozhraní sady Visual Studio by měly dodržovat [pokyny pro interakci s plochou pro Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Tento dokument je specifický pro Visual Studio a popisuje zvláštní situace nebo podrobnosti, které rozšiřují tyto pokyny pro Windows.

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
 První věc, kterou je třeba vzít v úvahu při určení stylu, je, zda budou ovládací prvky použity v uživatelském rozhraní motivů. Ovládací prvky ve standardním uživatelském rozhraní jsou netematické uživatelské rozhraní a musí dodržovat [normální styl desktopu Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), což znamená, že nejsou znovu šablonované a měly by se zobrazit ve výchozím vzhledu ovládacího prvku.

- **Dialogová okna standardní (nástroj):** ne motiv. Nevytvářejte znovu šablonu. Použijte výchozí hodnoty základního stylu ovládacího prvku.

- Okna **nástrojů, editory dokumentů, návrhové plochy a dialogy s motivy:** Použijte specializovaný vzhled motivu pomocí barevné služby.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Posuvníky
 Pokud nejsou rozšířené informace o obsahu, jako je například v editoru kódu, měly by se používat posuvníky [běžné způsoby interakce pro posuvníky Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) .

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Vstupní pole
 V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro textová pole](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

- Vstupní pole by se neměla stylovat v dialogových oknech nástrojů. Pro ovládací prvek použijte vnitřní základní styl.

- Vstupní pole motivu by se měla používat jenom v dialogových oknech a oknech motivů.

#### <a name="specialized-interactions"></a>Specializované interakce

- Pole jen pro čtení budou mít šedé (zakázané) pozadí, ale výchozí (aktivní) popředí.

- Požadovaná pole by měla být **\<Required>** v rámci těchto mezí. Barvy pozadí byste neměli měnit s výjimkou případů ve vzácných situacích.

- Ověření chyby: viz [oznámení a průběh pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Vstupní pole by měla být velikost, aby odpovídala obsahu, neodpovídají šířce okna, ve kterém jsou zobrazeny, ani libovolně odpovídat délce dlouhého pole, jako je například cesta. Délka může být náznakem uživatele s omezením, kolik znaků je v poli povoleno.

     ![Nesprávná šířka ovládacího prvku vstupní pole](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 – 01_IncorrectInputFieldControl") **Délka nesprávného vstupního pole: je pravděpodobné, že název bude dlouhý.**

     Správná délka vstupního pole ![šířky ovládacího prvku vstupního pole](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 – 02_CorrectInputFieldControl") **: vstupní pole je vhodnou šířkou pro očekávaný obsah.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Pole se seznamem a rozevírací seznamy
 V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro rozevírací seznamy a pole se seznamem](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neměňte šablonu ovládacího prvku znovu. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní motivů se pole se seznamem a rozevírací seznamy řídí standardními pro ovládací prvky.

#### <a name="layout"></a>Layout
 Pole se seznamem a rozevírací seznamy by měly být velikosti, aby odpovídaly šířce okna, ve kterém jsou zobrazeny, ani libovolně odpovídat délce dlouhého pole, jako je například cesta.

 ![Nesprávné rozložení odkládacího&#45;](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 – 03_IncorrectDropDownLayout")

 **Nesprávná délka pole pro ovládací prvek rozevíracího seznamu**

 ![Správné rozložení odkládacího&#45;](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 – 04_CorrectDropDownLayout")

 **Správná délka pole pro ovládací prvek rozevíracího seznamu**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Zaškrtávací políčka
 V případě typických chování interakce postupujte podle [pokynů pro plochu Windows pro instalaci zaškrtávacích políček](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl

- V dialogových oknech neměňte šablonu ovládacího prvku znovu. Pro ovládací prvek použijte vnitřní základní styl.

- V uživatelském rozhraní s motivem se zaškrtávací políčka dodržujte standardní pro ovládací prvky.

#### <a name="specialized-interactions"></a>Specializované interakce

- Interakce se zaškrtávacím políčkem nesmí nikdy odložit dialog ani přejít do jiné oblasti.

- Zaškrtávací políčka zarovnejte se směrným plánem prvního řádku textu.

     ![Nesprávné](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 – 05_IncorrectCheckBoxAlign") zarovnání zaškrtávacího políčka zarovnání **nesprávného zaškrtávacího políčka: zaškrtávací políčko se zacentruje na střed textu.**

     ![Správné](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 – 06_CorrectCheckBoxAlign") zarovnání zaškrtávacího políčka zarovnání zaškrtávacího políčka **: zaškrtávací políčko je zarovnáno se směrným plánem prvního řádku textu.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Přepínače
 V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro přepínače](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl
 V dialogových oknech nástrojů nepoužívejte přepínací tlačítka. Pro ovládací prvek použijte vnitřní základní styl.

#### <a name="specialized-interactions"></a>Specializované interakce
 K uzavření možností přepínače není nutné používat skupinový rámeček.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Skupinové rámečky
 V případě typických chování interakce postupujte podle [pokynů pro Windows Desktop pro skupiny](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Vizuální styl
 V dialogových oknech neměňte styl rámečky skupiny. Pro ovládací prvek použijte vnitřní základní styl.

#### <a name="layout"></a>Layout

- Není nutné používat skupinový rámeček k uzavření možností přepínačů, pokud nepotřebujete zachovat rozlišení skupiny v těsném rozložení.

- Nikdy nepoužívejte skupinový rámeček pro jeden ovládací prvek.

- Někdy je přijatelné použít místo kontejneru rámce skupiny horizontální pravidlo.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Textové ovládací prvky

### <a name="labels"></a>Štítky

#### <a name="active-label-state"></a>Stav aktivního popisku

##### <a name="utility-standard-dialogs"></a>Dialogová okna (standardní)

- Obecně postupujte podle pokynů pro stolní počítače Windows pro popisky ovládacích prvků.

- V dialogových oknech nástrojů by se popisky měly zobrazovat bez tučného písma ve standardním prostředí a v barvě textu. Podívejte [se na téma písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Tři tečky by měly vždy následovat za popisky.

##### <a name="signature-themed-dialogs"></a>Dialogová okna podpisu (motiv))
 Ovládací prvky Label můžou být tučné nebo světle šedé.

#### <a name="disabled-label-state"></a>Zakázaný stav popisku
 Popisky by měly odrážet vzhled ovládacího prvku, ke kterému jsou přidruženy. Například pokud je přidružený ovládací prvek zakázán, popisek by měl být zobrazen šedě a zakázán. To je obvykle zpracováváno operačním systémem a nevyžaduje žádné zvláštní zacházení.

#### <a name="dynamic-labels"></a>Dynamické popisky
 Dynamické popisky se mění v závislosti na aktuálním výběru. Kdykoli je to možné, použijte dynamické popisky v rozložení hlavních a podrobných informací, které uživatelům pomůžou pochopit, že zobrazené informace jsou relevantní pro konkrétní výběr a ne Obecné informace.

 ![Dynamický popisek použitý s dynamickým obsahem](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 – 01_DynamicLabel")

 **Příklad dynamického popisku používaného s dynamickým obsahem**

#### <a name="instructional-text"></a>Instruktážní text
 Některé prvky rozhraní využívají instruktážní text, které uživatelům pomůžou pochopit účel uživatelského rozhraní nebo určit, kterou akci chcete provést.

- Instruktážní text je nejčastěji v horní části dialogových oken, ale může se objevit v jiných oblastech, aby bylo možné předat pokyny komplexnímu seskupení ovládacích prvků.

- Instruktážní text není interaktivní, ale může obsahovat hypertextové odkazy na témata nápovědy.

- Používejte instruktážní text jenom v případě potřeby.

##### <a name="formatting"></a>Formátování
 Návodový text by měl být písmo prostředí, standardní (bez motivace) řídicí text. Podívejte [se na téma písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Podrobnosti o psaní návodového textu najdete v tématu [text uživatelského rozhraní a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Formátování popisného textu](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 – 02_InstructionalTextFormatting")

 **Instruktážní text v dialogovém okně Visual Studio**

#### <a name="informational-text"></a>Informační text
 Informační text je text, který uživateli poskytne další informace. Může být statický nebo dynamický nebo použitý jako oznámení. Je vždy jen pro čtení, ale pokud je užitečné, aby mohl uživatel mít možnost Kopírovat informace, dynamický text by měl být umístěn do kontejneru ovládacího prvku, jako je například textové pole jen pro čtení.

##### <a name="dynamic-context-specific-text"></a>Dynamický text (kontext specifický v kontextu)
 Dynamický informační text se změní v závislosti na kontextu, například když uživatel přepne fokus. Kromě toho se dynamický obsah často používá s dynamickým popiskem, ale ne vždy.

 ![Dynamický informační text](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 – 03_InformationalDynamicText")

 **Dynamický informativní text se změní v závislosti na kontextu.**

##### <a name="formatting"></a>Formátování
 Existují dva způsoby, jak zobrazit textová pole jen pro čtení: buď přímo na povrchu uživatelského rozhraní (viz výše), nebo obsažena v jiném ovládacím prvku, jako je například skupinový rámeček nebo textové pole. Buď je správný v závislosti na situaci. K určení toho, jak prezentovat informace jen pro čtení, je k dispozici Návrhář funkcí.

 Text může být uvnitř textového pole určeného jen pro čtení. To obecně znamená, že obsah může být vybrán a zkopírován, i když jej nelze upravovat.

 ![Formátování informativních textů pro čtení&#45;pouze polí](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 – 04_InformationalFormatting")

 **Formátování informativního textu pro pole jen pro čtení**

#### <a name="watermarks"></a>Vodoznaky
 I když se může jednat o stejný rozdíl mezi vodoznakem a textovým textem, jsou vodoznaky nahrazeny obsahem, když ovládací prvek nebo okno není prázdné a text pokynů zůstane stále viditelný.

 Meze by se měly použít, když je okno nebo ovládací prvek prázdné. Označují, co je potřeba udělat k naplnění oblasti, a může obsahovat odkazy na akce pro otevření relevantních oken, jako je například zdroj přetažení.

##### <a name="visual-style"></a>Vizuální styl

- Meze by se měly vycentrovat vodorovně v rámci okna.

- Meze by měly být zarovnané na střed, ne vlevo.

- Vodoznaky můžou být vertikálně zarovnané na střed nebo umístěné blízko horní části oblasti. Pokud se nachází v horní části oblasti, musí být dostatek místa, aby se vodoznak objevil.

- Použijte `Environment.GrayText` symbol barvy a písmo standardní prostředí. Hypertextové odkazy by měly používat sdílené tokeny standardní hypervazby: `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , a `Environment.PanelHyperlinkPressed` `Environment.PanelHyperlinkDisabled` .

- Meze nelze vybrat na pozadí.

- Pokud je to možné, zahrňte odkazy na meze, které uživateli pomůžou začít.

  ![Text vodoznaku v okně návrháře](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 – 05_Watermark1")

  ![Text vodoznaku v okně nástroje](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 – 06_Watermark2")

  **Příklady textu vodoznaku v aplikaci Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Tlačítka a hypertextové odkazy

### <a name="overview"></a>Přehled
 Tlačítka a ovládací prvky odkazů (hypertextové odkazy) by se měly řídit [základními pokyny pro stolní počítače s Windows na základě odkazů](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) na použití, určení velikosti a mezer.

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
 ![Odkazy příkazů na informačním panelu po stavové zprávě](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 – 01_CommandLinkInfobar")

 **Odkazy na příkazy použité na informačním panelu po stavové zprávě**

 ![Odkazy používané v překryvném okně CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 – 02_LinksInCodeLens")

 **Odkazy používané v překryvném okně CodeLens**

 ![Odkazy používané jako sekundární příkazy](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 – 03_LinksAsSecondaryCommands")

 **Odkazy používané pro sekundární příkazy, ve kterých by tlačítka mohla mít větší pozornost.**

### <a name="common-buttons"></a>Společná tlačítka

#### <a name="text"></a>Text
 Postupujte podle pokynů pro psaní v [textu uživatelského rozhraní a terminologii](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Vizuální styl

##### <a name="standard-dialogs"></a>Standardní dialogová okna
 Většina tlačítek v aplikaci Visual Studio se zobrazí ve standardních dialogových oknech a neměla by být ve stylu. Měly by odrážet standardní vzhled tlačítek podle operačního systému.

##### <a name="themed"></a>S motivem
 V některých případech mohou být tlačítka použita v uživatelském rozhraní se stylem a tato tlačítka musí být vhodně nastavena. Informace o ovládacích prvcích tematických prvků naleznete v [dialogových oknech](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Speciální tlačítka

#### <a name="browse-buttons"></a>Procházet... tlačítka
 **[Procházet...]** tlačítka se používají v Gridech, dialogových oknech a oknech nástrojů a jiných nemodálních prvcích uživatelského rozhraní. Zobrazují výběr, který pomáhá uživateli při naplňování hodnoty do ovládacího prvku. Toto tlačítko má dvě varianty, dlouhé a krátké.

 ![Dlouhé &#91;tlačítko Procházet... &#93;](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 – 04_BrowseLong")

 **Tlačítko dlouhého [Procházet...]**

 ![Krátké tři tečky&#45;pouze &#91;Procházet... &#93; tlačítko](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 – 05_BrowseShort")

 **Tlačítko krátkého znaku [...] jen pro tři tečky**

 Kdy použít krátké tlačítko se třemi tečkami:

- Je-li v dialogovém okně více než jedno dlouhé tlačítko **[Procházet...]** , například když je povoleno procházení několika polí. Použijte tlačítko short **[...]** pro každý, aby nedocházelo k odepření přístupových klíčů, které byly vytvořeny v této situaci (**&procházet** a **B&ocházet** ve stejném dialogovém okně).

- V těsném dialogovém okně nebo v případě, že není přijatelné místo pro vložení dlouhého tlačítka.

- Pokud se tlačítko zobrazí v ovládacím prvku mřížky.

  Pokyny pro použití tlačítka:

- Nepoužívejte přístupový klíč. Chcete-li k němu přistupovat pomocí klávesnice, musí uživatel z sousedícího ovládacího prvku kartu. Ujistěte se, že je pořadí karet tak, že jakékoli tlačítko pro procházení spadá hned za pole, které bude vyplňovat. Nikdy nepoužívejte podtržítko pod první tečkou.

- Nastavte vlastnost **název** rozhraní Microsoft Active ACCESSIBILITY (MSAA) na **Procházet...** (včetně tří teček), aby se čtenáři obrazovky načetly jako "Procházet", a ne "tečka-tečka-tečka" nebo "perioda-period-period". U spravovaných ovládacích prvků to znamená nastavení vlastnosti s **přístupným přístupem** .

- Nikdy nepoužívejte tlačítko se třemi tečkami **[...]** pro cokoli s výjimkou akce procházení. Například pokud potřebujete tlačítko **[New...]** , ale nemáte dostatek místa pro text, je nutné změnit návrh dialogu.

##### <a name="sizing-and-spacing"></a>Velikost a mezery
 ![Změna velikosti &#91;Procházet... &#93; tlačítka](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 – 06_BrowseSizing")

 **Změna velikosti tlačítek [Procházet...]**

 ![Mezery &#91;Procházet... &#93; tlačítka](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 – 07_BrowseSpacing")

 **Mezery [Procházet...] tlačítka**

#### <a name="graphical-buttons"></a>Grafická tlačítka
 Některá tlačítka by měla vždy používat grafický obraz a nikdy vkládat text do úspory místa a vyhnout se tak problémům s lokalizací. Tyto prvky se často používají v seznamech pro pole a v dalších seznamech s řazením.

> [!NOTE]
> Uživatelé musí mít k těmto tlačítkům kartu (nejsou k dispozici žádné přístupové klávesy), proto je umístěte do rozumné objednávky. Namapujte vlastnost Name tlačítka na akci, kterou provede, aby čtenáři obrazovky správně interpretoval akci tlačítka.

|Name|Image|
|-|-|
|Přidat|![Grafické tlačítko Přidat](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 – 08_ButtonAdd")|
|Odebrat|![Grafické tlačítko odebrat](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 – 09_ButtonRemove")|
|Přidat vše|![Grafické tlačítko Přidat vše](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 – 10_ButtonAddAll")|
|Odebrat vše|![Grafické tlačítko "Odebrat vše"](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 – 11_ButtonRemoveAll")|
|Přesunout nahoru|![Grafické tlačítko "přesunout nahoru"](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 – 12_ButtonMoveUp")|
|Přesunout dolů|![Grafické tlačítko "přesunout dolů"](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 – 13_ButtonMoveDown")|
|Odstranit|![Grafické tlačítko "odstranit"](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 – 14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Velikost a mezery
 Velikost grafických tlačítek je stejná jako u krátké verze tlačítka **[Procházet...]** (26x23 pixelů):

 ![Tlačítko s průhlednou barvou a bez ní](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 – 15_GraphicalButtonSpacing")

 **Vzhled tlačítka u grafického obrázku na tlačítku s a bez průhledné barvy**

### <a name="hyperlinks"></a>Hypertextové odkazy
 Hypertextové odkazy jsou vhodné pro navigační akce, jako je například otevření tématu nápovědy, modálního dialogového okna nebo průvodce. Je-li pro příkaz použit hypertextový odkaz, měl by vždy zobrazovat viditelné a znatelné změny uživatelského rozhraní. Obecně platí, že akce, které potvrzují akci (například uložit, zrušit a odstranit), jsou lépe sděleny pomocí tlačítka.

#### <a name="writing-style"></a>Styl psaní
 Postupujte podle [pokynů pro stolní počítače s Windows pro text uživatelského rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). Nepoužívejte "Další informace o", "Řekněte mi více o" nebo "získat pomoc s touto formulací". Místo toho odkazová Nápověda text odkazuje na primární otázku zodpovězenou obsahem Nápověda. Například "**návody přidat server do Průzkumník serveru?**"

#### <a name="visual-style"></a>Vizuální styl

- Hypertextové odkazy by měly vždy používat [službu VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Pokud hypertextový odkaz není správně ve stylu, při jeho zobrazení dojde k jeho červenému blikání nebo po navštívení jiné barvy.

- Nezahrnovat podtržení v ovládacím prvku, pokud se nejedná o fragment věty v celé větě, jako je například v horní části.

- Při najetí myší by se neměly zobrazovat podtržení. Místo toho je zpětná vazba pro uživatele, že je aktivní odkaz, mírně zvýrazněna barvou a odpovídajícím kurzorem odkazu.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Stromová zobrazení

### <a name="overview"></a>Přehled
 Stromová zobrazení slouží jako způsob uspořádání komplexních seznamů do skupin nadřazených a podřízených objektů. Uživatel může rozbalit nebo sbalit nadřazené skupiny a zobrazit nebo skrýt podkladové podřízené položky. Každou položku v rámci stromového zobrazení lze vybrat k zajištění dalších akcí.

 Toto téma se zabývá přijatelným používáním, řádným návrhem a funkcemi stromového zobrazení.

#### <a name="in-this-topic"></a>V tomto tématu

- [Vizuální styl](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interakce](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Vizuální styl

#### <a name="expanders"></a>Rozšíření
 Ovládací prvky stromového zobrazení by měly odpovídat návrhu rozšíření používanému v systémech Windows a Visual Studio. Každý uzel používá ovládací prvek rozšíření k zobrazení nebo skrytí podkladových položek. Použití ovládacího prvku rozšíření poskytuje konzistenci pro uživatele, kteří mohou narazit na různá stromová zobrazení v rámci systému Windows a sady Visual Studio.

 ![Správný ovládací prvek stromového zobrazení](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 – 1_TreeViewCorrect")

 **Oprava: správný styl uzlu stromového zobrazení pomocí ovládacího prvku rozšíření**

 ![Nesprávný uzel zobrazení stromu](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 – 2_TreeViewIncorrect1")

 **Nesprávné: nesprávný styl uzlu stromového zobrazení**

#### <a name="selection"></a>Výběr
 Když je vybrán uzel ve stromovém zobrazení, zvýraznění by se mělo rozšířit na celou šířku ovládacího prvku stromového zobrazení. To pomáhá uživatelům jasně určit, která položka byla vybrána. Barvy výběru by měly odrážet aktuální motiv sady Visual Studio.

 ![Správný ovládací prvek stromového zobrazení](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 – 1_TreeViewCorrect")

 **Správné: zvýraznění vybraného uzlu odpovídá celé šířce ovládacího prvku stromového zobrazení.**

 ![Nesprávné zvýrazňování zobrazení stromu](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 – 3_TreeViewIncorrect2")

 **Nesprávné: zvýraznění vybraného uzlu se nevejde na celou šířku ovládacího prvku stromového zobrazení.**

#### <a name="icons"></a>Ikony
 Ikony by měly být použity pouze v ovládacích prvcích stromového zobrazení, pokud je pomáhají vizuálně identifikovat rozdíly mezi položkami. Obecně by měly být ikony použity pouze v heterogenních seznamech, ve kterých ikony přenášejí informace pro odlišení typů prvků. V homogenním seznamu pomocí ikon se často považují za šum a je třeba se jim vyhnout. V takovém případě může ikona skupiny (nadřazená položka) vyjádřit typ položek v rámci tohoto případu. Výjimkou z tohoto pravidla by byla, pokud je ikona dynamická a používá se k označení stavu.

#### <a name="scroll-bars"></a>Posuvníky
 Pokud se obsah vejde do ovládacího prvku stromového zobrazení, měly by být vždy skryté posuvníky. Je přijatelné, aby byly posuvníky skryty nebo částečně transparentní v rolovacím okně a zobrazily se v případě, že okno obsahující stromové zobrazení má fokus, nebo když najedete myší na samotný stromové zobrazení.

 ![Stromové zobrazení s posuvníky](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 – 4_Scrollbars")

 **Zobrazí se svislé i vodorovné posuvníky, protože obsah překročil limity ovládacího prvku stromového zobrazení.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interakce

#### <a name="context-menus"></a>Místní nabídky
 Uzel zobrazení stromu může zobrazit možnosti podnabídky v místní nabídce. K tomu obvykle dochází, když uživatel klikne pravým tlačítkem myši na položku nebo stisknete klávesu nabídky na klávesnici Windows s vybranou položkou. Je důležité, aby uzel získal fokus a byl vybrán. To pomáhá uživateli zjistit, do které položky Tato nabídka patří.

 ![Vybraný uzel stromu a kontextová nabídka](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 – 5_ContextMenu")

 **Položka, která má vytvořit kontextovou nabídku, získá fokus a upozorní uživatele, která položka byla vybrána.**

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

  ![Ovládací prvek trid v aplikaci Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 – 6_Trid")

  **Ovládací prvek trid v aplikaci Visual Studio**
