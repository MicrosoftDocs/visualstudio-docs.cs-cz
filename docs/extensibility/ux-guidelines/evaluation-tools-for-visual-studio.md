---
title: Nástroje pro vyhodnocení Visual Studio | Microsoft Docs
description: Pomocí tohoto kontrolního seznamu můžete vyhodnotit kvalitu uživatelského prostředí u podrobností o vizuálech a interakcích u nových funkcí, které pro Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: baee9f3e2eaefcd659f8428bd566711949d0fe90
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900756"
---
# <a name="evaluation-tools-for-visual-studio"></a>Nástroje pro vyhodnocení pro Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Kontrolní seznam pro Visual Studio
 Pomocí tohoto kontrolního seznamu můžete vyhodnotit kvalitu uživatelského prostředí pro podrobnosti vizuálu a interakce.

### <a name="overview"></a>Přehled

- Ověřte, že všechny příkazy mají za následek zpětnou vazbu, která uživatele informuje o tom, že byly provedeny jejich příkazy.

- Ověřte, že jsou všechny prvky a ovládací prvky uživatelského rozhraní viditelné ve všech motivech a Vysoký kontrast režimu.

- Ověřte, že neaktivní a aktivní výběr jsou vždy rozlišené ve standardním i Vysoký kontrast režimu.

- Ověřte, že fokus je vždy viditelný a zřejmý.

### <a name="performance"></a>Výkon

- Ověřte, že se zobrazuje nějaký indikátor zaneprázdnění, pokud dokončení příkazu trvá déle než jednu sekundu.

- Ověřte, že pokud dokončení příkazu trvá déle než 10 sekund, zobrazí se explicitní indikátor průběhu, který určuje (upřednostňovaný) nebo neurčitý.

### <a name="ui-text"></a>Text uživatelského rozhraní

- Ověřte, že všechny popisky jsou velká a malá písmena a že žádný text není zcela malými písmeny.

    ||Správná odpověď.|Chyba|
    |-|-------------|---------------|
    |**Text příkazu (vše)**|Velká písmena ve větě:<br /><br /> **Název adresáře:**|Název adresáře:|
    |**Text tlačítka (klient)**|Případ nadpisu:<br /><br /> **[ Nastavit jako výchozí ]**|NASTAVIT JAKO VÝCHOZÍ|
    |**Text tlačítka (online)**|Velká písmena ve větě:<br /><br /> **[ Nastavit jako výchozí ]**||

- Ověřte, že všechny popisky kromě záhlaví a tlačítek skupin končí dvojtečkou a předchází ovládacímu prvku, se kterým jsou spárované.

- Ověřte, že se v uživatelském rozhraní spouští tlačítka, příkazy a odkazy, které zachycují uživatelský vstup na konci se třemi **tečkami (**).

  Příklady:

  - Tlačítko **[Upřesnit...]** v dialogovém okně.

  - Možnosti příkazu v nabídce Nástroje (**Nástroje > Možnosti**) by neměly získat tři tečky, protože samotné spuštění dialogového okna je záměrem příkazu.

- Ověřte, že uživatelské rozhraní neobsahuje žádné zkratky s výjimkou standardních termínů. Nemusí být například zadán kód HTML ani PROTOKOL TCP/IP, i když by měly být zadány informace OOM (mimo paměť) a PII (identifikovatelné osobní údaje).

### <a name="keyboard-access"></a>Přístup pomocí klávesnice

- Ověřte, že existuje způsob, jak provést každý úkol pomocí klávesnice. Obecně se toho dosahuje prostřednictvím přístupu ke každému ovládacímu prvku pomocí klávesnice, ale u některých vysoce vizuálních oblastí je přijatelné alternativní řešení, jako je zobrazení kódu.

- Ověřte, že můžete procházet ovládací prvky v logickém pořadí (zleva doprava a shora dolů). I když se jedná o osvědčený postup pro většinu kontrol, ne všechny kontroly tento přístup vyžadují. Ověřte například, že ovládací prvky přepínačů jsou ve skupině s jednou zastavte tabulátor.

- Ověřte, že všechny ovládací prvky mají popisky a že každý popisek má mnemotechnický symbol (výjimky zahrnují některé ovládací prvky bez popisků, které můžou následovat po ovládacím prvku označeném na kartě).

- Ověřte, že ne docházet ke konfliktům ve virtuálních zařízeních.

### <a name="fonts"></a>Písma

- Ověřte, že se všechna písma (tvář, velikost, barva) používají konzistentně a udržují hierarchii.

- Ověřte, že všechny prvky uživatelského rozhraní používají službu písem prostředí. (Viz [Písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pokud chcete zkontrolovat, jestli se služba používá, přejděte na Nástroje > možnosti > Písma a **barvy.** V rozevíracím seznamu Nastavení zvolte Písmo prostředí, změňte plochu písma na něco stylově odlišného (například Ha jejich nebo 12 bodů) a nastavte velikost na 12 bodů. Pak klikněte na OK. Možná budete muset integrované vývojové prostředí restartovat, ale většina uživatelského rozhraní se okamžitě změní. Oblasti, které změnu písma nepřichytá ani při restartování, toto písmo prostředí nevyu ádá.

- Ověřte, že písma odvozená od služby (například tučný nebo zvětšený text) si při změně velikosti písma prostředí zachovávají jejich velikost a formátování ve vztahu k "normálnímu" textu.

- Ověřte, že neexistují žádné chyby oříznutí kvůli zvětšeným písmům. Písma, která jsou oříznutá, jsou pravděpodobně výsledkem ovládacích prvků s pevnou výškou nebo kontejnerů s pevnou výškou.

### <a name="dialogs"></a>Dialogy

- Ověřte, že název dialogového okna je stejný jako příkaz, který ho spustil.

- Ověřte, že všechny standardní ovládací prvky jsou konzistentní s operačním systémem: barva pozadí je standardní a žádné ovládací prvky by neměly mít speciální styl, který by jinak odpovídal standardním ovládacím prvkům.

- Ověřte, že okraje ve formuláři by měly mít velikost 12 pixelů a měly by vypadat jednotně a konzistentně.

- Ověřte, že se dialogy zobrazují uprostřed v prostředí IDE nebo v okně, které je vytyčilo.

- Pokud je to užitečné, dialogy by měly být možné změnit. U dialogových oknů, která lze změnit, ověřte, že při změně velikosti se musí změnit velikost příslušných ovládacích prvků, zatímco ostatní části dialogového okna zůstanou konstantní.

- Ověřte, že dialogy s možností velikosti zachytává velikost upravenou uživatelem (velikost, umístění, rozšíření ovládacích prvků dialogového okna atd.).

- Ověřte, že v záhlaví není žádná ikona.

- Ověřte, že v záhlaví nejsou žádná tlačítka Minimalizovat a Maximalizovat.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Tlačítka operace dialogového okna (jenom VS Client)

- Ověřte, že jsou tlačítka operací v tomto pořadí: **OK,** **Zrušit,** **Použít.**

- Ověřte, **že tlačítka OK** a **Zrušit** mají standardní velikost: 75 × 23 pixelů.

- Ověřte, **že tlačítka OK** a **Zrušit** mají stejnou velikost bez ohledu na délku řetězce.

- Pokud popisek tlačítka operace vyžaduje, aby tlačítko bylo širší než standardní, ověřte, že odpovídající tlačítko **Zrušit** má stejnou velikost.

- Ověřte, že mezi tlačítky a přidruženými ovládacími prvky je odsazení 6 pixelů.

- Ověřte, **že tlačítka OK** a **Zrušit** nemají klávesová zkratky (přístupové klíče definované podtrženým písmenem).

- Ověřte, že jedno tlačítko (obvykle **OK)** má ve výchozím nastavení fokus.

- Ověření, **že esc** dialogové okno zruší

- Ověřte, **že enter** spustí výchozí tlačítko, pokud fokus není v ovládacím prvku, který zpracovává klávesu Enter.

- Ověřte, **že jsou** tlačítka OK a **Cancel** umístěná v pravém dolním rohu dialogového okna. Ve výjimečných případech je přijatelné, aby se skládaly svisle v pravém horním rohu.

- Ověřte, že se svislá konfigurace používá jenom v případě, že jsou další tlačítka ve vodorovném zarovnání v rámci dialogového okna.

### <a name="control-standards"></a>Standardy řízení

#### <a name="general"></a>Obecné

- Ověřte, že pokud je to možné, existují dobré výchozí hodnoty, které urychlí interakci uživatelů a nasměrují uživatele na bezpečný nebo běžný výsledek.

- Ověřte, že se standardní ovládací prvky chovají stejným způsobem, aby uživatelé věděli, co se stane na základě předchozích zkušeností.

#### <a name="label-controls"></a>Ovládací prvky Popisek

- Ověřte, že každý ovládací prvek má popisek a že každý popisek je vizuálně spárovaný s jeho ovládacím prvku (obecně v rozsahu 4 až 6 pixelů) a že je blíže k odpovídajícímu ovládacímu prvku než k jiným ovládacím prvkům.

- Ověřte, že jsou popisky zarovnané doleva s levým okrajem ovládacího prvku, pokud jsou nad a vodorovně zarovnané na střed, aby směrný plán popisku byl zarovnaný se základními hranami vstupního textu, pokud je umístěný doleva.

- Ověřte, že pokud je vlevo od ovládacího prvku umístěno několik skládaný popisek a vstupní ovládací prvky, popisky jsou vyprázdněny doleva a stejně daleko od okraje dialogového okna, nikdy se nevyprázdní doprava a rovná se vzdálenost od ovládacích prvků. Páry by měly být rovnoměrně distribuovány, pokud nepočítá další mezery k označení seskupení.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Vstupní ovládací prvky (textová pole a pole se seznamem)

- Ověřte, že při použití výchozího písma prostředí má výška zobrazení textových polí, polí se seznamem a tlačítek velikost 23 pixelů.

- Pokud se používá text nápovědy, pomocí služby color ověřte, že je `Environment.ControlEditHintText` barva nastavená na hodnotu .

- Pokud je pole povinné a musí být takto identifikované, ověřte následující:

  - je pozadí nastavené na a `Environment.ControlEditRequiredBackground` popředí je nastavené na . `Environment.ControlEditRequiredHintText`

  - v ovládacím prvku je text nápovědy, který se zobrazuje jako **\<Required> " "**

#### <a name="button-controls"></a>ovládací prvky tlačítek

- Ověřte, že tlačítka mají minimální velikost 75 × 23 pixelů, pokud nezadáte delší text.

- Ověřte, že tlačítka mají levý a pravý okraj 3–5 pixelů a také odsazení obsahu.

- Místo tlačítka **[Procházet...]** (nebo podobné funkce)  je přijatelné použít malé čtvercové tlačítko se třemi tečkami ( ). Pokud použijete , ověřte, že má tlačítko velikost 23 × 23.

- Pokud se v dialogovém okně nachází více než jedno tlačítko **[Procházet...],** ověřte, že se pro všechny používá zkrácená verze (jenom tři tečky **při** použití ).

- Ověřte, že tlačítka se **třemi tečkami (** ) nemají mnemotechnický symbol. Když je fokus na ovládacím prvku vstupu vedle něho, jedna karta by měla přesunout fokus na tlačítko se třemi tečkami.

- Ověřte, že tlačítka, příkazy a odkazy na příkazy, které spouštějí sekundární uživatelské rozhraní, které zachycují více uživatelských vstupů, musí končit třemi tečkami **[...]**.

#### <a name="hyperlinks"></a>Hypertextové odkazy

- Ověřte, že ovládací prvek hypertextový odkaz nikdy při aktivním blikání není červený. Toto je indikátor, že se služba barvy nepoužívá.

- Ověřte, zda jsou použité barvy VS:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Ověřte, zda se hypertextové odkazy zobrazovaly modře bez podtržení, pokud nejsou vloženy do odstavce.

#### <a name="check-boxes"></a>Zaškrtávací políčka

- Pokud má zaškrtávací políčko víceřádkový text, ověřte, zda je pole zarovnáno s prvním řádkem textu, nikoli svisle na střed na všech řádcích.

- Ověřte, že zaškrtávací políčka vždycky označují binární volbu a nedělají uživatele nebo otevřít nová okna nebo stránky.

- Pokud zaškrtávací políčko nabídne možnost související se vstupním ovládacím prvkem, ověřte, že je umístěno vlevo a velmi blízko pod tímto ovládacím prvkem, aby označoval jeho vztah.

- Ověřte, zda se zaškrtávací políčko **nikdy** nepoužívá jako způsob povolení celého obsahu dialogového okna nebo stránky.

#### <a name="group-boxes"></a>Skupinové rámečky

- Ověřte, zda dialogové okno neobsahuje jedno skupinové pole, které obsahuje celý obsah dialogového okna.

- Ověřte, že v každém poli skupiny existují alespoň dva ovládací prvky.

- V dialogovém okně by mělo být více než dvě pole skupin.

- Ověřte, že nejsou k dispozici žádná vnořená pole skupin.

### <a name="icons"></a>Ikony

- Ověřte, že ikony se v tmavém motivu zobrazují správně.

- Ověřte, že jsou všechny ikony založené na základních konceptech.

- Ověřte, zda je každá ikona odlišná, snadno rozpoznatelná a neobsahuje více než dvě koncepce (bez modifikátoru stavu/jazyka).

- Ověřte, že se základní ikona zobrazuje uprostřed v rámci prostoru.

- Ověřte, že jsou všechny ikony čitelné v režimu Vysoký kontrast.

- Ověřte, že se všechny použité barvy rovnají se standardy použití barev.

- Ověřte, že kolem ikon neexistují žádné olemice (ohraničení). (Pokud je přítomen, Hra Halo by měla odpovídat barvě pozadí sousedícího uživatelského rozhraní).

### <a name="touch-enabled-ui"></a>Uživatelské rozhraní s podporou dotykového ovládání

- Ověřte, zda jsou interaktivní ovládací prvky dostatečně velké, aby byly snadno dotykové – minimální velikost **23x23 pixelů** .

- Ověřte, zda jsou nejčastěji používané ovládací prvky velikosti nejméně **40x40 pixelů** .

- Ověřte, že mezi nimi mají interaktivní ovládací prvky aspoň **5 pixelů** .
