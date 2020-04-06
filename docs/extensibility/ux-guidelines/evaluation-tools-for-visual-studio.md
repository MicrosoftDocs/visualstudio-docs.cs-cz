---
title: Nástroje pro hodnocení sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ae5ae2d3be49a797ff1d594aab4517efab53330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698421"
---
# <a name="evaluation-tools-for-visual-studio"></a>Nástroje pro vyhodnocení pro Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Kontrolní seznam zručnosti pro Visual Studio
 Tento kontrolní seznam slouží k vyhodnocení kvality uživatelského prostředí pro vizuální podrobnosti a podrobnosti o interakci.

### <a name="overview"></a>Přehled

- Ověřte, zda všechny příkazy vedou ke zpětné vazbě, která uživatelům říká, že jejich příkazy byly provedeny.

- Ověřte, zda jsou všechny prvky a ovládací prvky uživatelského rozhraní viditelné ve všech motivech a v režimu vysokého kontrastu.

- Ověřte, zda je neaktivní a aktivní výběr vždy rozlišen, a to jak v režimu vysokého kontrastu, tak v režimu vysokého kontrastu.

- Ověřte, zda je fokus vždy viditelný a zřejmý.

### <a name="performance"></a>Výkon

- Ověřte, zda je zobrazen nějaký indikátor "zaneprázdněn", pokud dokončení příkazu trvá déle než jednu sekundu.

- Ověřte, zda dokončení příkazu trvá déle než 10 sekund, zobrazí se výslovný indikátor průběhu, buď určitý (upřednostňovaný) nebo neurčitý.

### <a name="ui-text"></a>Text v uj

- Ověřte, zda jsou všechny popisky velká a velká písmena a zda žádný text není zcela malá písmena.

    ||Správně|Špatně|
    |-|-------------|---------------|
    |**Text příkazu (vše)**|Případ věty:<br /><br /> **Název adresáře:**|Název adresáře:|
    |**Text tlačítka (klient)**|Případ názvu:<br /><br /> **[ Nastavit jako výchozí ]**|NASTAVIT JAKO VÝCHOZÍ|
    |**Text tlačítka (online)**|Případ věty:<br /><br /> **[ Nastavit jako výchozí ]**||

- Ověřte, zda všechny popisky kromě záhlaví skupin a tlačítek končí dvojtečkou a předcházejí ovládacímu prvku, se kterým jsou spárovány.

- Ověřte, zda tlačítka, příkazy a příkazové odkazy, které spouštějí uživatelské rozhraní za účelem zachycení uživatelského vstupu, končí ve třemi tečkách **[...]**.

  Příklady:

  - Tlačítko **[Upřesnit...]** v dialogu.

  - Možnosti příkazů v nabídce Nástroje **(Nástroje > Možnosti)** by neměly dostat tři tečky, protože spuštění samotného dialogu je záměrem příkazu.

- Ověřte, zda ui neobsahuje žádné zkratky, s výjimkou standardních termínů. Například html ani TCP/IP nemusí být vysvětleny, i když OOM (nedostatek paměti) a PII (osobně identifikovatelné informace) by měly.

### <a name="keyboard-access"></a>Přístup z klávesnice

- Ověřte, zda existuje způsob, jak provést každý úkol pomocí klávesnice. Obecně se to provádí prostřednictvím přístupu pomocí klávesnice pro každý ovládací prvek, ale pro některé oblasti s vysokou vizuální, řešení, jako je například jít do zobrazení kódu je přijatelné.

- Ověřte, zda můžete pomocí tabulátoru procházet ovládací prvky v logickém pořadí (zleva doprava a shora dolů). I když je to osvědčený postup pro většinu ovládacích prvků, ne všechny ovládací prvky vyžadují tento přístup. Ověřte například, zda jsou ovládací prvky přepínacích tlačítek ve skupině s jednou zarážkou tabulátoru.

- Ověřte, zda všechny ovládací prvky mají popisky a že každý popisek má mnemotechnické pomůčky (výjimky zahrnují některé neoznačené ovládací prvky, které mohou následovat označený ovládací prvek na kartě).

- Ověřte, zda neexistují žádné mnemotechnické konflikty.

### <a name="fonts"></a>Písma

- Ověřte, zda jsou všechna písma (plocha, velikost, barva) používána konzistentně a udržujte hierarchii.

- Ověřte, zda všechny prvky uživatelského rozhraní používají službu písem prostředí. (Viz [Písma a formátování pro Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Chcete-li zkontrolovat, zda je služba používána, přejděte na **nástroje > možnosti > písma a barvy**. V rozevíracím souboru Nastavení zvolte Písmo prostředí a změňte tvář písma na něco stylisticky odlišného (například Harrington nebo Comic Sans) a nastavte velikost na 12 bodů. Pak klikněte na OK. Možná budete muset restartovat ide, ale většina uI se okamžitě změní. Oblasti, které nezachycují změnu písma ani při restartování, nepoužívají písmo prostředí.

- Ověřte, zda písma, která jsou odvozená od služby (například tučný nebo zvětšený text), si po změně velikosti písma prostředí zachovávají svou velikost a formátování ve vztahu k "normálnímu" textu.

- Ověřte, zda nejsou žádné ořezové chyby z důvodu zvětšených písem. Písma, která jsou oříznuta, jsou pravděpodobně výsledkem ovládacích prvků s pevnou výškou nebo kontejnerů s pevnou výškou.

### <a name="dialogs"></a>Dialogy

- Ověřte, zda je název dialogu stejný jako příkaz, který jej spustil.

- Ověřte, zda jsou všechny standardní ovládací prvky konzistentní s operačním systémem: barva pozadí je standardní a žádné ovládací prvky by neměly mít speciální styl přeložené šablony, který způsobí, že se budou lišit od standardních ovládacích prvků.

- Ověřte, zda by okraje ve formuláři měly mít 12 pixelů a měly by vypadat stejnorodé a konzistentní.

- Ověřte, zda se dialogová okna zobrazují vystředěná v prostředí IDE nebo v okně, které je vytvořilo.

- Pokud je to užitečné, dialogová okna by měla být resizable. U dialogových oken, u kterých lze změnit velikost, ověřte, že po změně velikosti musí příslušné ovládací prvky změnit velikost, zatímco ostatní části dialogového okna zůstanou konstantní.

- Ověřte, zda dialogová okna s nastavitelnou velikostí zůstanou zachována, pokud se uchovávají všechny velikosti upravené uživatelem (velikost, umístění, rozšíření ovládacích prvků dialogových oken a tak dále).

- Ověřte, zda v záhlaví není žádná ikona.

- Ověřte, zda v záhlaví nejsou žádná tlačítka Minimalizovat a Maximalizovat.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Tlačítka pro ovládání dialogu (pouze klient VS)

- Ověřte, zda jsou ovládací tlačítka v tomto pořadí: **OK**, **Cancel**, **Apply**.

- Ověřte, zda mají tlačítka **OK** a **Storno** standardní velikost: 75 x 23 pixelů.

- Ověřte, zda mají tlačítka **OK** a **Storno** stejnou velikost bez ohledu na délku řetězce.

- Pokud popisek na ovládacím tlačítku vyžaduje, aby bylo tlačítko širší než standardní, ověřte, zda má odpovídající tlačítko **Storno** stejnou velikost.

- Ověřte, zda mezi tlačítky a přidruženými ovládacími prvky existuje odsazení o 6 obrazových bodech.

- Ověřte, zda tlačítka **OK** a **Storno** nemají mnemotechnické pomůky (přístupové klávesy definované podtrženým písmenem).

- Ověřte, zda jedno tlačítko (obvykle **OK)** má fokus ve výchozím nastavení.

- Ověření, zda **esc** zruší dialogové okno

- Ověřte, **zda enter** provede výchozí tlačítko, pokud fokus není v ovládacím prvku, který zpracovává Enter.

- Ověřte, zda jsou tlačítka **OK** a **Storna** umístěna v pravém dolním rohu dialogového okna. Ve výjimečných výjimkách je přijatelné, aby byly skládané svisle v pravém horním horním.

- Ověřte, zda je svislá konfigurace použita pouze v případě, že ostatní tlačítka jsou ve vodorovném zarovnání v dialogovém okně.

### <a name="control-standards"></a>Kontrolní standardy

#### <a name="general"></a>Obecné

- Ověřte, pokud je to možné, existují dobré výchozí hodnoty, které urychlují interakci s uživatelem a nasměrují uživatele k bezpečnému nebo běžnému výsledku.

- Ověřte, zda se standardní ovládací prvky chovají stejným způsobem, aby uživatelé věděli, co se stane na základě dřívějších zkušeností.

#### <a name="label-controls"></a>Ovládací prvky popisků

- Ověřte, zda má každý ovládací prvek popisek a zda je každý popisek vizuálně spárován s ovládacím prvkem (obvykle v rozsahu 4 až 6 pixelů) a je blíže k odpovídajícímu ovládacímu prvku než k jiným ovládacím prvkům.

- Ověřte, zda jsou popisky umístěny zarovnané doleva s levým okrajem ovládacího prvku, pokud jsou umístěny nad a vystředěny vodorovně, aby byl účaří popisku zarovnán se základnou vstupního textu, pokud je umístěn doleva.

- Ověřte, zda je několik skládaných ovládacích prvků popisku a vstupu umístěno vlevo od ovládacího prvku, popisky jsou zarovnány doleva a ve stejné vzdálenosti od okraje dialogového okna, nikdy vyprázdnění vpravo a ve stejné vzdálenosti od ovládacích prvků. Dvojice by měly být rovnoměrně rozloženy, pokud nepotřebují další mezery k označení seskupení.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Vstupní ovládací prvky (textová pole a pole se seznamem)

- Ověřte, zda při použití výchozího písma prostředí je výška zobrazení textových polí, polí se seznamem a tlačítek 23 pixelů.

- Pokud je použit text nápovědy, ověřte, zda je barva nastavena na `Environment.ControlEditHintText` použití služby barev.

- Pokud je toto pole povinné pole, které musí být jako takové identifikováno, ověřte:

  - že pozadí je `Environment.ControlEditRequiredBackground` nastaveno na a popředí je nastaveno na`Environment.ControlEditRequiredHintText`

  - že je v ovládacím prvku text nápovědy, který se zobrazí jako **\<"Povinné>"**

#### <a name="button-controls"></a>ovládací prvky tlačítek

- Ověřte, zda jsou tlačítka o minimální velikosti 75 x 23 pixelů, pokud nejsou vstříc delšímu textu.

- Ověřte, zda mají tlačítka levý a pravý okraj 3 až 5 pixelů a také odsazení obsahu.

- Je přijatelné použít malé čtvercové tlačítko s pouze třemi tečkami **[...]** na něm místo tlačítka **[Procházet...]** (nebo podobné funkce). Pokud je použito, ověřte, zda má tlačítko velikost 23 x 23.

- Pokud je v dialogu více než jedno tlačítko **[Procházet...],** ověřte, zda je zkrácená verze (pouze tři tečky **[...]**) použita pro všechny.

- Ověřte, zda tlačítka se třemi tečkami **[...]** nemají mnemotechnické pomůcky. Když je fokus na vstupním ovládacím prvku vedle něj, jedna karta by se měla přesunout fokus na tlačítko se třemi tečkami.

- Ověřte, zda tlačítka, příkazy a příkazové odkazy, které spouštějí sekundární uživatelské rozhraní, které zachycuje více uživatelských vstupů, musí končit třemi tečkami **[...]**.

#### <a name="hyperlinks"></a>Hypertextové odkazy

- Ověřte, zda ovládací prvek hypertextového odkazu nikdy nebliká červeně, když je aktivní. Jedná se o indikátor, že služba barev není používána

- Ověřte, zda jsou použité barvy VS:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Ověřte, zda hypertextové odkazy vypadají modře bez podtržení, pokud nejsou vloženy do odstavce.

#### <a name="check-boxes"></a>Políčka

- Pokud má zaškrtávací políčko víceřádkový text, ověřte, zda je pole zarovnáno s prvním řádkem textu, který není vystředěn svisle napříč všemi řádky.

- Ověřte, zda zaškrtávací políčka vždy označují binární volbu a neprocházet uživatele mj.

- Pokud zaškrtávací políčko představuje možnost související se vstupním ovládacím prvkem, ověřte, zda je umístěn zarovnané vlevo a velmi blízko pod tímto ovládacím prvkem k označení jeho vztahu.

- Ověřte, zda se zaškrtávací políčko **nikdy nepoužívá** jako prostředek k povolení celého obsahu dialogu nebo stránky.

#### <a name="group-boxes"></a>Skupinová pole

- Ověřte, zda dialogové okno neobsahuje v něm jediné skupinové pole, které obsahuje celý obsah dialogového okna.

- Ověřte, zda jsou v každém skupinovém rámečku alespoň dva ovládací prvky.

- Zřídka by měl být více než dvě skupinová pole v dialogu.

- Ověřte, zda neexistují žádná vnořená pole skupiny.

### <a name="icons"></a>Ikony

- Ověřte, zda se ikony zobrazují správně obráceně, když je ve tmě.

- Ověřte, zda jsou všechny ikony založeny na základních konceptech.

- Ověřte, zda je každá ikona odlišná, snadno rozpoznatelná a neobsahuje více než dva koncepty (bez modifikátoru stavu/jazyka).

- Ověřte, zda se základní ikona zobrazuje vystředěná v prostoru.

- Ověřte, zda jsou všechny ikony v režimu vysokého kontrastu čitelné.

- Ověřte, zda jsou všechny použité barvy v souladu se standardy používání barev.

- Ověřte, zda kolem ikon nejsou žádné aureoly (ohraničení). (Pokud je k dispozici, aureoly by měly odpovídat barvě pozadí sousedního uI).

### <a name="touch-enabled-ui"></a>Dotykové rozhraní

- Ověřte, zda jsou interaktivní ovládací prvky dostatečně velké, aby byly snadno dotknutelné – minimálně **23 x 23 pixelů**

- Ověřte, zda jsou nejčastěji používané ovládací prvky o **rozměrech nejméně 40 x 40 pixelů.**

- Ověřte, zda interaktivní ovládací prvky mají mezi sebou alespoň **5 pixelů mezer**
