---
title: Text a nápověda uživatelského rozhraní
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5f52d4d6121faba201b37ff8fd9fcff62b46935
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067969"
---
# <a name="ui-text-and-help-for-visual-studio"></a>Text uživatelského rozhraní a nápovědu k sadě Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> Text uživatelského rozhraní a terminologie
 Srozumitelné text je zásadní význam pro efektivní uživatelské rozhraní. Software uživatelé mohou číst popisků nejprve, zejména těch nejdůležitějších pro dokončení úlohy po ruce. Statický text je pro čtení s nižší četností. Plán pro uživatele ke spuštění relace jejich práce s rychlou kontrolu celé okno, za nímž následuje čtení uživatelského rozhraní v tomto přibližné pořadí:

1.  Interaktivní ovládací prvky v Centru

2.  Potvrdit tlačítka

3.  Interaktivní ovládací prvky jinde

4.  Hlavní pokyny

5.  Další vysvětlení

6.  Titulek okna

7.  Jiný statický text v hlavní části

### <a name="usage-patterns-for-ui-text"></a>Vzory využití pro text uživatelského rozhraní

#### <a name="title-bar-text"></a>Text záhlaví
 Text záhlaví musí odpovídat příkaz, který vytvoří podřízený proces uživatelského rozhraní.

#### <a name="instructional-text-helper-text"></a>Návodný text (text pomocné rutiny)
 V některých dialogových oknech je užitečné poskytnout viditelného hlavních pokynech k vysvětlení, co dělat v okně nebo na stránce. To se někdy označuje jako "pomocné rutiny text".

##### <a name="writing-style-rules-for-helper-text"></a>Zápis pravidla stylu textu pomocné rutiny

-   Není vysvětlují zřejmý. Pokud je to nezbytně nutné, nezahrnují pokyny.

-   Návodný text je vždy umístěny v horní části dialogového okna a by měla odkazovat na úloze prováděné.

-   Přesně můžete uživatelům vysvětlete, co potřebují dělat. Vyhněte se nadměrné komunikace a redundance.

-   Zkontrolujte každé okno a odstranění duplicitní slova a příkazy.

-   Zachovejte instruktážní text krátké. Pokud Další informace jsou nezbytné pro určité uživatele nebo scénáře, zadejte odkaz na podrobné principiální téma online.

-   Zadejte text, tak, aby všechna slova obsahuje váha a je nezbytné.

-   Postupujte podle pokynů existující Microsoft k [Text uživatelského rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) a [styl a tón](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="supplemental-instructions"></a>Další pokyny
 Další pokyny poskytují další informace, které pomáhá uživatelům pochopit ovládací prvky nebo řídit seskupení. Také může být nutné pochopit, jaký formát vstupního ovládacího prvku očekává text nápovědy. Další pokyny používejte opatrně. Vyhrazeny pro případech, kdy je pravděpodobnost, že uživatel nebude plně nerozumí následky volbě jejich provedení.

 ![Doplňkové text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601 b_SupplementalText1")

 **Doplňkové text v sadě Visual Studio**

 ![Doplňkové text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601 c_SupplementalText2")

 **Doplňkové text v sadě Visual Studio**

#### <a name="infotips"></a>InfoTips
 Návodný text často, může být příliš dlouhý na pozici v místě v uživatelském rozhraní nebo může být užitečné pouze noví uživatelé tak vnímají, že jako nepořádku zkušeným uživatelům. V takovém případě by měl umístit pokyny nebo informační text jako popisek pod tip.

 InfoTips by měl umístit blízko ovládací prvky, aby se vztahují k a měla používat ikonu konkrétní informační tip, který nenáročná ještě znatelný.

 ![Informační tip ve Visual Studiu](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")

 **Příklad tip v sadě Visual Studio**

##### <a name="writing-style-rules-for-infotips"></a>Zápis pravidla pro InfoTips

-   Zapište InfoTips jako úplných větách. Vyžadují určité akce, věty a koncové interpunkce.

-   Použijte InfoTips k doplnění hlavní pokyn nebo informace. Pokud právě používáte jiná slova přepočítat hlavní myšlenku, není nutné tip.

-   Zachovejte InfoTips krátký sladké. Krátká slova a prostý, každodenního jazyka, který podporuje a může vést ke vzniku uživatele.

-   Postupujte podle pokynů existující Microsoft k [Text uživatelského rozhraní](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx) a [styl a tón](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx).

#### <a name="control-labels"></a>Popisky ovládacího prvku
 Popisky ovládacího prvku by měl být krátký a stručné a postupujte podle [Windows Desktop pokyny pro ovládací prvky](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx).

 Další informace o formátu ovládací prvek popisek a umístění v rámci uživatelského rozhraní, najdete [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

#### <a name="help-links"></a>Odkazy na nápovědu
 Odkazy nápovědy, jde umístit buď v rámci instruktážní text nebo v těle rozhraní. Mohou být odkazy na nápovědu nebo spuštění interní dialogová okna.

##### <a name="visual-style-rules-for-help-links"></a>Vizuální styl pravidla pro odkazy na nápovědu

-   Použijte pro hypertextové odkazy barvy správné prostředí. Správně upravený hypertextový odkaz nebude flash stručně červené po kliknutí. Pokud se zobrazí, je jako ukazatel toho, že prostředí barvy nejsou používány.

-   Podtržení by měla sloužit pouze při najetí myší nebo když na odkaz vložený do odstavce.

-   Podrobnější informace o vizuálu a interakce styly hypertextových odkazů naleznete v tématu tlačítka a hypertextových odkazů.

##### <a name="writing-style-rules-for-help-links"></a>Zápis pravidla stylu pro odkazy na nápovědu

-   Při spuštění dialogová okna, Udržovat standardy pro symbol tří teček: žádné tlačítko se třemi tečkami pro navigaci, symbol tří teček, pokud úloha vyžaduje dalšího uživatelského rozhraní.

     ![Odkaz na nápovědu v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601 e_HelpLink")

     **Tři tečky (...) v na odkaz Nápověda označuje, že úloha bude vyžadovat dalšího uživatelského rozhraní.**

-   Odkazy nesmí začínat znakem "Informace", protože se nejedná o záměru uživatele. Uživatel chce odpovědět konkrétní dotaz, neinicializují, nepřijímaly obecné vzdělávání.

-   Fráze nápovědy k propojení tak, aby jejich položení dotazu, že odpoví na téma.

     Chyba: "Další informace o Windows Azure Mobile Services, ceny"

     Správné: "jaké cenové možnosti jsou dostupné pro Windows Azure Mobile Services?"

-   Nikdy nepoužívejte *klikněte na tlačítko...* text odkazu.

-   Nikdy odkaz pouze slovo "sem". Toto je problematické pro některé čtečky obrazovky, které budou hlasové pouze s hypertextovým odkazem slovo.

     Chyba: "najít informace o Windows Azure Mobile Services **tady**"

     Správné: "jaké cenové možnosti jsou dostupné pro Windows Azure Mobile Services?"

-   Další informace o správný styl pro odkazy na nápovědu najdete v článku [Windows Desktop pokyny pro pomoc](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx).

#### <a name="hint-text"></a>Text nápovědy
 Text nápovědy se zobrazí jako vodoznak v rámci ovládacího prvku nebo pod ovládacím prvkem. Sice správné formátování se použije s použitím příslušného tokenu VSColors `Environment.GrayText`.

 Může se objevit v různých formách.

-   Místo popisek ovládacího prvku:

     ![Pomocného parametru text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601 f_HintText1")

-   S operací poskytující pokyny:

     ![Pomocného parametru text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601 g_HintText2")

-   Text označující požadovanou položku:

     ![Pomocného parametru text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601 h_HintText3")

#### <a name="watermark-text"></a>Vodoznakového textu
 Na prázdný návrhové ploše by měla zobrazovat text co dělat, stejně jako odkazy a v případě potřeby otevřete další související windows:

 ![Vodoznak text v sadě Visual Studio](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601 i_WatermarkText")

 **Příklad vodoznakového textu v sadě Visual Studio**

### <a name="common-terminology"></a>Běžné terminologie

|Termín|Vysvětlení|Komentář|
|----------|-----------------|-------------|
|Přihlášení / odhlášení|Příkazy používají jako synonyma s webovým rozhraním představující ověřování do webových vlastnosti. V rámci klientů použijeme tento jednou jako hodnoty nejvyšší úrovně pro přihlašování do a z připojení uživatele integrovaného vývojového prostředí, která představuje nejvyšší úrovně identitou, která poskytuje vyšší úroveň funkcí, jako je roaming a licencování, které nejsou k dispozici s další připojení.|Uživatelské rozhraní IDE je pouze funkce, která by měla představovat přihlašovací / Odhlásit se příkaz, protože představuje nejvyšší uživatelská rozhraní IDE.|
|Připojit / Odpojit|Použít na místech, kde funkci udržuje jedno připojení ke službě online.|Průzkumník serveru, kde může mít pouze jeden aktivní připojení Azure současně, je příkladem připojení/odpojení.|
|Přidat / odebrat|Bez destruktivní. Použijte v případě přidávání nebo odebírání něco ze seznamu.|Dialogové okno Správce připojení k TFS serveru seznamu je příkladem přidat nebo odebrat.|
|Odstranit|Destruktivní. Použijte pouze v případě, že element odebírá se trvale vyřazeny nebo odstranit z disku.|"Odstranit" obecně vyžaduje výzvu, pokud je výsledek odstranění souboru z disku.|

## <a name="error-messages"></a>Chybové zprávy

### <a name="overview"></a>Přehled
 Chyby dojít. Nastavení omezení pro co uživatel udělat, je rozumné prvním krokem při bránění zanedbání zabránit chybové zprávy. Ale pokud dojde k chybě, kvalitně napsané chybovou zprávu můžete urazily dlouhou cestu směrem k odstranění problému. Chybové zprávy jsou pravděpodobně jedním z nejdůležitějších typy oznámení, že se uživateli zobrazí, protože jsou synchronní a poukazovat na problém, který je potřeba vyřešit. Špatně napsaný chybové zprávy ponechte uživatelé na svých vlastních rozhodnout příčinu chyby a jakékoli možná řešení.

 Uživatelé můžou přestat dejte pozor na Nepromyšlené nebo tak dojít k zápisu pouze nezbytné zprávy, které aplikacím dodávají hodnotu pro uživatele matoucí chybové zprávy. Pokud zpráva je pouze oznámení, použijte alternativní prezentaci.

### <a name="rules-for-creating-an-error-message"></a>Pravidla pro vytváření chybovou zprávu

-   Při vytváření chybové zprávy, vyberte příslušnou chybovou úroveň pro cílovou skupinu. Cíl pro jednoduché souhrny, které poskytují akce, které uživateli umožňuje pořizovat, pokud je k dispozici. Není stav cokoli, co uživatel není potřeba znát.

-   Poskytovat konstruktivní pomoc. Je snazší přečíst a reagovat na chybovou zprávu, která obsahuje instrukce.

-   Nepoužívejte negativy double.

-   Provádění obou automatické a ruční gramatické a pravopisné zkontrolovat jakákoli chybová zpráva, kterou píšete.

-   Pro komplexní chybové zprávy Vyhněte se sekvenční komunikace. Nikdy nepoužívejte propojení F1 pro chybovou zprávu. Vlastní zprávě by měl být dostatečné.

-   Použijte správnou ikonu.

-   Ujistěte se, dotazy srozumitelné a pomocí tlačítek, které mají zrušte zaškrtnutí možností, jako je například "Odstranit" a "Storno".

-   Pro upozornění být jasné, o co se bude důsledků budete pokračovat. Tlačítka by měla zobrazovat důsledku toho.

-   U chyb popište, co může uživatel provést k vyřešení problému. Tlačítka by měla být akce nebo Řekněme, že "Zavřít". Nepoužívejte tlačítko "OK" pro chybovou zprávu.

-   Některé dotazy položte si otázku: při vytváření chybová zpráva:

    -   Může uživatel přijít na to, jak vyřešit problém s touto chybou samostatně?

    -   Používá uživatel slovník stejný jako tato chyba?

    -   Je tato chyba ambigious nebo sdíleného v několika situacích? Pokud ano, jak vám vedou uživatele k řešení, které potřebují?

#### <a name="build-errors"></a>Chyby sestavení
 Visual Studio je nástroj pro vývoj softwaru, řada jeho součástí má kompilace, převod, nebo krok vývojáři převést do binárního formátu kódování. Tyto převody mohou způsobit chyby, pokud kompilátor nemůže zpracovat nesprávně vytvořené soubory nebo pokud – možnosti kompilátoru nebyly nastaveny správně.

 Uživatelé sady Visual Studio věnovat potřeby obrovského počtu hodin vývoj řešení chyb při sestavení. Tato doba řešení zvýší v případě, že chyby mají závislosti nebo když chybové zprávy jsou napsán, což může být obtížné a odhalit příčiny chyby.

 Nejlepší chyby sestavení jsou ty, které k událostem na prvním místě, což je důvod, proč sada Visual Studio poskytuje funkce automatického dokončování a podtržení vlnovkou pro IntelliSense. Validátory schématu a podobné nástroje poskytují stejný druh zpětnou vazbu. Tyto mechanismy proaktivně provedou uživatele vytvořit ve správném formátu kód lessening pravděpodobnost vzniku chyby sestavení.

 Visual Studio poskytuje panel nástrojů, kde uživatelé můžou číst a procházet chyby, ke kterým došlo v systému windows jejich dokumentu. Klávesové zkratky jsou poskytovány tak, aby uživatel mohl rychle přejít velké množství kódu a přejít přímo na umístění problém. Visual Studio také umožňuje každé chyby sestavení vlastnit konkrétní ID – klíčové slovo/kontextové nápovědy tak, aby uživatel přejít přímo na téma nápovědy, která poskytuje podrobnější informace o této chybě.

 Chyby sestavení srozumitelné a stručné uvedení zápisu:

-   **Použití plain jazyka** , který popisuje problém s malou nebo žádnou žargonu kompilátoru. Text chyby sestavení nemůže být zbytečně technické.

-   **Popisují možné příčiny.** Například "chybí dvojtečka mezi vlastností a hodnotou v" (vlastnost): (hodnota) "prohlášení."

-   Zadejte podrobnosti o potenciální opravy. Pokud není k dispozici dostatek volného místa, může další podrobnosti umístit do příslušné téma nápovědy.

### <a name="components-of-a-well-written-error-message"></a>Součásti kvalitně napsané chybová zpráva

#### <a name="use-the-shell-dialog-service-for-error-messages"></a>Pomocí dialogového okna služby prostředí pro chybové zprávy.
 Pomocí dialogového okna služby prostředí umožňuje řídit vzhled zprávy – písma zejména – bez hlavní změny na jednotlivé prvky. Použití **IErrorInfo** mechanismy a dejte nám o nich pomocí **IVsUIShell::SetErrorInfo/ReportErrorInfo**.

#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>Zvolte prezentaci aplikace efektivní a příslušné oznámení.
 Použijte modální dialogové okno s kritické upozornění, pokud okamžité nic dělat. aby nedošlo ke ztrátě dat (synchronní oznámení). Kritické ikony jsou vyhrazené pro situace, ve které zavření zprávy bez čtení může vést k negativní důsledky. Ztráta dat je důležité situaci, která vyžaduje při reakci na úroveň upozornění. Nadměrné kritickou ikonu desensitizes uživatele na jeho význam. Pokud je v podstatě informativní chybová zpráva, vezměte v úvahu alternativy k modální dialogové okno (asynchronní oznámení).

#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>Zadejte čistý, stručné vysvětlení, proč k problému došlo místo technické vysvětlení.
 Uživatelé s technické podrobnosti vysvětlení nadměrného zatížení způsobí, že je větší pravděpodobnost Ignorovat chybové zprávy. Příklady dobré zasílání zpráv:

-   "Nelze k otevření požadovaného souboru."

-   "Nelze se připojit k Internetu."

#### <a name="provide-information-about-how-to-fix-the-problem"></a>Zadejte informace o tom, jak tento problém vyřešit.
 Nabízí návrhy uživatele o tom, jak tento problém vyřešit. Pokud neexistují žádné návrhy byla upřímná s uživatelem. Poskytují přímé odkazy na alternativní online zdrojů, například technickou podporu nebo podpory prostřednictvím komunity. Pokuste se uživatele odkazovaly na konkrétní online informace, které jsou relevantní pro problém. ID chyby zvažte možnost propojení uživatelů se vlákno diskuse o konkrétní chybu. Příklady dobré zasílání zpráv:

-   "Ujistěte se, že jsou připojené k Internetu a zkuste to znovu."

-   "Ujistěte se, zda soubor existuje a zda máte oprávnění k jeho otevření."

#### <a name="write-a-message-that-is-short-and-to-the-point"></a>Zapsat zprávu, která je krátký a výstižně.
 Chybová zpráva může upozornit, vysvětlete a nabízejí řešení, ale stále se ignoruje, pokud je příliš rozvláčný. Jedním řešením je použití progresivní zpřístupnění s tlačítko Podrobnosti. Například zadejte krátký popis nebo řešení a potom se spojí další podrobnosti v části Podrobnosti o tlačítko. Pokud se uživatelé rozhodnou přečtěte si další informace o chybě, že lze provést.

 Jazyk ve zprávě musí odpovídat:

-   **Příslušné domény.** Použijte jazyk, který uživatel rozumět. I v případě našich zákazníků jsou vývojáři, často nemají kontextu a terminologií, které máme k dispozici.

-   **Konkrétní.** Vyhněte se vágní formulace a poskytnout konkrétní názvy a umístění objekty. Například chybová zpráva jako "není platný znak" není užitečné. Které znak? "Soubor nebyl nalezen." Soubor, který?

-   **Zdvořilý.** Nemáte blame uživatele nebo je můžete stupid. Vyhněte nebezpečný nebo nevhodného jazyka (ukončit, spustit, ukončit závažné, neplatný). Vyhněte se text velkými písmeny, což se často používá jako shouting a není jako čitelný. Nepoužívejte si.

-   **Opravte.** Použijte správnou pravopis a gramatiku (i v alphas). Překlepy jsou neprofesionálně a to je absolutně.

-   **Kontextově vhodná.** Použijte tlačítko odpovídající text. Vyhněte se tlačítko "OK" a místo toho použijte "Continue" nebo "Ano/Ne"

### <a name="error-message-examples"></a>Příklady chybová zpráva

|Dobré|Špatné|
|----------|---------|
|"Číslo je již ve službě. Zkontrolujte číslo a znovu vytáčení nebo vytáčení 0 pro operátor."|-"Chyby (449): Neplatné číslo"<br />– "Tato chyba neošetřené výjimce označuje, že operace byla úspěšně dokončena."<br /><br /> ![Chybná zpráva v sadě Visual Studio](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602 a_ErrorDialog")|

## <a name="accessing-help"></a>Přístup k nápovědě

### <a name="overview"></a>Přehled
 Kromě dokumentaci na webu MSDN Visual Studio uživatel má několik přístupových bodů pomáhat uživatele v uživatelském rozhraní. Zajistit, že tyto přístupových bodů jsou stále k dispozici funkce týmy musí využívat systému nápovědy, které nabízí prostředí. Těchto přístupových bodů jsou:

-   **Pokyny a další text v dialogových oknech.** Statický text, který poskytuje směr nebo vysvětlení, buď v Uživatelském rozhraní plochy nebo při najetí myší nad ikonou informační tip.

-   **Nápověda F1** (pouze editoru). V editoru sady Visual Studio může uživatel důvěřovat, že v každém okamžiku stisknutím klávesy F1 zobrazíte tématu nápovědy specifické pro aktuální výběr. Ujistěte se, že témata související s F1 jsou vhodné a informativní.

-   **Hypertextové odkazy na témata nápovědy.** Hypertextový odkaz v rámci dialogového okna, panel nástrojů nebo návrhové plochy, které spouští tématu pomáhat uživatele v dalších informací o technologii, funkce nebo informace o tom, jak provádění různých úloh.

-   **Mechanismy pomocné rutiny uživatelského rozhraní, jako jsou inteligentní značky a vytváření dialogových oken.** Tyto mechanismy uživatele pomáhají porozumět prvku uživatelského rozhraní nebo usnadnění úlohy, jako jsou inteligentní značky nebo Tvůrce dialogová okna.

-   **Tlačítka nápovědy k uživatelskému rozhraní** (zastaralé). Viditelné ukazatele v záhlaví okna, která poskytuje přístup k související téma nápovědy F1.

### <a name="text"></a>Text

#### <a name="instructional-and-supplemental-text-in-dialogs"></a>Pokyny a další text v dialogových oknech
 V dialogových oknech, které podporují složité úkoly může být potřeba poskytnout Návodný text v rámci uživatelského rozhraní, často v horní části dialogového okna nebo blízko ní složitějšími ovládacími prvky. Zobrazit [uživatelského rozhraní text a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) podrobnosti na styl psaní.

#### <a name="infotips"></a>InfoTips
 Návodný text často, může být příliš dlouhý na pozici v místě v uživatelském rozhraní nebo může být užitečné pouze noví uživatelé tak vnímají, že jako nepořádku zkušeným uživatelům. V takovém případě by měl umístit pokyny nebo informační text jako popisek pod tip.

 InfoTips by měl umístit blízko ovládací prvky, aby se vztahují k a měla používat ikonu konkrétní informační tip, který nenáročná ještě znatelný.

 ![Informační tip ve Visual Studiu](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")

 **Příklad tip v sadě Visual Studio**

### <a name="interactive-help-mechanisms"></a>Interaktivní mechanismy na nápovědu

#### <a name="f1-help"></a>F1 – nápověda
 Nápověda F1 je vyžadován v rámci editor nebo návrhové plochy, ale jinde ne v prostředí sady Visual Studio.

#### <a name="hyperlinks-to-help-topics"></a>Hypertextové odkazy na témata nápovědy
 Hypertextové odkazy je možné provést akci, přejděte v rámci rozhraní IDE nebo spuštění nápovědy v prohlížeči. V tématu [uživatelského rozhraní text a terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology) podrobné informace o jazyce a 07.10.01 tlačítka a hypertextové odkazy na pokyny pro vizuál a rozložení.

#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>Nápověda [?] tlačítka v záhlaví dialogového okna (zastaralé)
 Tlačítka [?] Nápověda v záhlaví okna dialogová okna ve většině případů jsou zastaralé. Témata uživatelského rozhraní se už nejsou součástí našeho modelu dokumentu, a proto nemusí být k příslušné téma propojení. V podstatě totéž jako Nápověda F1 byla tlačítko nadpisu a, který už není nutné v dialogových oknech. V některých případech to stále slouží jako indikátor, že je k dispozici, další koncepční a procedurální informace i když hypertextové odkazy se běžně používají v novější uživatelského rozhraní.

##### <a name="dialogs-created-through-the-environment"></a>Dialogová okna vytvořených prostřednictvím prostředí
 Mnoho prostředí dialogová okna jsou vytvořené prostřednictvím **VBDialogBoxParam** funkce. Tato sdílená funkce byla aktualizována jako pomoc při přesunu **pomáhají** tlačítko z dialogového okna **?** tlačítko při zachování architekturu, která je zpětně kompatibilní a rozšiřitelný.

 Konkrétně **VBDialogBoxParam** funkce zkoumá šablony dialogového okna pro tlačítko, jehož ID je **IDHELP** (9) nebo popisek je **pomáhají** nebo **& pomáhají**. Pokud se najde tlačítko Nápověda je skrytá a **WS_EX_CONTEXTHELP** styl je přidán do dialogového okna, které umístí **?** tlačítko v záhlaví dialogového okna.

 Když se vytvoří dialogové okno, nabízených oznámení proc dialogového okna do zásobníku a vyvolá dialogové okno s předběžného zpracování proc dialogové okno s názvem **DialogPreProc**. Když **?** Po kliknutí na tlačítko, odešle **WM_SYSCOMMAND** z **SC_CONTEXTHELP** do dialogového okna. **DialogPreProc** zaznamená tento příkaz a ho změní na **WM_HELP** zprávu, která se předá do původní procedury dialogového okna

 Většina prostředí vytvořené dialogová okna mít tlačítko Nápověda v dialogovém okně. Po zobrazení dialogového okna na tlačítko Nápověda je skryto automaticky a pouze **?** tlačítko funguje. Pokud **?** tlačítko je někdy odebrat nebo změnit ve Windows, toto řešení umožňuje rychle přejděte zpět do původní tlačítko Nápověda.

 Toto řešení umožňuje čtyři předpoklady, které by mohly způsobit chyby:

- Tlačítko Nápověda v dialogovém okně je **IDHELP** (9).

- Dialogové okno vypadá správně, když je skrytý na tlačítko Nápověda.

- Dialogové okno nenahrazuje jeho návrat winproc.

- Dialogové okno není vložené uvnitř jiného dialogového okna.

  Pokud dialogové okno se nachází v rámci msenv a nepoužívá **VBDialogBoxParam**, prozkoumat využití **VBDialogBoxParam** před implementací vlastní obslužné rutiny.

##### <a name="dialogs-created-through-other-packages"></a>Dialogová okna, které jsou vytvořené pomocí jiných balíčků
 Můžete implementovat svoje vlastní řešení pro dialogová okna, které se nacházejí mimo msenv. Pro třídy sdílené dialogového okna v vašeho balíčku VSPackage zvažte přechod na tlačítko na záhlaví okna nebo implementace obslužné rutiny pro každý dialogového okna. Následující kód představuje kostru implementace k vám pomůžou začít:

```
struct DLGPROCITEM
{
    FARPROC proc; // The info used to create the dialog.
    DLGPROCITEM* procPrev;
};

DLGPROCITEM* g_dlgProcStack = NULL;

// A dialog starter/wrapper function is used to push the new
// dialog proc to the top of our dialog proc stack.

int SomeDialogStarterFunction(hinst, id, proc, etc)
{
    if (g_dlgProcStack == NULL)
    {
        g_dlgProcStack = new DLGPROCITEM;
        g_dlgProcStack->procPrev = NULL;
    }
    else
    {
        DLGPROCITEM* procItem = new DLGPROCITEM;
        g_dlgProcStack->procPrev = g_dlgProcStack;
        g_dlgProcStack = procItem;
    }
}

// Pop this dialog proc off the dialog proc stack.

DialogBoxIndirectParam...(...)
{
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;
    delete g_dlgProcStack;
    g_dlgProcStack = procItem;
}

// A wrapper dialog procedure will allow us to capture the
// SC_CONTEXTHELP button on the title bar from Windows and
// forward it as a simple WM_HELP message back to the dialog.

INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,
    WPARAM wParam, LPARAM lParam)
{
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)
    {
        uMsg = WM_HELP;
        wParam = 0;
        lParam = 0;
    }
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,
        hwndDlg, uMsg, wParam, lParam);
}
```

##### <a name="help-buttons-in-managed-code"></a>Tlačítka nápovědy ve spravovaném kódu
 Přepisování výchozího chování tlačítko okno nadpis panelu Nápověda je snadné ve spravovaném kódu. Níže je kompletní ukázkovou aplikaci, která ukazuje toto chování. V podstatě je potřeba přepsat formuláře **WndProc** metodu a poté fire vypnout nápovědy klávesy F1 požadavků, kdy **SC_CONTEXTHELP** zachytit zprávy.

```
using System;
using System.Windows.Forms;

public class HelpForm : Form
{
    private const int SC_CONTEXTHELP = 0xF180;
    private const int WM_SYSCOMMAND = 0x0112;

    public HelpForm()
    {
        this.ClientSize = new System.Drawing.Size(300, 250);
        this.HelpButton = true;
        this.MaximizeBox = false;
        this.MinimizeBox = false;
        this.Name = "HelpForm";
        this.Text = "Help Form";
    }

    protected override void WndProc(ref Message m)
    {
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)
            ShowHelp();
        else
            base.WndProc(ref m);
    }

    private void ShowHelp()
    {
        MessageBox.Show("F1 Help goes here.");
    }

     [STAThread]
    static void Main()
    {
        Application.EnableVisualStyles();
        Application.EnableRTLMirroring();
        Application.Run(new HelpForm());
    }
}
```

## <a name="see-also"></a>Viz také
 [Písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md) [rozložení pro sadu Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md) [oznámení a postup pro Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)
