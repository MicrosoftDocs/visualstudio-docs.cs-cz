---
title: Přizpůsobení rozložení oken
description: Zjistěte, jak přizpůsobit charakteristiky, které se ve Windows projevují, a vytvářet rozložení, která fungují nejlépe pro různé pracovní postupy vývoje.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: conceptual
f1_keywords:
- vs.windows
- vs.environment
helpviewer_keywords:
- windows [Visual Studio], managing
- custom window configurations
- layout [Visual Studio], window management
- document windows [Visual Studio]
- interface modes
- AutoHide windows
- MDI, window interface modes
- multiple monitors
- Tabbed Document mode
- debug mode
- custom layouts
ms.assetid: 7517ff13-76de-4ecf-9c1b-eb9b7ff4d718
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: be11db364d0505833e722d3db308b41a18ccbb9d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308126"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v Visual Studio

V Visual Studio můžete přizpůsobit umístění, velikost a chování oken a vytvořit rozložení oken, která fungují nejlépe pro různé vývojové pracovní postupy. Když přizpůsobíte rozložení, integrované vývojové prostředí si ho zapamatuje. Pokud například změníte umístění ukotvení  Průzkumník řešení a pak Visual Studio zavřete, při příštím otevření Visual Studio, i když pracujete na jiném počítači, bude **Průzkumník řešení** ukotvený ve stejném umístění.

Můžete také jedním příkazem nastavit název a uložit vlastní rozložení a přepínat mezi rozloženími. Můžete například vytvořit rozložení pro úpravy a rozložení pro ladění a přepínat mezi nimi pomocí příkazu nabídky **Použít** rozložení  >   okna.

## <a name="tool-and-document-windows"></a>Okna nástrojů a dokumentů

Integrované vývojové prostředí (IDE) má dva základní typy oken, *okna nástrojů* a *okna dokumentů.* Mezi okna **nástrojů patří Průzkumník řešení,** **Průzkumník serveru,** **okno Výstup,** **Seznam chyb,** návrháři, okna ladicího programu atd. Okna dokumentů obsahují soubory zdrojového kódu, libovolné textové soubory, konfigurační soubory atd. Velikost panelů nástrojů můžete změnit a přetáhnout podle záhlaví. Okna dokumentů je možné přetáhnout na jejich kartu. Klikněte pravým tlačítkem na kartu nebo záhlaví a nastavte další možnosti v okně.

V **nabídce Okna** se zobrazují možnosti ukotvení, plovoucí desetinné čárky a skrytí oken v integrovaném vývojovém prostředí. Kliknutím pravým tlačítkem na kartu okna nebo záhlaví zobrazíte další možnosti pro toto konkrétní okno. Najednou můžete zobrazit více než jednu instanci určitých oken nástrojů. Můžete například zobrazit více než jedno okno webového prohlížeče a výběrem možnosti Nové  okno v nabídce **Okno** můžete vytvořit další instance některých panelů nástrojů.

### <a name="split-windows"></a>Rozdělit okna

Pokud v dokumentu potřebujete zobrazit nebo upravit dvě umístění najednou, můžete rozdělit okna. Pokud chcete dokument rozdělit do dvou samostatných sekcí posouvání, klikněte **v nabídce** **Okno na Rozdělit.** Kliknutím **na Odebrat** rozdělení v nabídce **Okno** obnovíte jedno zobrazení.

### <a name="tabs"></a>Karty

Pomocí karet můžete rozložení uspořádat několika různými způsoby. Můžete například zobrazit náhled souboru v editoru bez otevření souboru, seskupit karty a další.

#### <a name="preview-tab-document-windows"></a>Karta Náhled (okna dokumentů)

Na **kartě Náhled** můžete zobrazit soubory v editoru, aniž byste je otevřeli. Náhled souborů můžete zobrazit tak, že je zvolíte v **Průzkumník řešení**, během ladění při krokování do souborů, pomocí možnosti Přejít k definici a při procházení výsledků hledání. Soubory náhledu se zobrazí na kartě na pravé straně karty dokumentu. Soubor se otevře pro úpravy, pokud ho upravíte, nebo zvolte **Otevřít.**

::: moniker range=">=vs-2019"

#### <a name="vertical-document-tabs"></a>Svislé karty dokumentů

**[Novinka ve verzi 16.4:](/visualstudio/releases/2019/release-notes-v16.4/)** Do verze Visual Studio 2019 verze 16.4 jsme přidali jednu z nejlepších žádostí o [funkce,](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html)vertikální karty dokumentů. Karty dokumentů teď můžete spravovat ve svislém seznamu na levé nebo pravé straně editoru.

Svislé karty dokumentů můžete použít následujícími způsoby:

- Na **řádku**  >  **nabídek**  >    >  zvolte Nástroje Možnosti Karty prostředí a **Okna.** Potom v ovládacím **prvku Nastavit rozložení** karet zvolte  **z** rozevíracího seznamu buď **Nahoře,** Vlevo nebo Vpravo.

- Klikněte pravým tlačítkem na kartu, zvolte **Nastavit rozložení karet** a pak zvolte buď **Vlevo,** nebo **Vpravo.** (Pokud chcete karty vrátit na výchozí pozici, zvolte **Nahoře**.)

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animace znázorňuje svislé karty dokumentů v akci":::

::: moniker-end

#### <a name="tab-groups"></a>Skupiny karet

Skupiny karet rozšiřují vaši schopnost spravovat omezený pracovní prostor, když v integrovaném vývojovém prostředí pracujete se dvěma nebo více otevřenými dokumenty. Můžete uspořádat několik oken dokumentů a panelů nástrojů do vertikálních nebo vodorovných skupin karet a promíchat dokumenty z jedné skupiny karet do druhé.

### <a name="toolbars"></a>Panely nástrojů

Panely nástrojů můžete uspořádat přetažením na místo, kde je chcete, nebo pomocí **dialogového okna** Přizpůsobit. Další informace o umístění a přizpůsobení panelů nástrojů najdete v tématu [Postupy: Přizpůsobení nabídek a panelů nástrojů.](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)

## <a name="arrange-and-dock-windows"></a>Uspořádání a ukotvení oken

Okno dokumentu nebo panel nástrojů lze *ukotvit* tak, aby měl pozici a velikost v rámci rámce okna integrovaného vývojového prostředí. Můžete ho také umístit jako samostatné plovoucí okno, které je mimo integrované vývojové prostředí (IDE).

Okno nástroje můžete ukotvit kdekoli uvnitř rámce integrovaného vývojového prostředí( IDE). Některá okna nástrojů můžete také ukotvit jako okna s kartami v rámci editoru. Můžete také ukotvit okna dokumentů v rámci rámce editoru a připnout je na aktuální pozici v pořadí ovládacích panelů.

Můžete také ukotvit více oken, aby bylo možné s plovoucí desetinnou čárkou najednou *pracovat* nad nebo vně integrovaného vývojového prostředí. Okna nástrojů mohou být také skrytá nebo minimalizovaná.

Okna můžete uspořádat následujícími způsoby:

- Připněte okna dokumentu nalevo od karty.

- Ukotvení oken pomocí tabulátoru k editačnímu rámci

- Ukotvení panelů nástrojů k okraji rámce v integrovaném vývojovém prostředí

- Plovoucí okno dokumentu nebo nástrojů v integrovaném vývojovém prostředí (IDE) nebo mimo toto integrované vývojové prostředí (IDE)

- Skryjte okna nástrojů na okraji integrovaného vývojového prostředí.

- Zobrazení oken na různých monitorech

- Resetujte umístění okna na výchozí rozložení nebo do uloženého vlastního rozložení.

Pokud chcete uspořádat okna nástrojů a dokumentů, umístěte kurzor na záhlaví okna a přetáhněte ho tam, kde chcete. Případně můžete kliknout pravým tlačítkem na záhlaví okna a použít jeho místní nabídku, nebo můžete použít příkazy v **nabídce** Okno.

### <a name="dock-windows"></a>Ukotvení oken

Když kliknete a přetáhnete záhlaví panelu nástrojů nebo kartu okna dokumentu, zobrazí se kosočtverec s vodítkem. Když je během operace přetažení ukazatel myši nad jednou ze šipek v kosočtverci, zobrazí se vystínovaná oblast, která ukazuje, kde se okno při uvolnění tlačítka myši ukotví.

Pokud chcete přesunout ukotvené okno bez přichycení na místo, stiskněte při přetažení okna klávesu **Ctrl.**

Pokud chcete okno nástroje nebo okno dokumentu vrátit na jeho nejnovější ukotvené umístění, stiskněte klávesu **Ctrl** a poklikejte na záhlaví nebo kartu okna.

Následující obrázek znázorňuje kosočtverec pro okna dokumentů, která je možné ukotvit pouze v rámci editačních rámců:

![Kosočtverec s průvodcem oknem dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna nástrojů je možné v integrovaném vývojovém prostředí (IDE) nebo v rámci editačního rámce připevnit na jednu stranu rámce. Při přetažení okna nástroje do jiného umístění se zobrazí kosočtverec, který vám pomůže toto okno snadno uvolnit.

![Kosočtverce s průvodcem v okně nástrojů](../ide/media/vs10guidediamond.png)

Následující obrázek **znázorňuje Průzkumník řešení** ukotvené v novém umístění, které je vymezené modrou vystínovanou oblastí:

![Ukotvení Průzkumník řešení na nové pozici](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zavření a automatické skrytí oken nástrojů

Okno nástroje můžete zavřít kliknutím na **X** v pravém horním rohu záhlaví. Pokud chcete okno znovu otevřít, použijte jeho klávesovou zkratku nebo příkaz nabídky. Okna nástrojů podporují funkci s názvem *automatické* skrytí, která způsobí, že se okno při použití jiného okna posune mimo cestu. Při automatickém zobrazení okna se jeho název zobrazí na kartě na okraji integrovaného vývojového prostředí( IDE). Pokud chcete toto okno znovu použít, přejděte na kartu, aby se okno vrátilo zpět do zobrazení.

![Automatické skrytí](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Pokud chcete nastavit, jestli automatické skrytí funguje v  oknech nástrojů jednotlivě nebo jako ukotvené skupiny, vyberte nebo zrušte zaškrtnutí tlačítka Automaticky skrýt, které ovlivní aktivní okna nástrojů pouze v **dialogovém okně** Možnosti. Další informace najdete v tématu [Obecné, Prostředí, dialogové okno Možnosti.](../ide/reference/general-environment-options-dialog-box.md)

> [!NOTE]
> Okna nástrojů s povoleným automatickým skrytí se mohou dočasně přepnout do zobrazení, když je okno fokusu. Pokud chcete okno znovu skrýt, vyberte položku mimo aktuální okno. Když okno ztratí fokus, posune se zpět ze zobrazení.

### <a name="use-a-second-monitor"></a>Použití druhého monitorování

Pokud máte druhé monitorování a váš operační systém ho podporuje, můžete zvolit, které monitorování zobrazí okno. Na jiných monitorech můžete dokonce *seskupit více* oken dohromady.

> [!TIP]
> Můžete vytvořit více instancí Průzkumník řešení **a** přesunout je do jiného monitorování. Klikněte pravým tlačítkem na okno a zvolte **Nový Průzkumník řešení Zobrazení**. Všechna okna můžete vrátit zpět do původního monitoru tak, že při výběru klávesy **Ctrl** poklikáte.

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, název a přepínání mezi rozloženími oken

Integrované vývojové prostředí (IDE) můžete vrátit do původního rozložení okna pro kolekci nastavení pomocí **příkazu Resetovat rozložení** okna. Když spustíte tento příkaz, dojde k následujícím akcím:

- Všechna okna se přesunou na výchozí pozice.

- Okna zavřená ve výchozím rozložení okna se zavře.

- Otevřou se okna, která jsou otevřená ve výchozím rozložení okna.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastních rozložení

Visual Studio umožňuje ukládat až 10 vlastních rozložení oken a rychle mezi nimi přepínat. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, která využívají více monitorů s integrovanými i plovoucími okny nástrojů.

Nejprve vytvořte testovací řešení, které má dva projekty, z nichž každý má jiné optimální rozložení.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvoření projektu uživatelského rozhraní a přizpůsobení rozložení

::: moniker range="vs-2017"

1. Vytvoří nový projekt **aplikace WPF** v C#. Představte si, že v tomto projektu budete vyvíjet uživatelské rozhraní. Chcete maximalizovat prostor pro okno návrháře a jiné okna nástrojů přesunout ze své.

::: moniker-end

::: moniker range=">=vs-2019"

1. Vytvořte nový projekt **aplikace WPF** v jazyce C#. Představte si, že v tomto projektu budete vyvíjet uživatelské rozhraní. Chcete maximalizovat prostor pro okno návrháře a jiné okna nástrojů přesunout ze své.

::: moniker-end

2. Pokud máte více monitorů, přenesete okno **Průzkumník řešení** a okno **vlastnosti** do druhého monitoru. V jednom systému monitorování zkuste zavřít všechna okna kromě návrháře.

3. Stisknutím **kombinace kláves CTRL** + **ALT** + **X** zobrazte okno **panelu nástrojů** . Je-li okno ukotveno, přetáhněte jej tak, aby bylo na místě, kde byste ho chtěli umístit jinam.

4. Stisknutím klávesy **F5** vložte aplikaci Visual Studio do režimu ladění. Upravte umístění oken **Automatické** hodnoty, **zásobník volání** a **výstup ladění výstupu** tak, jak chcete. Rozložení, které se chystáte vytvořit, bude platit jak v režimu úprav, tak v režimu ladění.

5. V případě, že vaše rozložení v režimu ladění i v režimu úprav, jak chcete, vyberte možnost **okno**  >  **Uložit rozložení okna**. Zavolejte toto rozložení "Návrhář".

     Všimněte si, že nové rozložení má přiřazenou další klávesovou zkratku v seznamu rezervovaných **kláves CTRL** + **ALT** + **1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Vytvoření databázového projektu a rozložení

1. Přidejte do řešení nový projekt **databáze SQL Server** .

2. V **Průzkumník řešení** klikněte pravým tlačítkem myši na nový projekt a vyberte možnost **Zobrazit v Průzkumník objektů**. Tím se zobrazí okno **Průzkumník objektů systému SQL Server** , které umožňuje přístup k tabulkám, zobrazením a dalším objektům ve vaší databázi. Můžete buď uvolnit toto okno, nebo ho nechat Dock. Upravte ostatní okna nástrojů tak, jak chcete. Pro přidání realit můžete přidat skutečnou databázi, ale není to pro tento návod nutné.

3. Když vaše rozložení požadujete, v hlavní nabídce vyberte **okno**  >  **Uložit rozložení okna**. Volání tohoto rozložení "projekt databáze". (Pro tento projekt se bother s rozložením režimu ladění.)

#### <a name="switch-between-the-layouts"></a>Přepínání mezi rozloženími

Chcete-li přepínat mezi rozloženími, použijte klávesové zkratky nebo v hlavní nabídce vyberte možnost **okno**  >  **použít rozložení okna**.

![Nabídka pro použití rozložení okna](../ide/media/vs2015_applywindowlayout.png)

Po použití rozložení uživatelského rozhraní si všimněte, jak je rozložení zachované v režimu úprav i v režimu ladění.

Pokud máte k dispozici nastavení pro více monitorů v práci a jediný monitorované přenosné počítače v domácnosti, můžete vytvořit rozložení optimalizovaná pro každý počítač.

> [!NOTE]
> Pokud použijete rozložení pro více monitorů v systému s jedním monitorem, budou plovoucí okna, která jste umístili na druhý monitor, skrytá za oknem aplikace Visual Studio. Tato okna můžete přenést do popředí stisknutím **kombinace kláves ALT + TAB**. Pokud později spustíte Visual Studio s více monitory, můžete obnovit okna na zadané pozice tak, že znovu použijete rozložení.

#### <a name="manage-and-roam-your-layouts"></a>Správa a roaming vašich rozložení

Vlastní rozložení můžete odebrat, přejmenovat nebo změnit jejich pořadí, a to volbou **okna**  >  **spravovat rozložení oken**. Pokud přesunete rozložení, vazba klíče se automaticky upraví tak, aby odrážela nové umístění v seznamu. Vazby nelze jinak upravovat, takže můžete současně uložit maximálně 10 rozložení.

![Spravovat rozložení oken](../ide/media/managewindowlayouts.png)

Chcete-li připomenout, k jakému klávesové zkratce je přiřazeno rozložení, vyberte možnost **okno**  >  **použít rozložení okna**.

Tato rozložení automaticky procházejí mezi edicemi sady Visual Studio a také mezi různými instancemi Blendu na samostatných počítačích a z libovolné edice Express na jakékoli jiné společnosti. Rozložení ale neumožňuje roaming napříč Visual Studiem, Blendem a Expressem.

## <a name="see-also"></a>Viz také

- [Postupy: pohyb v integrovaném vývojovém prostředí](../ide/how-to-move-around-in-the-visual-studio-ide.md)
