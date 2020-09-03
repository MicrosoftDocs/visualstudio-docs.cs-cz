---
title: Přizpůsobení rozložení oken
ms.date: 07/31/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2135183a474e29229d941bbd47af8d6abc263e49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87546066"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v aplikaci Visual Studio

V aplikaci Visual Studio můžete přizpůsobit polohu, velikost a chování Windows pro vytváření rozložení oken, která fungují nejlépe pro různé vývojové pracovní postupy. Když rozložení přizpůsobíte, IDE ho zapamatuje. Například pokud změníte umístění ukotvení **Průzkumník řešení** a pak zavřete Visual Studio, při příštím otevření sady Visual Studio, a to i v případě, že pracujete na jiném počítači, **Průzkumník řešení** bude ukotveno ve stejném umístění.

Můžete také pojmenovat a uložit vlastní rozložení a pak přepínat mezi rozloženími jediným příkazem. Můžete například vytvořit rozložení pro úpravy a rozložení pro ladění a mezi nimi přepínat pomocí příkazu **okna**pro  >  **použití nabídky rozložení** okna.

## <a name="tool-and-document-windows"></a>Okna nástrojů a dokumentů

Rozhraní IDE má dva základní typy oken, okna *nástrojů* a *okna dokumentů*. Okna nástrojů zahrnují **Průzkumník řešení**, **Průzkumník serveru**, **okno výstup**, **Seznam chyb**, návrháře, okna ladicího programu a tak dále. Systém dokumentů Windows obsahuje soubory zdrojového kódu, libovolné textové soubory, konfigurační soubory a tak dále. Můžete změnit velikost oken nástrojů a přetáhnout je podle jejich záhlaví. Okna dokumentu lze přetáhnout na jejich kartu. Klikněte pravým tlačítkem myši na kartu nebo záhlaví a nastavte další možnosti okna.

V nabídce **okna** se zobrazí možnosti pro ukotvení, plovoucí a skrývání oken v integrovaném vývojovém prostředí (IDE). Kliknutím pravým tlačítkem myši na kartu okna nebo záhlaví zobrazíte další možnosti tohoto konkrétního okna. V jednom okamžiku můžete zobrazit víc než jednu instanci některých oken nástrojů. Můžete například zobrazit více než jedno okno webového prohlížeče a můžete vytvořit další instance některých oken nástrojů výběrem možnosti **nové okno** v nabídce **okno** .

### <a name="split-windows"></a>Rozdělit okna

Pokud je třeba v dokumentu zobrazit nebo upravit dvě umístění najednou, můžete rozdělit okna. Pokud chcete dokument rozdělit do dvou nezávisle přesouvaných oddílů, klikněte na **rozdělit** v nabídce **okna** . Kliknutím na **Odebrat rozdělení** v nabídce **okno** obnovíte jednoduché zobrazení.

### <a name="tabs"></a>Karty

Pomocí karet můžete uspořádat rozložení několika různými způsoby. Můžete například zobrazit náhled souboru v editoru, aniž byste soubor otevřeli, můžete seskupovat své karty a další.

#### <a name="preview-tab-document-windows"></a>Karta náhled (okna dokumentu)

Na kartě **Náhled** můžete zobrazit soubory v editoru bez nutnosti jejich otevírání. Můžete zobrazit náhled souborů tak, že je vyberete v **Průzkumník řešení**, během ladění, když přejdete do souboru s možností **Přejít k definici**a při procházení výsledků hledání. Soubory náhledu se zobrazí na kartě na pravé straně karty dokumentu. Soubor se otevře pro úpravy, pokud ho upravíte, nebo klikněte na  **otevřít**.

::: moniker range="vs-2019"

#### <a name="vertical-document-tabs"></a>Svislé karty dokumentu

**[Novinka ve verzi 16,4](/visualstudio/releases/2019/release-notes-v16.4/)**: Přidali jsme jednu z hlavních žádostí o funkce, [vertikálních karet dokumentů](https://developercommunity.visualstudio.com/idea/467369/vertical-group-tab.html)ve verzi Visual Studio 2019 verze 16,4. Teď můžete spravovat karty dokumentu ve svislém seznamu na levé nebo pravé straně editoru.

Svislé karty dokumentu můžete použít následujícími způsoby:

- **Tools**  >  **Options**  >  V řádku nabídek vyberte možnosti nástrojů karta**prostředí**  >  **a okna** . Pak z ovládacího prvku **rozložení karty sada** zvolte v rozevíracím seznamu buď **nahoře**, **vlevo**nebo **vpravo** .

- Klikněte pravým tlačítkem myši na kartu, zvolte možnost **nastavit rozložení karty**a pak zvolte možnost **vlevo** nebo **vpravo**. (Pokud chcete tabulátory vrátit na výchozí pozici, vyberte **nahoře**.)

    :::image type="content" source="./media/vs-2019/vertical-tabs.gif" alt-text="Animace, která zobrazuje svislé karty dokumentu v akci":::

::: moniker-end

#### <a name="tab-groups"></a>Skupiny karet

Skupiny karet vám při práci se dvěma nebo více otevřenými dokumenty v integrovaném vývojovém prostředí rozšíří možnost spravovat omezený pracovní prostor. Můžete uspořádat více oken dokumentů a oken nástrojů do skupin svislých a vodorovných karet a náhodně dokumenty z jedné skupiny karet do druhé.

### <a name="toolbars"></a>Panely nástrojů

Panely nástrojů lze uspořádat přetažením do míst, kde chcete, nebo pomocí dialogového okna **přizpůsobit** . Další informace o tom, jak umístit a přizpůsobit panely nástrojů, najdete v tématu [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Uspořádat a ukotvit okna

Okno dokumentu nebo nástroj může být *ukotveno*, takže má pozici a velikost v rámci rámce okna IDE. Můžete ho také umístit jako samostatné plovoucí okno, které je mimo rozhraní IDE.

Můžete ukotvit okno nástrojů kdekoli uvnitř rámce IDE. Můžete také ukotvit některá okna nástrojů jako okna s kartami v rámci editoru. A můžete ukotvit okna dokumentu v rámci editoru a můžete je připnout na aktuální pozici v pořadí prvků.

Můžete také ukotvit více oken, *aby je bylo* možné spojit dohromady v rámci nebo vně integrovaného vývojového prostředí (IDE). Okna nástrojů můžou být taky skrytá nebo minimalizovaná.

Okna můžete uspořádat následujícími způsoby:

- Připnout okna dokumentu vlevo od zásobníku karet.

- Okna ukotvení karet do editačního snímku.

- Ukotvěte okna nástrojů k okraji rámce v integrovaném vývojovém prostředí (IDE).

- Obtékání dokumentu nebo nástrojů v systému Windows nad rámec nebo mimo integrované vývojové prostředí (IDE)

- Skryjte okna nástrojů podél okraje integrovaného vývojového prostředí (IDE).

- Zobrazit okna v různých monitorech.

- Obnovení umístění okna do výchozího rozložení nebo uloženého vlastního rozložení.

Pro uspořádání nástrojů a oken dokumentů můžete umístit kurzor do záhlaví okna a pak ho přetáhnout na místo, kde chcete. Případně můžete kliknout pravým tlačítkem myši na záhlaví okna a použít jeho kontextovou nabídku, nebo můžete použít příkazy v nabídce **okna** .

### <a name="dock-windows"></a>Ukotvit okna

Když kliknete a přetáhnete záhlaví okna nástroje nebo kartu okna dokumentu, zobrazí se kosočtverec s vodítkem. Když se během operace přetažení ukazatel myši nachází nad jednou ze šipek ve čtverečku, zobrazí se šedivá oblast, ve které se zobrazí, kde bude okno ukotveno, pokud nyní uvolníte tlačítko myši.

Chcete-li přesunout okno ukotvit bez jeho přitahování na místo, stiskněte klávesu **CTRL** při přetahování okna.

Chcete-li vrátit okno nástrojů nebo okno dokumentu do svého posledního ukotveného umístění, stiskněte klávesu **CTRL** a dvakrát klikněte na záhlaví nebo kartu okna.

Následující obrázek znázorňuje vodítko pro okna dokumentu, která lze ukotvit pouze v rámci editačního rámce:

![Kosočtverec s oknem dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna nástrojů lze připravit na jednu stranu snímku v integrovaném vývojovém prostředí nebo v rámci editačního rámce. Po přetahování okna nástroje na jiné místo se zobrazí kosočtverec s vodítkem, který vám pomůže okno snadno ukotvit.

![Panely nástrojů okna nástroje – kosočtverce](../ide/media/vs10guidediamond.png)

Následující obrázek ukazuje **Průzkumník řešení** ukotven v novém umístění, které je ohraničeno modrou šedou oblastí:

![Ukotvení Průzkumník řešení na nové pozici](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zavřít a automaticky skrýt okna nástrojů

Okno nástroje můžete zavřít kliknutím na **X** v pravém horním rohu záhlaví. Chcete-li znovu otevřít okno, použijte jeho klávesovou zkratku nebo příkaz nabídky. Nástroj podporuje systém Windows funkci s názvem *automaticky skrýt*, což způsobí, že okno vyčerpá výstup, když použijete jiné okno. Je-li okno automaticky skryto, jeho název se zobrazí na kartě na okraji integrovaného vývojového prostředí (IDE). Chcete-li znovu použít okno, přejděte na kartu, aby se snímky okna znovu zobrazily.

![Automaticky skrývat](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Chcete-li nastavit, zda má automatické skrývání pracovat v oknech nástrojů individuálně nebo jako ukotvené skupiny, zaškrtněte nebo zrušte zaškrtnutí políčka **automaticky skrýt ovlivní aktivní okna nástrojů pouze** v dialogovém okně **Možnosti** . Další informace naleznete v části [Obecné, prostředí, dialogové okno Možnosti](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna nástrojů, která mají povolenou možnost automaticky skrývat, mohou být dočasně posunuta do zobrazení, když je okno aktivní. Chcete-li znovu skrýt okno, vyberte položku mimo aktuální okno. Když okno ztratí fokus, snímky se vrátí zpátky z pohledu.

### <a name="use-a-second-monitor"></a>Použít druhý monitor

Pokud máte druhý monitor a váš operační systém ho podporuje, můžete zvolit, který monitor zobrazí okno. Můžete dokonce seskupit více oken *v počítačích na* jiných monitorech.

> [!TIP]
> Můžete vytvořit více instancí **Průzkumník řešení** a přesunout je do jiného monitoru. Klikněte pravým tlačítkem myši na okno a vyberte možnost **nové zobrazení Průzkumník řešení**. Všechna okna můžete vrátit zpět na původní monitor dvojitým kliknutím na klávesovou **zkratku CTRL** .

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, pojmenování a přepínání mezi rozloženími oken

Rozhraní IDE můžete vrátit do původního rozložení okna pro kolekci nastavení pomocí příkazu **obnovit rozložení okna** . Při spuštění tohoto příkazu dojde k následujícím akcím:

- Všechna okna se přesunou do jejich výchozích umístění.

- Okna, která jsou zavřena ve výchozím rozložení okna, jsou zavřena.

- Okna, která jsou otevřená ve výchozím rozložení okna, se otevřou.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastních rozložení

Visual Studio umožňuje ukládat až 10 vlastních rozložení oken a rychle mezi nimi přepínat. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, která využívají více monitorů s integrovanými i plovoucími okny nástrojů.

Nejprve vytvořte testovací řešení, které má dva projekty, z nichž každý má jiné optimální rozložení.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvoření projektu uživatelského rozhraní a přizpůsobení rozložení

1. Vytvoří nový projekt **aplikace WPF** v C#. Představte si, že v tomto projektu budete vyvíjet uživatelské rozhraní. Chcete maximalizovat prostor pro okno návrháře a jiné okna nástrojů přesunout ze své.

2. Pokud máte více monitorů, přenesete okno **Průzkumník řešení** a okno **vlastnosti** do druhého monitoru. V jednom systému monitorování zkuste zavřít všechna okna kromě návrháře.

3. Stisknutím **kombinace kláves CTRL** + **ALT** + **X** zobrazte okno **panelu nástrojů** . Je-li okno ukotveno, přetáhněte jej tak, aby bylo na místě, kde byste ho chtěli umístit jinam.

4. Stisknutím klávesy **F5** vložte aplikaci Visual Studio do režimu ladění. Upravte umístění oken **Automatické**hodnoty, **zásobník volání**a **výstup ladění výstupu** tak, jak chcete. Rozložení, které se chystáte vytvořit, bude platit jak v režimu úprav, tak v režimu ladění.

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
