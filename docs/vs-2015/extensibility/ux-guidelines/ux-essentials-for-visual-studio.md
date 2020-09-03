---
title: Základy uživatelského prostředí
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181410"
---
# <a name="ux-essentials-for-visual-studio"></a>Základy uživatelského prostředí pro Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>Osvědčené postupy

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. je konzistentní v rámci prostředí sady Visual Studio.

- Sledujte existující vzory interakce v rámci prostředí.

- Navrhněte funkce, které mají být v souladu s vizuálním jazykem prostředí a craftsmanship požadavky.

- Použijte sdílené příkazy a ovládací prvky, pokud existují.

- Porozumět hierarchii sady Visual Studio a způsobu, jakým vytváří kontext a řídí uživatelské rozhraní.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. použijte službu prostředí pro písma a barvy.

- Uživatelské rozhraní by mělo respektovat aktuální nastavení písma prostředí, pokud není Vystavené pro přizpůsobení na stránce písma a barvy v dialogovém okně Možnosti.

- Prvky uživatelského rozhraní musí používat službu VSColor pomocí tokenů sdíleného prostředí nebo tokenů specifických pro funkce.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Zajistěte, aby všechny trojrozměrnés byly konzistentní s novým stylem VS.

- Postupujte podle principů návrhu sady Visual Studio pro ikony, glyfy a další grafiky.

- Neumísťujte text do grafických prvků.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Navrhněte z perspektivy zaměřené na uživatele.

- Vytvořte tok úkolů před jednotlivými funkcemi v rámci něj.

- Seznamte se s uživateli a zajistěte, aby znalosti byly ve specifikaci explicitní.

- Při kontrole uživatelského rozhraní vyhodnoťte kompletní prostředí a také podrobnosti.

- Navrhněte uživatelské rozhraní tak, aby zůstalo funkční a atraktivní bez ohledu na národní prostředí nebo jazyk.

## <a name="screen-resolution"></a>Rozlišení obrazovky

### <a name="minimum-resolution"></a>Minimální rozlišení
 Minimální rozlišení pro Visual Studio Dev14 je 1280x1024. To znamená, že je *možné* použít Visual Studio v tomto řešení, i když se nemusí jednat o optimální prostředí pro uživatele. Není zaručeno, že všechny aspekty budou použitelné v řešeních nižších než 1280x1024.

 Velikost počátečního dialogového okna nesmí být větší než 1000 pixelů, aby se vešla do rámce IDE v rámci tohoto minimálního rozlišení na 96 dpi.

### <a name="high-density-displays"></a>Displeje s vysokou hustotou
 Uživatelské rozhraní v aplikaci Visual Studio musí dobře fungovat ve všech faktorech škálování DPI, které Windows podporuje, od tohoto pole: 150%, 200% a 250%.

## <a name="anti-patterns"></a>Anti-patterny
 Visual Studio obsahuje mnoho příkladů uživatelského rozhraní, které následují podle našich pokynů a osvědčených postupů. Ve snaze zajistit konzistenci se vývojáři často vypůjčují ze vzorů návrhu uživatelského rozhraní, podobně jako při sestavování. I když je to dobrý přístup, který nám pomáhá zajistit konzistenci v souvislosti s uživatelem a vizuálním návrhem, provedeme s několika podrobnostmi, které nesplňují naše pokyny z důvodu omezení plánu nebo stanovení priorit chyb. V těchto případech nechceme, aby týmy kopírovaly jeden z těchto "antipatterns", protože šíří špatné nebo nekonzistentní uživatelské rozhraní v prostředí sady Visual Studio.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Požadovaná pole/nastavení zobrazená v chybovém stavu ve výchozím nastavení

#### <a name="feature-team-goals"></a>Cíle týmu funkcí

- Upozorněte uživatele, že přidali prvek, který musí být nakonfigurován.

- Nakreslete pozornost uživatele do oblastí, které vyžadují vstup.

#### <a name="anti-pattern-solution"></a>Řešení proti vzorům
 Jakmile uživatel zahájí akci a předtím, než úkol dokončí, umístěte hned ikony kritického zastavení vedle oblastí, které vyžadují konfiguraci.

#### <a name="example-manifest-designer-declarations"></a>Příklad: deklarace návrháře manifestu
 Přidáním deklarace do seznamu se okamžitě umístí do chybového stavu, který přetrvává, dokud uživatel nenastaví požadované vlastnosti.

 V takovém případě je k dispozici další obavy, protože ikona použitá pro výstrahu obsahuje znak "x", takže nelze vedle ní použít běžné ikony pro odebrání. V důsledku toho uživatelské rozhraní používá tlačítko odebrat a další ovládací prvek clunky.

 ![Deklarace chyb návrháře manifestu anti&#45;vzor](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti – vzor")

 **Umístění uživatelského rozhraní do chybového stavu je ve výchozím nastavení sady Visual Studio anti-Pattern.**

#### <a name="alternatives"></a>Alternativy
 Mnohem lepší řešení tohoto problému je:

- Povolí uživateli přidat deklaraci bez upozornění a pak okamžitě přejít na nastavení vlastností položky.

- Pokud se fokus přesune z položky, například pokud chcete přidat další deklaraci do seznamu nebo se pokusit změnit karty v návrháři, přidejte ikonu upozornění (zlatý trojúhelník).

- Pokud se uživatel pokusí změnit karty před nastavením vlastností u všech deklarací, zobrazí se dialogové okno s vysvětlením, že aplikace nebude sestavovat (nebo bez ohledu na dopady), dokud nebudou upozornění vyřešena. Pokud uživatel zavře dialogové okno a karty změny se zobrazí, na kartě deklarace se přidá ikona (kritická nebo upozornění, podle potřeby).

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Vynucení čtení textu před chybějícím uživatelským ROZHRANÍm uživatelem

#### <a name="feature-team-goals"></a>Cíle týmu funkcí
 Nepovolujte uživateli možnost Zavřít uživatelské rozhraní, aniž byste museli nejprve zobrazit text vysvětlení.

#### <a name="anti-pattern"></a>Anti-Pattern
 Tým vkládá odkazy na videa do různých míst v uživatelském rozhraní VS se rozhodla o společný vzor tlačítka pro uzavření X a vysvětlení popisu tlačítka, jak je uvedeno v uživatelském rozhraní, a místo toho se implementuje rozevírací seznam a odkaz "příště nezobrazovat".

 ![Vzorový text anti&#45;vzor &#45; nesprávný](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Nesprávné: vynucení čtení vysvětlujícího textu před ukončením uživatelského rozhraní v sadě Visual Studio je antipattern.**

#### <a name="result"></a>Výsledek
 Místo jednoduchého tlačítka Zavřít (jedním kliknutím) se uživatel nuceně pustit uživatelské rozhraní na všech místech, kde se zobrazují odkazy na video, pomocí dvou kliknutí.

#### <a name="alternatives"></a>Alternativy
 Správným návrhem této situace by bylo postupovat podle vzorů, které jsou společné pro Internet Explorer, Office a Visual Studio: při najetí myší může uživatel zobrazit popis popisu a jedno kliknutí skryje uživatelské rozhraní.

 ![Vzorový text anti&#45;vzor &#45; správný](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-vzor – správné")

 **Oprava: jak je navrženo, odkazy na videa by měly zobrazit popis tlačítka s dalšími informacemi při najetí myší a kliknutím na "X" by se měla zpráva Zavřít, aniž by bylo potřeba provádět další interakci.**

### <a name="using-command-bars-for-settings"></a>Použití panelů příkazů pro nastavení
 ![Panel příkazů anti&#45;vzor &#45; obrázek A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-vzor-obrázek")

 **Obrázek A: anti-Pattern panelu příkazů**

 **Obrázek A** představuje tento antipattern: umístění nastavení pod příkazové tlačítko, které se vztahuje na více než jenom příkaz. V této skice jsou k dispozici příkazy kromě příkazu Spustit ladění – například zobrazení v prohlížeči, spuštění bez ladění a krokování – to bude platit pro vybrané nastavení.

 ![Panel příkazů anti&#45;vzor &#45; obrázek B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-Pattern-FigureB")

 **Obrázek B: lepší, ale stále ještě anti-Pattern panelu příkazů**

 Mírně lepší, ale stále nežádoucí, je umístit nastavení tohoto typu na panely nástrojů, jak je znázorněno na **obrázku B**. I když rozdělená tlačítka pobírají méně místa a z toho důvodu je lepší podobu v rozevíracích seznamech, oba návrhy stále používají panel nástrojů k povýšení něčeho, co není ve skutečnosti příkaz.

 ![Panel příkazů anti&#45;vzor &#45; obrázek C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-Pattern-FigureC")

 **Obrázek C: správné použití vzoru panelu příkazů sady Visual Studio**

 Na **obrázku C**je nastavení vázáno na řadu příkazů. Není nastavené žádné globální nastavení a právě se přepíná mezi čtyřmi příkazy. Jedná se o jedinou situaci, kdy jsou příkazy na panelu nástrojů přijatelné.

### <a name="control-anti-patterns"></a>Řízení anti-patternů
 Některé anti-patterny jsou jednoduše nesprávného použití nebo prezentace ovládacího prvku nebo skupiny ovládacích prvků.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Podtržení používané jako popisek skupiny, nikoli hypertextový odkaz
 Text podtržení by měl být použit pouze pro hypertextové odkazy.

 **Špatné:**

 ![Podtržení typu anti&#45;v popiscích skupin](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 – g_GroupLabelIncorrect")

 **Podtržený text, který není hypertextovým odkazem, je anti-Pattern sady Visual Studio.**

 **Dobré:**

 ![Podtržení&#45;ho vzoru v popisech skupin &#40;správné&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 – h_GroupLabelCorrect")

 **Správně se styly, text, který není hypertextový odkaz, se v písmu prostředí zobrazí jako nezobrazený.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Kliknutím na zaškrtávací políčko v okně dojde k zobrazení okna.
 Zaškrtnutím políčka Povolit vzdálenou plochu pro všechny role v Průvodci publikováním aplikace systému Windows Azure se okamžitě zobrazí automaticky otevírané okno, anti-Pattern sady Visual Studio. Kromě toho pole se zaškrtávacím políčkem po výběru neplní zaškrtávací políčko, další anti-vzor interakce.

 ![Zaškrtávací políčko&#45;kontrolního bodu&#45;](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 – i_CheckboxPopup")

 **Po kliknutí na zaškrtávací políčko se zobrazí dialogové okno sady Visual Studio anti-Pattern.**

### <a name="hyperlink-anti-patterns"></a>Anti-vzory hypertextových odkazů
 Následující příklad obsahuje dva anti-patterny.

1. Při najetí myší na červenou barvu se při použití ukazatele myši zapíná správná sdílená barva ze služby písma.

2. "Další informace" není vhodný text pro odkaz na koncepční téma. Cílem uživatele není získat další informace, je porozumět cílům jejich výběru.

   ![Vzorová ochrana před&#45;mi hypertextovými odkazy](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 – j_HyperlinkIncorrect")

   **Ignorování barevné služby a použití možnosti "Další informace" pro hypertextové odkazy jsou anti-patterny sady Visual Studio.**

   **Lepší řešení:** Vyžádejte si otázku, na kterou se uživatel bude dotazovat kliknutím na odkaz.

- Jak fungují služby Windows Azure?

- Kdy potřebuji projekt Windows Azure Mobile Services?

#### <a name="using-click-here-for-links"></a>Použití "kliknutí sem" pro odkazy
 Hypertextové odkazy by měly být samoně popisné. Je to anti-vzor pro použití "kliknutí sem" nebo jakékoli podobné variace.

 **Chybné:** Kliknutím sem zobrazíte pokyny k vytvoření nového projektu. "

 **Dobrá akce:** "Návody vytvořit nový projekt?"
