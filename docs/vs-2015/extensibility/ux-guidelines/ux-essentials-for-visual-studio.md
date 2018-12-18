---
title: Základy uživatelského prostředí
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8984b0b7854457fcfa8f2b48e82fa8d12f8e539d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060466"
---
# <a name="ux-essentials-for-visual-studio"></a>Základy uživatelského prostředí pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Osvědčené postupy

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Být konzistentní prostředí sady Visual Studio.

-   Použijte existující vzory interakcí v rámci prostředí.

-   Návrh funkcí, které bylo v souladu s požadavky visual jazyka a řemeslné ruční práce k prostředí.

-   Používat sdílený příkazy a ovládací prvky, pokud existují.

-   Zjistěte, hierarchie sady Visual Studio a jak vytváří kontextu a řídí uživatelské rozhraní.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Pomocí služby prostředí písem a barev.

-   Uživatelské rozhraní by měly dodržovat aktuální nastavení písma prostředí, pokud je přístupný pro vlastní nastavení na stránce písma a barev v dialogovém okně Možnosti.

-   Prvky uživatelského rozhraní musí používat službu VSColor pomocí tokenů sdílená prostředí nebo konkrétních funkcí tokeny.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Ujistěte se, všechna trénováním konzistentní s nový styl VS.

-   Pomocí sady Visual Studio Principy návrhu pro ikon, glyfy a jiných grafických.

-   Neumísťujte text v grafické prvky.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Návrh z pohledu zaměřenou na uživatele.

-   Vytvořte tok úkolů před jednotlivých funkcí v něm.

-   Se seznámit s vašimi uživateli a proveďte explicitní v vaše specifikace dané znalosti.

-   Při kontrole uživatelského rozhraní, vyhodnoťte plně funkční, jakož i podrobnosti.

-   Návrh uživatelského rozhraní tak, aby zůstane funkční a atraktivní bez ohledu na to, národní prostředí nebo jazyk.

## <a name="screen-resolution"></a>Rozlišení obrazovky

### <a name="minimum-resolution"></a>Minimální rozlišení
 Minimální rozlišení pro Visual Studio Dev14 se 1280 × 1024. To znamená, že je *možné* pro používání sady Visual Studio toto rozlišení, ale nemusí být optimální uživatelské prostředí. Není zaručeno, že všechny aspekty bude možné použít při rozlišení nižší než 1280 × 1024.

 Počáteční dialogové okno by neměl být delší než 1000 pixelů na výšku tak, aby se vešel do rámečku integrovaného vývojového prostředí v rámci této minimální rozlišení při 96 dpi.

### <a name="high-density-displays"></a>Zobrazí s vysokou hustotou
 Uživatelské rozhraní v sadě Visual Studio musí fungovat dobře ve všech DPI škálování faktory, které podporuje Windows úprav: 150 %, 200 % a 250 %.

## <a name="anti-patterns"></a>Antimodely
 Visual Studio obsahuje mnoho příkladů uživatelského rozhraní, které následují Naše pokyny a osvědčené postupy. Ve snaze být konzistentní vzhledem k aplikacím vývojáři často si půjčte z podobný co při sestavování vzorů návrhu uživatelského rozhraní produktu. I když je to dobrý nápad, pomůže nám jednotka konzistence v interakci s uživatelem a vizuální návrh, v některých případech dodáváme funkce s několik podrobností, které splňují Naše pokyny z důvodu omezení plánu nebo defect stanovení priorit. V těchto případech doporučujeme nechcete, aby týmy zkopírovat jeden z těchto "antimodely" vzhledem k tomu, že udrželi chybná nebo nekonzistentní uživatelské rozhraní v rámci prostředí sady Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Požadované pole a nastavení výchozí zobrazené v chybovém stavu

#### <a name="feature-team-goals"></a>Funkce cílů týmu

-   Upozornit uživatele, aby vložili element, který musí být nakonfigurované.

-   Upozornit uživatele na oblasti, které vyžadují vstup.

#### <a name="anti-pattern-solution"></a>Řešení ochrany proti vzor
 Poté, co uživatel inicioval akci a předtím, než nebude dokončena úloha okamžitě umístíte kritické zastavení ikony vedle oblastí, které vyžadují konfiguraci.

#### <a name="example-manifest-designer-declarations"></a>Příklad: Manifest Designer deklarace
 Přidáte deklaraci do seznamu bezprostředně umístí v chybovém stavu, která zůstává v platnosti do uživatel nastaví požadované vlastnosti.

 V takovém případě je další žádný problém vzhledem k tomu, že ikona použitá pro upozornění obsahuje znak "x", proto odebrat společné nelze použít ikonu vedle něj. V důsledku toho rozhraní používá tlačítko odebrat, více clunky ovládacího prvku.

 ![Manifest Designer chyba deklarace spojení anti&#45;vzor](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti – vzor")

 **Umístění uživatelského rozhraní v chybovém stavu, ve výchozím nastavení je vzor proti sady Visual Studio.**

#### <a name="alternatives"></a>Alternativy
 Mnohem lepší řešení tohoto problému může být:

-   Umožní uživateli přidat deklarace bez upozornění a poté přesuňte okamžitě můžete nastavit vlastnosti v položce.

-   Přidat ikonu upozornění (gold trojúhelník) když fokus přesunete z položky, například přidat další deklarace do seznamu nebo pokusí změnit karet v návrháři.

-   Pokud uživatel se pokusí změnit karty před nastavením vlastností pro všechny deklarace, vyvolat přes pop dialogové okno s vysvětlením, že nebude možné sestavit aplikaci (nebo libovolné důsledky) až do vyřešení upozornění. Pokud uživatel zavře dialogové okno a změní karty přesto pak ikonu (kritický nebo varování, podle potřeby) se přidá na kartu deklarace.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Vynucení uživateli číst text před zavření uživatelského rozhraní

#### <a name="feature-team-goals"></a>Funkce cílů týmu
 Nepovolit uživatelům zavřít uživatelského rozhraní, aniž byste museli zobrazovat první text vysvětlení.

#### <a name="anti-pattern"></a>Ochrana proti vzor
 Vložení videa odkazů na různých místech v Uživatelském rozhraní VS proti běžný vzor X tým zavřete tlačítko a popisek vysvětlení podle uživatelského prostředí a místo toho implementovat rozevírací seznam a odkaz "Již příště nezobrazovat".

 ![Vysvětlující text spojení anti&#45;vzor &#45; nesprávné](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Nesprávný: vynucení uživateli číst vysvětlující text před zavření uživatelského rozhraní je odolné proti vzoru v rámci sady Visual Studio.**

#### <a name="result"></a>Výsledek
 Místo jednoduchého tlačítko pro uzavření (jedním kliknutím) uživatel bude muset používat dvě kliknutí se jednoduše zavřít uživatelského rozhraní všude, kde je video odkazy jsou zobrazeny.

#### <a name="alternatives"></a>Alternativy
 Správný návrh v této situaci může být podle tohoto vzoru vytvořené common Internet Explorer, Office a sady Visual Studio: při najetí myší, uživatel uvidí popisek a jedním kliknutím skryje uživatelské rozhraní.

 ![Vysvětlující text spojení anti&#45;vzor &#45; správné](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "opravte vzor Explanatorytextanti")

 **Správné: tak, jak navrženo, odkazy na video má zobrazit popisek společně s dalšími informacemi při najetí myší, a kliknutím na "X" by měla Zavřít zprávu bez nutnosti další interakce.**

### <a name="using-command-bars-for-settings"></a>Použití panely příkazů pro nastavení
 ![Panel příkazů proti&#45;vzor &#45; obrázek A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti. vzor FigureA")

 **Obrázek A: příkazového řádku proti vzor**

 **Obrázek A** představuje tento model proti: uvedení nastavení pod příkazového tlačítka, která se vztahuje k více než jen příkaz. V tomto nákresu jsou příkazy kromě spustit ladění – jako zobrazit v prohlížeči spustit bez ladění a Krokovat s vnořením –, který bude respektovat nastavení vybrané.

 ![Panel příkazů proti&#45;vzor &#45; obrázek B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti. vzor FigureB")

 **Obrázek B: lepší, ale stále vzoru proti panel pro příkaz**

 O trochu lepší, ale stále nežádoucí, je nastavení tohoto typu vložení v panelech nástrojů, jak je znázorněno v **obrázek B**. Tlačítka rozdělení trvat méně místa a proto jsou vylepšení přes rozevírací seznamy, obou řešení stále používají panelu nástrojů na podporu něco, co skutečně není příkaz.

 ![Panel příkazů proti&#45;vzor &#45; obrázek C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti. vzor FigureC")

 **Obrázek C: správné použití sady Visual Studio příkazového řádku vzor**

 V **obrázek C**, nastavení se váže na řadu příkazů. Neexistuje žádné globální nastavení nastavena a jsme právě jste přepínání mezi čtyř příkazů. Toto je pouze situace, ve kterém jsou přijatelné příkazy na panelu nástrojů.

### <a name="control-anti-patterns"></a>Antimodely pro ovládací prvek
 Některé antimodely pro jsou jednoduše nesprávné použití nebo prezentace ovládacího prvku nebo skupiny ovládacích prvků.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podtržení použitý jako název skupiny, ne hypertextový odkaz
 Podtržení text by měla sloužit pouze pro hypertextové odkazy.

 **Špatné:**

 ![Podtržením spojení anti&#45;vzoru v popiscích skupiny](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")

 **Podtržený text, který není hypertextový odkaz je vzor proti sady Visual Studio.**

 **Dobré:**

 ![Podtržením spojení anti&#45;vzoru v popiscích skupiny &#40;správné&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")

 **Styl správně,-hypertextový odkaz text se zobrazí prostým písmem prostředí.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknutím na zaškrtávací políčko následek zobrazení dialogu
 Kliknutím na políčko "Povolit vzdálenou plochu pro všechny role" v průvodci "Publikování Windows Azure aplikace" okamžitě otevře vyskakovací dialogové okno, proti vzoru sady Visual Studio. Kromě toho zaškrtávací políčko nevyplní se zaškrtávacím políčkem Po výběru, jiné interakční proti.

 ![Zaškrtávací políčko pop&#45;nahoru anti&#45;vzor](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")

 **Spustit až dialogové okno po kliknutí na zaškrtávací políčko proti vzoru sady Visual Studio.**

### <a name="hyperlink-anti-patterns"></a>Antimodely pro hypertextový odkaz
 Následující příklad obsahuje dva antimodely.

1. Popředí při najetí myší zapnout red znamená, že nepoužívá správná barva sdílené ze služby písma.

2. "Další informace" není odpovídající text odkazu na toto téma. Cílem uživatele je víc, přečtěte si, že je znají důsledky podle vlastní volby.

   ![Hypertextový odkaz spojení anti&#45;vzory](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")

   **Ignoruje se barva služby a pomocí "Další informace" hypertextových odkazů jsou antimodely pro Visual Studio.**

   **Lepší řešení:** pokládat otázky, uživatel by s dotazem, kliknutím na odkaz.

-   Jak fungují služby Windows Azure?

-   Kdy potřebuji projekt Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Použití "Kliknutím sem" pro odkazy
 Hypertextové odkazy by měl být samopopisných. Je proti vzor, který se má použít, "Klikněte sem" nebo libovolný podobné změny.

 **Chybný:** "Kliknutím sem pokyny o tom, jak vytvořit nový projekt."

 **V pořádku:** "Jak vytvořit nový projekt?"
