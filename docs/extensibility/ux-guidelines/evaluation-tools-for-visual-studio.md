---
title: Nástrojů pro Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147330"
---
# <a name="evaluation-tools-for-visual-studio"></a>Nástrojů pro Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Kontrolní seznam řemeslné ruční práce pro sadu Visual Studio  
 Tento kontrolní seznam použijte k vyhodnocení kvality činnost koncového uživatele podrobnosti visual a interakce.  
  
### <a name="overview"></a>Přehled  
  
-   Ověřte, že všechny příkazy za následek zpětnou vazbu, která informuje uživatele, že byla provedena jejich příkazy.  
  
-   Ověřte, že všechny prvky uživatelského rozhraní a ovládací prvky jsou viditelné ve všech motivy a v režimu vysokého kontrastu.  
  
-   Ověřte, že neaktivní a aktivní výběr jsou vždy rozlišené, jak v standard a režimu vysokého kontrastu.  
  
-   Ověřte, že fokus je vždy viditelné a zřejmá.  
  
### <a name="performance"></a>Výkon  
  
-   Ověřte, zda některé druh "zaneprázdněn" indikátoru je zobrazen, pokud příkaz má více než jedna sekunda k dokončení.  
  
-   Ověřte, že příkaz má více než 10 sekund. Chcete dokončit, zobrazí panel explicitní průběh buď determinate (doporučeno) nebo neurčitou, se zobrazí.  
  
### <a name="ui-text"></a>Textu uživatelského rozhraní  
  
-   Ověřte, že všechny popisky se rozlišují větu nebo název a zda žádný text zcela malá písmena.  
  
    ||Opravte|Nesprávný|  
    |-|-------------|---------------|  
    |**Text příkazu (všechny)**|Věty:<br /><br /> **Název adresáře:**|Název adresáře:|  
    |**Text tlačítka (klient)**|První písmeno velké:<br /><br /> **[Nastavit jako výchozí]**|VÝCHOZÍ SADA AS|  
    |**Text tlačítka (online)**|Věty:<br /><br /> **[Nastavit jako výchozí]**||  
  
-   Ověřte, zda všechny popisky, s výjimkou záhlaví skupiny a tlačítka, končit dvojtečkou a předcházet ovládací prvek, ke kterému jsou spárovat.  
  
-   Ověřte, že tlačítka, příkazy a příkaz odkazy, které spustit uživatelské rozhraní pro zachycení uživatelského vstupu končit třemi tečkami **[...]** .  
  
     Příklady:  
  
    -   **[Rozšířené...]**  tlačítko na dialogové okno.  
  
    -   Parametry příkazu v nabídce Nástroje (**nástroje > Možnosti**) by neměla získat třemi tečkami, protože spuštění dialogu samotné je záměr příkazu.  
  
-   Ověřte, zda uživatelské rozhraní obsahuje žádné zkratky, s výjimkou standardní podmínky. Například HTML ani TCP/IP musí být vypsány, i když OOM (nedostatek paměti) a PII (identifikovatelné osobní údaje), by měly.  
  
### <a name="keyboard-access"></a>Použití klávesnice  
  
-   Ověřte, zda je způsob, jak každý dosáhnout pomocí klávesnice. Obvykle je to možné udělat prostřednictvím klávesnice přístupu pro každý ovládací prvek, ale pro některé oblasti vysoce visual je přijatelné alternativní řešení například přejdete na zobrazení kódu.  
  
-   Ověřte, že můžete kartě prostřednictvím ovládacích prvků v logickém pořadí (zleva doprava a shora dolů). Přestože se doporučuje pro většinu ovládací prvky, ne všechny ovládací prvky vyžadují tento přístup. Ověřte například, tento přepínač, ovládací prvky jsou ve skupině s zastavení jedné karty.  
  
-   Ověřte, zda všechny ovládací prvky popisky a zda má každý popisek symbol a (výjimky patří některé-označený ovládací prvky, které může díky ovládacího prvku s popiskem na kartě).  
  
-   Ověřte, že nejsou klávesovými konflikty.  
  
### <a name="fonts"></a>Písma  
  
-   Ověřte, zda všechny písem (řez, velikost, barvu) se používají konzistentně a Udržovat hierarchii.  
  
-   Ověřte, zda všechny prvky uživatelského rozhraní pomocí služby písma prostředí. (Viz [písma a formátování pro sadu Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Chcete-li zkontrolovat, pokud služba používá, přejděte na **nástroje > Možnosti > písma a barev**. V rozevírací nabídce nastavení zvolte písmo prostředí a změnit tučné písmo stylistically (například Svoboda nebo Comic sítě SAN) a nastavit velikost na 12 pt. Klikněte na tlačítko OK. Možná budete muset restartovat integrovaného vývojového prostředí, ale většina uživatelského rozhraní se změní okamžitě. Oblasti, které nejsou vyzvednutí Změna písma i při restartování nepoužívají písmo prostředí.  
  
-   Ověřte, že písma, která jsou odvozená služby (například tučné a zvětšeným text) zachovat jejich velikost a formátování ve vztahu k "normální" text při změně velikosti písma prostředí.  
  
-   Ověřte, že zde nejsou žádné chyby výstřižek z důvodu zvětšeným písem. Písma, která získat oříznut jsou pravděpodobně výsledkem pevnou výšku ovládacích prvků nebo pevnou výšku kontejnerů.  
  
### <a name="dialogs"></a>Dialogová okna  
  
-   Ověřte, že název dialogového okna je stejný jako příkaz, který je spuštěn.  
  
-   Ověřte, zda všechny standardní ovládací prvky jsou konzistentní s operačním systémem: barva pozadí je standardní a žádná opatření má mít speciální použití šablon re styl, který umožní jejich zobrazí liší od standardní ovládací prvky.  
  
-   Ověřte, zda okraje v rámci formuláře by měl být 12 pixelů a by se měla objevit jednotné a konzistentní.  
  
-   Ověřte, že zobrazují dialogová okna v prostředí IDE nebo okně, které je vytvořený na střed.  
  
-   Pokud je to užitečné, dialogová okna by měl být umožňující změnu velikosti. Dialogová okna, které jsou s možností změny velikosti ověřte, že při změně velikosti, příslušné ovládací prvky musíte změnit velikost při další části dialogového okna zůstat konstantní.  
  
-   Ověřte, že s možností změny velikosti dialogová okna uchovat jakékoli velikosti upravit uživatele (velikost, umístění, rozšíření ovládací prvky dialogového okna a tak dále).  
  
-   Ověřte, zda je v záhlaví žádná ikona.  
  
-   Ověřte, že neexistují žádné tlačítka Minimalizovat a maximalizovat v záhlaví.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Dialogové okno operace tlačítka (pouze VS klient)  
  
-   Ověřte, zda jsou operace tlačítka v tomto pořadí: **OK**, **zrušit**, **použít**.  
  
-   Ověřte, že **OK** a **zrušit** tlačítka jsou standardní velikost: 75 x 23 pixelů.  
  
-   Ověřte, že **OK** a **zrušit** tlačítka jsou stejné velikosti bez ohledu na délku řetězce.  
  
-   Pokud popisek na tlačítko operaci vyžaduje tlačítko je větší než standardní, ověřte, že odpovídající **zrušit** tlačítko je rovna velikosti.  
  
-   Ověřte, zda je 6 pixelů odsazení mezi tlačítka a přidružených ovládacích prvcích.  
  
-   Ověřte, zda **OK** a **zrušit** tlačítka nemají klávesové zkratky (přístupové klávesy definované podtržené písmeno).  
  
-   Ověřte, že jedno tlačítko (obvykle **OK**) má právě fokus ve výchozím nastavení.  
  
-   Ověřte, že **Esc** zruší dialogové okno  
  
-   Ověřte, že **Enter** provede výchozího tlačítka, pokud není v ovládacím prvku, který zpracovává Enter fokus.  
  
-   Ověřte, zda **OK** a **zrušit** tlačítka jsou umístěny v pravém dolním rohu dialogu. Ve výjimečných výjimkách je přijatelné pro mají být skládaný svisle v pravém horním rohu.  
  
-   Ověřte, že svislé konfigurace se používá pouze v případě, že jsou ostatní tlačítka v vodorovné zarovnání v dialogovém okně.  
  
### <a name="control-standards"></a>Standardy ovládací prvek  
  
#### <a name="general"></a>Obecné  
  
-   Ověřte, jestli, pokud je to možné, jsou dobrý výchozí hodnoty pro urychlení interakci s uživatelem a uživatelé směrem k bezpečné a běžné výsledek.  
  
-   Ověřte, že standardní ovládací prvky chovají stejným způsobem jako tak, aby uživatelé věděli, co se stane na základě starší prostředí.  
  
#### <a name="label-controls"></a>Popisek – ovládací prvky  
  
-   Zkontrolujte, zda má každý ovládací prvek popisek a každý popisek je vizuálně spárován s jeho ovládací prvek (obvykle v rozsahu 4 až 6 pixelů), bude co nejblíže k jeho odpovídající prvku než a jiných ovládacích prvků.  
  
-   Ověřte, že popisky jsou umístěny vyprázdnit levá pomocí ovládacího prvku levá strana, pokud nad a zarovnaný na střed ve vodorovném směru, takže směrného plánu popisku je zarovnáno s směrného plánu ze vstupního textu, pokud umístěný na levé straně.  
  
-   Ověřte, že pokud několik skládaný popisek a vstupní ovládací prvky jsou umístěny na levé straně ovládacího prvku, popisky jsou zarovnané vlevo a stejnou vzdálenost od levého okraje dialogového okna, nikdy vyprázdnění práva a stejnou vzdálenost z ovládacích prvků. Dvojice by měl být rozloženy rovnoměrně, pokud potřebují další mezery udávajících seskupení.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Vstupní ovládací prvky (textová pole a pole se seznamem)  
  
-   Ověřte, zda při použití výchozí prostředí písmo, výška zobrazení pro textová pole, pole se seznamem a tlačítka, jsou všechny 23 pixelů.  
  
-   Pokud se používá textu nápovědy, ověřte, že barvu je nastavena na `Environment.ControlEditHintText` pomocí služby barev.  
  
-   Pokud je datové pole povinné pole, které musí být označeny jako nové, ověřte:  
  
    -   který je nastaven na pozadí `Environment.ControlEditRequiredBackground` popředí je nastavená na `Environment.ControlEditRequiredHintText`  
  
    -   zda je text nápovědy v rámci ovládací prvek, který se zobrazí jako **"\<požadované >"**  
  
#### <a name="button-controls"></a>ovládací prvky tlačítek  
  
-   Ověřte, zda jsou tlačítka minimální velikost 75 x 23 pixelů, pokud požadavků delší text.  
  
-   Ověřte, že tlačítka mít levé a pravé okraje 3 až 5 pixelů, jakož i odsazení pro obsah.  
  
-   Se dá použít malé odmocnina tlačítko s jenom tři tečky **[...]**  na něm místo **[Procházet...]**  tlačítko (nebo podobné funkce). Pokud se používá, ověřte, zda tlačítko 23 x 23 velikost.  
  
-   Pokud je více než jedna **[Procházet...]**  tlačítko v dialogu a potom ověřte, že zkrácená verze (jen třemi tečkami **[...]** ) se používá pro všechny.  
  
-   Ověřte, že se třemi tečkami **[...]**  tlačítka nemají symbol a. Pokud je fokus na vstupního ovládacího prvku u ní, přesuňte jedné karty fokus se třemi tečkami.  
  
-   Ověřte, že tlačítka, příkazy a příkaz odkazů, které spouštějí sekundární uživatelské rozhraní, které jsou zaznamenány další uživatelský vstup musí končit třemi tečkami **[...]** .  
  
#### <a name="hyperlinks"></a>Hypertextové odkazy  
  
-   Ověřte, že ovládacího prvku hypertextový odkaz nikdy bliká red, když je aktivní. Toto je indikátor, službu barva není ani použití  
  
-   Ověřte, zda jsou VS barvy používané:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Ověřte, že hypertextové odkazy zobrazí modré s žádné podtržení, pokud vložené do odstavec.  
  
#### <a name="check-boxes"></a>Zaškrtávací políčka  
  
-   Pokud je zaškrtávací políčko víceřádkový text, ověřte, že pole zarovnaná s první řádek textu, není svisle na střed mezi všechny řádky.  
  
-   Ověřte, zda zaškrtávací políčka vždy označují binární volby a není navigaci uživatele nebo otevřete nové windows nebo stránky.  
  
-   Pokud zaškrtávací políčko představuje možnost související s vstupního ovládacího prvku, ověřte, že je umístěný vyprázdnit vlevo a velmi zavřete pod, řídíte, aby znamenat jejich vztah.  
  
-   Ověřte, zda je zaškrtávací políčko **nikdy** použít jako prostředek k povolení celý obsah dialogového nebo stránky.  
  
#### <a name="group-boxes"></a>Skupinové rámečky  
  
-   Ověřte, že dialogové okno neobsahuje jednoduchý skupinový rámeček v něm, který obsahuje celý obsah dialogového okna.  
  
-   Ověřte, že existují alespoň dvě ovládacích prvků v každé skupině pole.  
  
-   Zřídka by měla existovat více než dva skupinové rámečky na dialogové okno.  
  
-   Ověřte, že neexistují žádné vnořené skupinové rámečky.  
  
### <a name="icons"></a>Ikony  
  
-   Ověřte, že ikony zobrazují správně obráceným v tmavým motivem.  
  
-   Ověřte, že všechny ikony jsou založeny na základní koncepty.  
  
-   Ověřte, zda každá ikona je odlišné, snadno rozpoznat a neobsahuje více než dvěma konceptů (bez stavu modifikátor/jazyk).  
  
-   Ověřte, že zobrazuje ikonu základní zarovnaný na střed v prostoru.  
  
-   Ověřte, že všechny ikony zobrazují čitelná v režimu vysokého kontrastu.  
  
-   Ověřte, že všechny barvu použitou zarovnaná s standardy využití barev.  
  
-   Ověřte, že neexistují žádné olemování (hranice) kolem ikony. (Pokud existuje, bylo by měl odpovídat barvu pozadí přiléhající uživatelského rozhraní).  
  
### <a name="touch-enabled-ui"></a>Povolit dotykové ovládání uživatelského rozhraní  
  
-   Ověřte, zda jsou interaktivní ovládací prvky dostatečně velký pro být snadno touchable – minimální **23 x 23 pixelů** velikost  
  
-   Ověřte, zda jsou nejčastěji používané ovládací prvky alespoň **40 x 40 pixelů** velikost.  
  
-   Ověřte, že interaktivní ovládací prvky alespoň **5 pixelů mezery** mezi nimi