---
title: Základy uživatelského Visual Studio | Microsoft Docs
description: V těchto osvědčených postupech pro uživatelské prostředí najdete nové funkce, které vyvíjíte pro Visual Studio, včetně znalosti rozlišení obrazovky.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 74b27e87e6f16130573ef6671286501f77e44352
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899417"
---
# <a name="ux-essentials-for-visual-studio"></a>Základy uživatelského prostředí pro Visual Studio

## <a name="best-practices"></a>Osvědčené postupy

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Být konzistentní v rámci Visual Studio prostředí.

- Postupujte podle [existujících vzorů interakce](interaction-patterns-for-visual-studio.md) v prostředí.

- Navrhujte funkce tak, aby byly konzistentní s vizuálním jazykem a požadavky prostředí [na mluvenou řeč.](evaluation-tools-for-visual-studio.md)

- Pokud existují sdílené příkazy a ovládací prvky, použijte je.

- Seznamte se Visual Studio a zjistíte, jak vytváří kontext a řídí uživatelské rozhraní.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Pro písma a barvy použijte službu prostředí.

- Uživatelské rozhraní by mělo respektovat aktuální [nastavení písma prostředí,](fonts-and-formatting-for-visual-studio.md) pokud není zveřejněné pro přizpůsobení na stránce Písma a barvy v dialogovém okně Možnosti.

- Prvky uživatelského rozhraní musí používat [službu VSColor](colors-and-styling-for-visual-studio.md)pomocí tokenů sdíleného prostředí nebo tokenů specifických pro funkci.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Zajistěte, aby všechny snímky byly konzistentní s novým stylem VS.

- Dodržujte Visual Studio pro ikony, piktogramy a další grafiku.

- Neumis ovat text do grafických prvků.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Návrh z pohledu uživatele

- Vytvořte tok úlohy před jednotlivými funkcemi v rámci tohoto toku.

- Seznamte se s uživateli a ujistěte se, že je ve své specifikacích explicitně znáte.

- Při prohlédněte si uživatelské rozhraní a vyhodnoťte kompletní prostředí i podrobnosti.

- Navrhovat uživatelské rozhraní tak, aby zůstalo funkční a atraktivní bez ohledu na národní prostředí nebo jazyk.

## <a name="screen-resolution"></a>Rozlišení obrazovky

### <a name="minimum-resolution"></a>Minimální rozlišení

- Minimální rozlišení pro Visual Studio 2015 je **1280 × 720.** To znamená, že *je možné* použít Visual Studio řešení, i když to nemusí být optimální uživatelské prostředí. Neexistuje žádná záruka, že všechny aspekty budou použitelné při řešeních nižších než 1280 × 720.

- Cílové rozlišení pro Visual Studio **je 1366 × 768.** Jedná se o nejnižší řešení, při kterém slibujeme *dobré uživatelské* prostředí.

- Počáteční výška dialogového okna by **měla být menší než 700** pixelů, takže se vejde do minimálního rozlišení rámce IDE při 96 dpi.

### <a name="high-density-displays"></a>Zobrazení s vysokou hustotou
 Uživatelské rozhraní Visual Studio musí dobře fungovat ve všech faktorech škálování DPI, které Systém Windows podporuje beze změny: 150 %, 200 % a 250 %.

## <a name="anti-patterns"></a>Antivzory
 Visual Studio obsahuje mnoho příkladů uživatelského rozhraní, které dodržuje naše pokyny a osvědčené postupy. Ve snaze být konzistentní si vývojáři často vypůjčují ze vzorů návrhu uživatelského rozhraní produktů podobných těm, které budujou. I když se jedná o dobrý přístup, který nám pomáhá zajistit konzistenci v interakci uživatelů a vizuálním návrhu, v některých případech dodáme funkce s několika podrobnostmi, které z důvodu plánových omezení nebo stanovení priorit vad nesplňuje naše pokyny. V těchto případech nechcete, aby týmy kopírovat jeden z těchto "antivzory", protože v rámci tohoto prostředí prosažují špatné nebo nekonzistentní uživatelské Visual Studio prostředí.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Požadovaná pole/nastavení zobrazená ve výchozím chybovém stavu

#### <a name="feature-team-goals"></a>Cíle týmu funkcí

- Upozornit uživatele, že přidali element, který musí být nakonfigurován.

- Přitápejte pozornost uživatele k oblastem, které potřebují vstup.

#### <a name="anti-pattern-solution"></a>Anti-pattern solution
 Jakmile uživatel zahájí akci a před dokončením úlohy, ihned umístěte ikony kritického zastavení vedle oblastí, které potřebují konfiguraci.

#### <a name="example-manifest-designer-declarations"></a>Příklad: Deklarace návrháře manifestu
 Když přidáte deklaraci do seznamu, okamžitě ji umístíte do chybového stavu, který se zachová, dokud uživatel nenastavuje požadované vlastnosti.

 V tomto případě existuje další problém, protože ikona použitá pro výstrahu obsahuje ikonu " ", takže vedle ní nelze použít běžnou ikonu &times; odebrání. V důsledku toho uživatelské rozhraní používá tlačítko Odebrat, ovládací prvek s více prvky.

 ![Umístění uživatelského rozhraní do chybového stavu je Visual Studio anti-vzor.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti – vzor")<br />Umístění uživatelského rozhraní do chybového stavu je Visual Studio anti-vzor.

#### <a name="alternatives"></a>Alternativy

Lepším řešením tohoto problému je:

- Umožní uživateli přidat deklaraci bez upozornění a potom ji okamžitě přesunout, aby nastavil vlastnosti položky.

- Přidejte ikonu upozornění (zlatý trojúhelník), když se fokus přesune z položky, například přidání další deklarace do seznamu nebo pokus o změnu karet v návrháři.

- Pokud se uživatel pokusí změnit karty před nastavením vlastností u deklarací, vysunout dialogové okno s vysvětlením, že aplikace se nevystaví (nebo bez ohledu na to, jaké to bude mít důsledky), dokud se upozornění nevyřeší. Pokud uživatel dialogové okno zavře a karty přesto změní, přidá se na kartu Deklarace ikona (kritické nebo upozornění podle potřeby).

### <a name="multiple-clicks-to-dismiss-ui"></a>Zavření uživatelského rozhraní několika kliknutími

#### <a name="feature-team-goals"></a>Cíle týmu funkcí
 Neumožňují uživateli zavřít uživatelské rozhraní, aniž by nejprve viděli text vysvětlení.

#### <a name="anti-pattern"></a>Anti-pattern
 Tým, který vkládá odkazy na video na různá místa v uživatelském rozhraní sady VS, rozhodl se proti běžnému vzoru tlačítka zavřít a popisu tlačítka, jak je určeno uživatelským rozhraním, a místo toho implementoval rozevírací seznam a odkaz "Znovu nez &times; zobrazení".

#### <a name="example-video-links-in-team-explorer"></a>Příklad: Odkazy na video v Team Explorer
Vynucení, aby si uživatel před zavřením uživatelského rozhraní přečetl vysvětlující text, je v rámci Visual Studio. Správně navržené odkazy na videa by měly zobrazit popisek s dalšími informacemi o najetí myší a kliknutím na " by se zpráva měla zavřít bez &times; nutnosti další interakce.

 ![Nesprávný vzor vysvětlujícího&#45;proti &#45; textu](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Nesprávný vzor odkazu na video

Místo jednoduchého tlačítka zavřít (jedním kliknutím) musí uživatel jednoduše zavřít uživatelské rozhraní na každém místě, kde se zobrazí odkazy na video.

Správným návrhem pro tuto situaci je postupovat podle vzoru společného pro Internet Explorer, Office a Visual Studio: při najetí myší se uživateli zobrazí popis popisu a jedno kliknutí skryje uživatelské rozhraní.

 ![Správný vzor vysvětlujícího&#45;proti &#45; textu](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-vzor – správné")<br />Oprava vzoru odkazu na video

### <a name="using-command-bars-for-settings"></a>Použití panelu příkazů pro nastavení

**Obrázek A** představuje tento anti-vzor: umístění nastavení pod příkazové tlačítko, které platí pro více než jen příkaz. V tomto náčrtu jsou kromě možnosti Spustit ladění k dispozici příkazy, jako je například Zobrazení v prohlížeči, Spustit bez ladění a Krokovat s krokem do, které respektují vybrané nastavení.

![Obrázek A: Anti pattern panelu příkazů](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-vzor-obrázek")<br />Obrázek A: Anti pattern panelu příkazů

O něco lepší, ale stále nežádoucí je umístění nastavení tohoto typu na panely nástrojů, jak je znázorněno na **obrázku B.** I když tlačítka rozdělení zaují méně místa, a proto se vylepšují oproti rozevíracím nabídkám, oba návrhy pořád používají panel nástrojů k propagaci něčeho, co ve skutečnosti není příkaz.

![Obrázek B: Lepší, ale stále anti-vzor panelu příkazů](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Pattern-FigureB")<br />Obrázek B: Lepší, ale stále anti-vzor panelu příkazů

Ve správném přístupu, který je znázorněn **na obrázku C,** je nastavení vázané na řadu příkazů. Není nastaveno žádné globální nastavení a pouze přepínáme mezi čtyřmi příkazy. Toto je jediná situace, kdy jsou příkazy na panelu nástrojů přijatelné.

![Obrázek C: Správné použití Visual Studio panelu příkazů](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Pattern-FigureC")<br />Obrázek C: Správné použití Visual Studio panelu příkazů

### <a name="control-anti-patterns"></a>Řízení antivzory
 Některé antivzory jsou jednoduše nesprávné použití nebo prezentace ovládacího prvku nebo skupiny ovládacích prvků.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podtržení se používá jako popisek skupiny, nikoli hypertextový odkaz.
 Podtržení textu by se mělo používat jenom pro hypertextové odkazy.

 **Špatné:**\
 ![Podtržený text, který není hypertextovým odkazem, Visual Studio proti vzoru.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 – g_GroupLabelIncorrect")<br />Podtržený text, který není hypertextovým odkazem, Visual Studio proti vzoru.

 **Dobré:**\
 ![Text bez hypertextového odkazu má správný styl a v písmu prostředí se zobrazuje bez jeho návěsí.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 – h_GroupLabelCorrect")<br />Text bez hypertextového odkazu má správný styl a v písmu prostředí se zobrazuje bez jeho návěsí.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Po kliknutí na zaškrtávací políčko se zobrazí automaticky otevírané dialogové okno.
 Po kliknutí na zaškrtávací políčko Povolit vzdálenou plochu pro všechny role v průvodci publikováním aplikace Windows Azure se okamžitě zobrazí automaticky otevírané dialogové okno, Visual Studio je anti-vzoru. Kromě toho se zaškrtávací políčko po výběru nevyplní zaškrtávacím políkem, další anti-vzor interakce.

 ![Zobrazení dialogového okna po kliknutí na zaškrtávací políčko je Visual Studio anti-vzor.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 – i_CheckboxPopup")<br />Zobrazení dialogového okna po kliknutí na zaškrtávací políčko je Visual Studio anti-vzor.

### <a name="hyperlink-anti-patterns"></a>Antivzory hypertextových odkazů
 Následující příklad obsahuje dva antivzory:

1. Zapnutí červeného popředí při najetí myší znamená, že se ze služby písem nebude používat správná sdílená barva.

2. "Další informace" není vhodný text pro odkaz na koncepční téma. Cílem uživatele není dozvědět se více, je pochopit důsledky jeho volby.

   ![Ignorování barevné služby a použití možnosti "Další informace" pro hypertextové odkazy jsou anti-patterny sady Visual Studio.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 – j_HyperlinkIncorrect")<br />Ignorování barevné služby a použití možnosti "Další informace" pro hypertextové odkazy jsou anti-patterny sady Visual Studio.

**Lepší řešení:** Vyžádejte si otázku, na kterou se uživatel bude dotazovat kliknutím na odkaz. Příklad:

- Jak fungují služby Windows Azure?

- Kdy potřebuji projekt Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Použití "kliknutí sem" pro odkazy
 Hypertextové odkazy by měly být samoně popisné. Je to anti-vzor pro použití "kliknutí sem" nebo jakékoli podobné variace.

 **Chybné:** Kliknutím sem zobrazíte pokyny k vytvoření nového projektu. "

 **Dobrá akce:** "Návody vytvořit nový projekt?"
