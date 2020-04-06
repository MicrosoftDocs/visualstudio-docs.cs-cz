---
title: Základní informace o uživatelském zařízení pro visual studio | Dokumenty společnosti Microsoft
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698334"
---
# <a name="ux-essentials-for-visual-studio"></a>Základy uživatelského prostředí pro Visual Studio

## <a name="best-practices"></a>Osvědčené postupy

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Buďte konzistentní v prostředí sady Visual Studio.

- Sledujte existující [vzory interakcí](interaction-patterns-for-visual-studio.md) v prostředí.

- Konstrukční prvky jsou v souladu s vizuálním jazykem a požadavky na [řemeslné zpracování](evaluation-tools-for-visual-studio.md).

- Sdílené příkazy a ovládací prvky používejte v případě, že existují.

- Seznamte se s hierarchií sady Visual Studio a s tím, jak vytváří kontext a řídí ui.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Použijte službu prostředí pro písma a barvy.

- Uživatelské rozhraní by mělo respektovat aktuální nastavení [písma prostředí,](fonts-and-formatting-for-visual-studio.md) pokud není vystaveno pro vlastní nastavení na stránce Písma a barvy v dialogovém okně Možnosti.

- Prvky uživatelského rozhraní musí používat [službu VSColor Service](colors-and-styling-for-visual-studio.md), pomocí tokenů sdíleného prostředí nebo tokenů specifických pro funkce.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Proveďte všechny snímky v souladu s novým stylem VS.

- Postupujte podle principů návrhu sady Visual Studio pro ikony, glyfy a další grafiky.

- Neumisťovat text do grafických prvků.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Design z pohledu zaměřeného na uživatele.

- Vytvořte tok úkolů před jednotlivými prvky v něm.

- Seznamte se se svými uživateli a aby tyto znalosti explicitní ve vašem spec.

- Při kontrole uživatelského prostředí vyhodnoťte kompletní prostředí a podrobnosti.

- Navrhněte své uzlové prostředí tak, aby zůstalo funkční a atraktivní bez ohledu na národní prostředí nebo jazyk.

## <a name="screen-resolution"></a>Rozlišení obrazovky

### <a name="minimum-resolution"></a>Minimální rozlišení

- Minimální rozlišení pro Visual Studio 2015 je **1280x720**. To znamená, že je *možné* použít visual studio v tomto rozlišení, i když nemusí být optimální uživatelské prostředí. Neexistuje žádná záruka, že všechny aspekty budou použitelné v rozlišení nižší než 1280x720.

- Cílové rozlišení pro Visual Studio je **1366x768**. Toto je nejnižší rozlišení, při kterém slibujeme *dobrou* uživatelskou zkušenost.

- Počáteční výška dialogu by měla být **menší než 700 pixelů**, takže se vejde do minimálního rozlišení rámce IDE při 96 dpi.

### <a name="high-density-displays"></a>Displeje s vysokou hustotou
 UI v sadě Visual Studio musí dobře fungovat ve všech faktorech škálování DPI, které systém Windows podporuje po vybalení: 150 %, 200 % a 250 %.

## <a name="anti-patterns"></a>Anti-vzory
 Visual Studio obsahuje mnoho příkladů ui, které se řídí našimi pokyny a osvědčenými postupy. Ve snaze být konzistentní, vývojáři často půjčit z produktu ui návrhové vzory podobné tomu, co jsou stavební. I když je to dobrý přístup, který nám pomáhá řídit konzistenci v interakci s uživatelem a vizuální design, děláme příležitostně loď funkce s několika detaily, které nesplňují naše pokyny z důvodu omezení plánu nebo defektu priority. V těchto případech nechceme, aby týmy kopírovat jeden z těchto "anti-patterns", protože se množí špatné nebo nekonzistentní ui v prostředí sady Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Požadovaná pole/nastavení zobrazená ve výchozím nastavení v chybovém stavu

#### <a name="feature-team-goals"></a>Cíle týmu

- Upozorněte uživatele, že přidali prvek, který musí být nakonfigurován.

- Upozorněte uživatele na oblasti, které potřebují vstup.

#### <a name="anti-pattern-solution"></a>Anti-vzor řešení
 Jakmile uživatel iniciuje akci a před dokončením úkolu, okamžitě umístěte ikony kritického zastavení vedle oblastí, které potřebují konfiguraci.

#### <a name="example-manifest-designer-declarations"></a>Příklad: Deklarace návrháře manifestu
 Přidání deklarace do seznamu okamžitě umístí do chybového stavu, který přetrvává, dokud uživatel nastaví požadované vlastnosti.

 V tomto případě existuje další problém, protože ikona použitá&times;pro výstrahu obsahuje ikonu " ", takže vedle ní nelze použít společnou ikonu odebrání. V důsledku toho ui používá tlačítko Remove, více neohrabaný ovládací prvek.

 ![Umístění uI v chybovém stavu ve výchozím nastavení je Anti-Pattern sady Visual Studio.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-pattern ManifestDesignererrordeclarationsanti-pattern ManifestDesignererrordeclarationsanti-pattern ManifestDesigner")<br />Umístění uI v chybovém stavu ve výchozím nastavení je Anti-Pattern sady Visual Studio.

#### <a name="alternatives"></a>Alternativy

Lepším řešením tohoto problému je:

- Umožněte uživateli přidat deklaraci bez upozornění a potom okamžitě přesunout nastavení vlastností položky.

- Přidejte ikonu upozornění (zlatý trojúhelník) při přesunu fokusu z položky, například přidání další deklarace do seznamu nebo pokus o změnu karet v návrháři.

- Pokud se uživatel pokusí změnit karty před nastavením vlastností na všechny deklarace, pop dialogové okno s vysvětlením, že aplikace nebude stavět (nebo bez ohledu na důsledky), dokud upozornění jsou vyřešeny. Pokud uživatel zavře dialogové okno a změní karty tak jako tak pak ikona (kritické nebo upozornění, podle potřeby) je přidán a prohlášení kartu.

### <a name="multiple-clicks-to-dismiss-ui"></a>Více kliknutí pro zavření ui

#### <a name="feature-team-goals"></a>Cíle týmu
 Nepovolte uživateli zavřít uživatelské rozhraní bez předchozího zobrazení textu vysvětlení.

#### <a name="anti-pattern"></a>Proti vzoru
 Tým, který vložil odkazy na video na různá místa v uživatelském&times;okně VS, se rozhodl proti společnému vzoru " " vysvětlení zavření a popisku, jak je specifikováno uX, a místo toho implementoval rozevírací a znovu zobrazit odkaz "Nezobrazovat znovu".

#### <a name="example-video-links-in-team-explorer"></a>Příklad: Odkazy na videa v Průzkumníkovi týmu
Vynucení uživatele číst vysvětlující text před zavřením uživatelského rozhraní je anti-pattern v rámci sady Visual Studio. Správně navržené odkazy na videa by měly zobrazovat popisek&times;s dalšími informacemi o ukazateli myši a kliknutím na tlačítko " " by měla být zpráva odmítnuta bez nutnosti další interakce.

 ![Vysvětlující text proti&#45;vzor &#45; nesprávný](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Nesprávné použitívíce kliknutí")<br />Nesprávný vzor odkazu na video

Namísto jednoduchého tlačítka pro zavření (jedno kliknutí) je uživatel nucen použít dvě kliknutí, aby jednoduše zavřel uživatelské rozhraní na každém místě, kde se zobrazí odkazy na video.

Správný návrh pro tuto situaci je postupujte podle vzoru společné ho Aplikace Internet Explorer, Office a Visual Studio: při najetí přes, uživatel může vidět popis popisu a jedním kliknutím skryje uživatelské rozhraní.

 ![Vysvětlující text proti&#45;vzor &#45; správný](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Vysvětlující textanti-vzor-správné")<br />Opravit vzor propojení videa

### <a name="using-command-bars-for-settings"></a>Použití panelů příkazů pro nastavení

**Obrázek A** představuje tento anti-pattern: uvedení nastavení pod příkazové tlačítko, které se vztahuje na více než jen příkaz. V této skice jsou kromě počátečního ladění příkazy , které budou respektovat vybrané nastavení.

![Obrázek A: Protivzorek panelu příkazů](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-vzor-FigureA")<br />Obrázek A: Protivzorek panelu příkazů

O něco lepší, ale stále nežádoucí, je uvedení nastavení tohoto typu v panelech nástrojů, jak je znázorněno na **obrázku B**. Zatímco rozdělená tlačítka zabírají méně místa, a proto jsou zlepšení oproti rozevíracím nabídkám, oba návrhy stále používají panel nástrojů k propagaci něčeho, co ve skutečnosti není příkazem.

![Obrázek B: Lepší, ale stále panel příkazů proti vzoru](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-vzor-ObrázekB")<br />Obrázek B: Lepší, ale stále panel příkazů proti vzoru

Při správném přiblížení znázorněném **na obrázku C**je nastavení vázáno na řadu příkazů. Neexistuje žádné globální nastavení a my jsme jen přepínání mezi čtyřmi příkazy. Toto je jediná situace, ve které jsou přijatelné příkazy v panelu nástrojů.

![Obrázek C: Správné použití vzoru panelu příkazů sady Visual Studio](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-vzor-ObrázekC")<br />Obrázek C: Správné použití vzoru panelu příkazů sady Visual Studio

### <a name="control-anti-patterns"></a>Kontrola anti-patterns
 Některé anti-patterns jsou jednoduše nesprávné použití nebo prezentace ovládacího prvku nebo skupiny ovládacích prvků.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podtržení používané jako popisek skupiny, nikoli jako hypertextový odkaz
 Podtržení textu by mělo být použito pouze pro hypertextové odkazy.

 **Špatné:**\
 ![Podtržený text, který není hypertextovým odkazem, je anti-pattern sady Visual Studio.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Podtržený text, který není hypertextovým odkazem, je anti-pattern sady Visual Studio.

 **Dobré:**\
 ![Stylizovaný správně, text bez hypertextového odkazu se v písmu prostředí zobrazí bez ozdob.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Stylizovaný správně, text bez hypertextového odkazu se v písmu prostředí zobrazí bez ozdob.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknutím na zaškrtávací políčko se vyskakovacím dialogu zobrazí vyskakovací dialog.
 Kliknutím na zaškrtávací políčko Povolit vzdálenou plochu pro všechny role v průvodci Publikováním aplikace Windows Azure okamžitě zobrazíte vyskakovací dialog Visual Studio anti-pattern. Zaškrtávací políčko navíc nevyplňuje zaškrtávací políčko po zaškrtnutí jiného anti-patternu interakce.

 ![Po klepnutí na zaškrtávací políčko je antipattern sady Visual Studio.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Po klepnutí na zaškrtávací políčko je antipattern sady Visual Studio.

### <a name="hyperlink-anti-patterns"></a>Anti-patterny hypertextového odkazu
 Následující příklad obsahuje dva anti-patterns:

1. V popředí, které při najetí na ně zčervená, znamená, že se nepoužívá správná sdílená barva ze služby písem.

2. "Další informace" není vhodný text pro odkaz na koncepční téma. Cílem uživatele není dozvědět se více, je pochopit důsledky jejich výběru.

   ![Ignorování služby barev a použití "Další informace" pro hypertextové odkazy jsou anti-patterns sady Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Ignorování služby barev a použití "Další informace" pro hypertextové odkazy jsou anti-patterns sady Visual Studio.

**Lepší řešení:** Podejte otázku, kterou by uživatel položil kliknutím na odkaz. Například:

- Jak fungují služby Windows Azure?

- Kdy potřebuji projekt mobilních služeb Windows Azure?

#### <a name="using-click-here-for-links"></a>Použití "Klikněte zde" pro odkazy
 Hypertextové odkazy by měly být popisné. Je to anti-vzor použít "Klikněte zde" nebo podobné variace.

 **Špatné:** "Klikněte zde pro pokyny, jak vytvořit nový projekt."

 **Dobrý:** "Jak vytvořím nový projekt?"
