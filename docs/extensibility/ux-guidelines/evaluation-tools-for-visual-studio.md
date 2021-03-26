---
title: Nástroje pro vyhodnocení pro Visual Studio | Microsoft Docs
description: Tento kontrolní seznam použijte k vyhodnocení kvality uživatelského prostředí pro vizuální a podrobnosti o interakcích pro nové funkce, které navrhujete pro Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6f23521763e73ef65b9c5a2f17acb54b85b71d63
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089885"
---
# <a name="evaluation-tools-for-visual-studio"></a>Nástroje pro vyhodnocení pro Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Kontrolní seznam Craftsmanship pro Visual Studio
 Tento kontrolní seznam použijte k vyhodnocení kvality uživatelského prostředí pro podrobnosti o vizuálu a interakci.

### <a name="overview"></a>Přehled

- Ověřte, že všechny příkazy mají za následek zpětnou vazbu, která oznamuje uživatelům, že jejich příkazy byly provedeny.

- Ověřte, zda jsou všechny prvky uživatelského rozhraní a ovládací prvky viditelné ve všech motivech a v režimu Vysoký kontrast.

- Ověřte, zda jsou neaktivní a aktivní výběr vždy odlišeny v režimu Standard a Vysoký kontrast.

- Ověřte, zda je fokus vždy viditelný a zřejmý.

### <a name="performance"></a>Výkon

- Ověřte, zda je zobrazen nějaký druh indikátoru zaneprázdněnosti, pokud příkaz trvá déle než jednu sekundu.

- Ověřte, že pokud je příkaz dokončený déle než 10 sekund, zobrazí se explicitní indikátor průběhu, buď zrušení ukončení (upřednostňované), nebo neurčité.

### <a name="ui-text"></a>Text uživatelského rozhraní

- Ověřte, zda jsou všechny popisky tvořené věty nebo nadpisem a zda žádný text není zcela malý.

    ||Správná odpověď.|Chyba|
    |-|-------------|---------------|
    |**Text příkazu (vše)**|Případ věty:<br /><br /> **Název adresáře:**|Název adresáře:|
    |**Text tlačítka (klient)**|Případ nadpisu:<br /><br /> **[Nastavit jako výchozí]**|NASTAVIT JAKO VÝCHOZÍ|
    |**Text tlačítka (online)**|Případ věty:<br /><br /> **[Nastavit jako výchozí]**||

- Ověřte, že všechny popisky kromě záhlaví a tlačítek skupin končí dvojtečkou a předcházejí ovládacímu prvku, se kterým jsou spárovány.

- Ověřte, že tlačítka, příkazy a odkazy na příkazy, které spouštějí uživatelské rozhraní pro zachycení vstupu uživatele, končí třemi tečkami **[...]**.

  Příklady:

  - Tlačítko **[Upřesnit...]** v dialogovém okně.

  - Možnosti příkazu v nabídce nástroje (**nástroje > možnosti**) by neměly získat tři tečky, protože otevření samotného dialogového okna je záměrem příkazu.

- Ověřte, že uživatelské rozhraní neobsahuje žádné zkratky, s výjimkou standardních výrazů. Například není nutné napsaný kód HTML ani TCP/IP, i když OOM (nedostatek paměti) a PII (osobní údaje) by měly.

### <a name="keyboard-access"></a>Přístup ke klávesnici

- Ověřte, že existuje způsob, jak provést jednotlivé úlohy pomocí klávesnice. Obecně se to provádí pomocí přístupu k klávesnicím pro každý ovládací prvek, ale u některých velmi vizuálních oblastí je přijatelné alternativní řešení, jako je například zobrazení kódu.

- Ověřte, zda lze pomocí ovládacích prvků ovládací prvky v logickém pořadí (zleva doprava a shora dolů). I když je to pro většinu ovládacích prvků osvědčeným postupem, ne všechny ovládací prvky vyžadují tento přístup. Ověřte například, že ovládací prvky přepínače jsou ve skupině s jednou zarážku tabulátoru.

- Ověřte, že všechny ovládací prvky mají popisky a že každý popisek má symbolické označení (výjimky zahrnují některé ovládací prvky bez popisku, které mohou následovat po popisku ovládacího prvku na kartě).

- Ověřte, že nejsou v konfliktu žádné symbolické.

### <a name="fonts"></a>Písma

- Ověřte, že se všechna písma (ploška, velikost, barva) používají konzistentně a udržují hierarchii.

- Ověřte, že všechny prvky uživatelského rozhraní používají službu fonting Environment. (Viz [písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Pokud chcete zjistit, jestli se služba používá, můžete přejít na **nástroje > možnosti > písma a barvy**. V rozevíracím seznamu nastavení vyberte možnost písmo prostředí a změňte řez písma na něco odlišně (například Harrington nebo Comic San) a nastavte velikost na 12 bodů. Pak klikněte na OK. Možná budete muset prostředí IDE restartovat, ale většina uživatelského rozhraní se změní hned. Oblasti, které neobsahují změny písma ani při restartování, nepoužívají písmo prostředí.

- Ověřte, že písma, která jsou odvozená ze služby (například tučný nebo zvětšený text), při změně velikosti písma prostředí uchovávají jejich velikost a formátování ve vztahu k "normálnímu" textu.

- Ověřte, že kvůli zvětšeným písmům nedochází k žádným chybám oříznutí. Písma, která jsou oříznuta, jsou zřejmě výsledkem ovládacích prvků pevné výšky nebo pevné výšky.

### <a name="dialogs"></a>Dialogy

- Ověřte, že název dialogového okna je stejný jako příkaz, který ho spustil.

- Ověřte, že všechny standardní ovládací prvky jsou konzistentní s operačním systémem: barva pozadí je standardní a žádné ovládací prvky by neměly mít speciální styl znovu vytvořeného šablony, který se bude zobrazovat jinak než standardní ovládací prvky.

- Ověřte, že okraje v rámci formuláře by měly být 12 pixelů a měly by vypadat jednotně a konzistentní.

- Ověřte, že se dialogová okna zobrazují na střed prostředí IDE nebo v okně, které je vytvořilo.

- Pokud je to užitečné, měly by být dialogy měnitelné. Pro dialogy, jejichž velikost lze změnit, ověřte, že při změně velikosti musí příslušné ovládací prvky změnit velikost, zatímco ostatní části dialogového okna zůstanou konstantní.

- Ověřte, zda dialogová okna umožňující změnu velikosti zachovávají velikost uživatelsky upravené velikosti (velikost, umístění, rozšíření ovládacích prvků dialogu atd.).

- Ověřte, zda záhlaví neobsahuje ikonu.

- Ověřte, že v záhlaví nejsou žádná tlačítka minimalizace a maximalizovat.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Tlačítka operací dialogu (jenom klient VS)

- Ověřte, že jsou tlačítka operace v tomto pořadí: **OK**, **Zrušit**, **použít**.

- Ověřte, že tlačítka **OK** a **Zrušit** mají standardní velikost: 75x23 pixelů.

- Ověřte, že tlačítka **OK** a **Storno** mají stejnou velikost bez ohledu na délku řetězce.

- Pokud tlačítko popisek na operaci vyžaduje, aby tlačítko bylo širší než standard, ověřte, že odpovídající tlačítko **Storno** má stejnou velikost.

- Ověřte, zda je mezi tlačítky a přidruženými ovládacími prvky odsazení 6 pixelů.

- Ověřte, zda tlačítka **OK** a **Storno** nemají klávesové zkratky (přístupové klávesy definované podtrženým písmenem).

- Ověřte, zda je ve výchozím nastavení vybráno jedno tlačítko (obvykle **OK**).

- Ověřte, že **klávesa ESC** zruší dialog.

- Ověřte, že možnost **ENTER** provede výchozí tlačítko, pokud fokus není v ovládacím prvku, který zpracovává zadání.

- Ověřte, zda jsou tlačítka **OK** a **Storno** umístěna v pravém dolním rohu dialogového okna. Ve výjimečných výjimkách je přijatelné, aby byly v pravém horním rohu navrstveny svisle.

- Ověřte, zda se svislá konfigurace používá pouze v případě, že jsou jiná tlačítka v rámci dialogového okna v horizontálním zarovnání.

### <a name="control-standards"></a>Standardy ovládacích prvků

#### <a name="general"></a>Obecné

- Ověřte, že pokud je to možné, existují dobré výchozí hodnoty pro urychlení interakce s uživatelem a přímé nasměrování uživatelů k bezpečnému nebo běžnému výsledku.

- Ověřte, že se standardní ovládací prvky chovají stejným způsobem, aby uživatelé věděli, co se stane na základě předchozích zkušeností.

#### <a name="label-controls"></a>Ovládací prvky popisku

- Ověřte, zda má každý ovládací prvek popisek a zda je každý popisek vizuálně spárován s jeho ovládacím prvkem (obvykle v rozsahu 4-6 pixelů) a je blíže k odpovídajícímu ovládacímu prvku než jiné ovládací prvky.

- Ověřte, že jsou popisky umístěné vlevo a na levém okraji ovládacího prvku, pokud je umístěný nahoře a vodorovně na střed, aby se účaří popisku rovnalo se směrným plánem vstupního textu, pokud je umístěný vlevo.

- Ověřte, zda je na levé straně ovládacího prvku umístěno několik skládaných popisků a vstupních ovládacích prvků, popisky budou zarovnány doleva a stejnou vzdálenost od okraje dialogového okna, nikdy nemusíte naprázdnit pravou a stejnou vzdálenost od ovládacích prvků. Páry by se měly rovnoměrně distribuovat, pokud nepotřebují další mezery k označení seskupení.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Vstupní ovládací prvky (textová pole a pole se seznamem)

- Ověřte, že při použití výchozího písma prostředí je výška displeje pro textová pole, pole se seznamem a tlačítka všechny 23 pixelů.

- Pokud je použit text nápovědy, ověřte, zda je barva nastavena na `Environment.ControlEditHintText` používání barevné služby.

- Pokud pole je povinné pole, které musí být označeno jako, ověřte:

  - zda je pozadí nastaveno na hodnotu `Environment.ControlEditRequiredBackground` a v popředí je nastaveno na `Environment.ControlEditRequiredHintText`

  - , že v ovládacím prvku je text nápovědy, který se zobrazí jako " **\<Required> "**

#### <a name="button-controls"></a>ovládací prvky tlačítek

- Ověřte, že tlačítka mají minimální velikost 75x23 pixelů, pokud nepotřebujete delší text.

- Ověřte, že tlačítka mají levý a pravý okraj 3-5 pixelů a také odsazení obsahu.

- Je přijatelné použít malé čtvercové tlačítko se třemi tečkami **[...]** namísto tlačítka **[Procházet...]** (nebo podobné funkce). Pokud se používá, ověřte, že je toto tlačítko 23x23 velikosti.

- Pokud v dialogovém okně existuje více než jedno tlačítko **[Procházet...]** , pak ověřte, že se pro všechny používá zkrácená verze (jenom se třemi tečkami **[...]**).

- Ověřte, zda tlačítka se třemi tečkami **[...]** nemají symbol. Když je fokus na ovládacím prvku vstupu vedle něho, jedna karta by měla přesunout fokus na tlačítko se třemi tečkami.

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
