---
title: Přizpůsobení rozložení oken
ms.date: 01/23/2017
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
ms.openlocfilehash: c1963c76b67eaedea4cdf013739c112275ecffb2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596707"
---
# <a name="customize-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v aplikaci Visual Studio

V aplikaci Visual Studio můžete přizpůsobit polohu, velikost a chování Windows pro vytváření rozložení oken, která fungují nejlépe pro různé vývojové pracovní postupy. Při přizpůsobování rozložení prostředí IDE pamatuje ho. Například pokud změníte umístění ukotvení **Průzkumník řešení** a pak zavřete Visual Studio, při příštím otevření sady Visual Studio, a to i v případě, že pracujete na jiném počítači, **Průzkumník řešení** bude ukotveno ve stejném umístění.

Můžete také pojmenovat a uložit vlastní rozložení a pak přepínat mezi rozloženími jediným příkazem. Můžete například vytvořit rozložení pro úpravy a rozložení pro ladění a přepínat mezi nimi pomocí **okna** > použít příkaz nabídky **rozložení okna** .

## <a name="kinds-of-windows"></a>Druhy Windows

### <a name="tool-and-document-windows"></a>Okna nástrojů a dokumentů

Integrované vývojové prostředí má dva základní typy, *okna nástrojů* a *dokumentu windows*. Okna nástrojů zahrnují **Průzkumník řešení**, **Průzkumník serveru**, **okno výstup**, **Seznam chyb**, návrháře, okna ladicího programu a tak dále. Okna dokumentů obsahují soubory zdrojového kódu, libovolných textových souborů, konfigurační soubory a tak dále. Okna nástrojů můžete velikost a přetáhnout pomocí jejich záhlaví. Okna dokumentu lze přetáhnout na jejich kartu. Kliknutím pravým tlačítkem myši na kartu nebo záhlaví nastavíte další možnosti okna.

**Okno** nabídce se zobrazí možnosti pro ukotvení plovoucí desetinné čárky a skrytí oken v integrovaném vývojovém prostředí. Klikněte pravým tlačítkem na řádku okna kartu nebo název zobrazíte další možnosti pro toto konkrétní okno. Najednou můžete zobrazit více než jeden výskyt určitých oken nástrojů. Například můžete zobrazit více než jeden okno webového prohlížeče a můžete vytvořit další instance některých oknech nástrojů výběrem **nové okno** na **okno** nabídky.

### <a name="preview-tab-document-windows"></a>Kartu náhledu (okna dokumentu)

Na kartě **Náhled** můžete zobrazit soubory v editoru bez nutnosti jejich otevírání. Můžete zobrazit náhled souborů tak, že je vyberete v **Průzkumník řešení**, během ladění, když přejdete do souboru s možností **Přejít k definici**a při procházení výsledků hledání. Soubory ve verzi Preview se zobrazí na kartě na pravé straně zásobník karet dokumentů. Soubor se otevře pro úpravy, pokud ho upravíte, nebo klikněte na **otevřít**.

### <a name="tab-groups"></a>Skupiny karet

Skupiny karet vám při práci se dvěma nebo více otevřenými dokumenty v integrovaném vývojovém prostředí rozšíří možnost spravovat omezený pracovní prostor. Můžete uspořádat více oken dokumentů a oken nástrojů do skupin svislých a vodorovných karet a náhodně dokumenty z jedné skupiny karet do druhé.

### <a name="split-windows"></a>Rozdělit okna

Až budete mít k zobrazení nebo úpravám dvě místa současně v dokumentu, můžete rozdělit systém windows. Pokud chcete rozdělit dokumentu na dva oddíly nezávisle na sobě posouvání, klikněte na tlačítko **rozdělení** na **okno** nabídky. Klikněte na tlačítko **odebrat rozdělení** na **okno** nabídky k obnovení jednoho zobrazení.

### <a name="toolbars"></a>Panely nástrojů

Panely nástrojů lze uspořádat přetažením nebo pomocí **vlastní** dialogové okno. Další informace o tom, jak umístit a přizpůsobit panely nástrojů, najdete v tématu [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arrange-and-dock-windows"></a>Uspořádat a ukotvit okna

Okno dokumentu nebo nástroj může být *ukotveno*, takže má pozici a velikost v rámci rámce okna IDE nebo plovoucí jako samostatné okno nezávislé na rozhraní IDE. Panely nástrojů lze ukotvit kdekoli v rámci integrovaného vývojového prostředí; Některé panely nástrojů lze ukotvit jako oken s kartami v rámci editoru. Okna dokumentu lze ukotvit v rámci editoru a je možné připnout svoje aktuální umístění v pořadí karet. Můžete ukotvit více oken, *abyste je mohli* spojit dohromady v rámci nebo vně integrovaného vývojového prostředí (IDE). Nástroje systému windows můžete také skrytý nebo minimalizovat.

Uspořádat okna následujícími způsoby:

- Připnete také okna windows vlevo na kartu.

- Okna dokování karet pro úpravy snímků.

- Ukotvení oken nástrojů k okraji rámečku v rozhraní IDE.

- Plovoucí dokument nebo nástroje okna přes nebo mimo rozhraní IDE.

- Skryjte panel nástrojů k okraji rozhraní IDE.

- Zobrazení oken na různých monitorech.

- Obnovení umístění okna do výchozího rozložení nebo uložené vlastní rozložení.

Uspořádejte okna nástrojů a oken dokumentů přetažením pomocí příkazů v nabídce **okna** nebo kliknutím pravým tlačítkem myši na záhlaví okna k uspořádání.

### <a name="dock-windows"></a>Ukotvit okna

Když klikněte a přetáhněte záhlaví panelu nástrojů nebo okna dokumentu na kartě, zobrazí se kosočtverce vodítka. Během operace přetažení když ukazatel myši je nad jednu ze šipek v kosočtverec, na vystínovanou oblast se zobrazí, který ukazuje, kde Ukotvit okno Pokud nyní uvolněte tlačítko myši.

Chcete-li přesunout okno ukotvit bez jeho přitahování na místo, stiskněte klávesu **CTRL** při přetahování okna.

Chcete-li vrátit okno nástrojů nebo okno dokumentu do svého posledního ukotveného umístění, stiskněte klávesu **CTRL** a dvakrát klikněte na záhlaví nebo kartu okna.

Směrová růžice okna dokumentu, které může být ukotven pouze v editačním rámci naleznete na následujícím obrázku:

![Kosočtverec s oknem dokumentu](../ide/media/documentwindowguidediamonds.png)

Okna nástrojů můžete připevnit na jedné straně rámu v integrovaném vývojovém prostředí nebo v editačním rámci. Po přetahování okna nástroje na jiné místo se zobrazí kosočtverec s vodítkem, který vám pomůže okno snadno ukotvit.

![Panely nástrojů okna nástroje – kosočtverce](../ide/media/vs10guidediamond.png)

Následující obrázek ukazuje **Průzkumník řešení** ukotven v novém umístění, které je ohraničeno modrou šedou oblastí:

![Ukotvení Průzkumník řešení na nové pozici](../ide/media/vs2015_dock_diamond.png)

### <a name="close-and-auto-hide-tool-windows"></a>Zavřít a automaticky skrýt okna nástrojů

Okno nástroje můžete zavřít kliknutím na **X** v pravém horním rohu záhlaví. Chcete-li znovu otevřít okno, použijte jeho klávesovou zkratku nebo příkaz nabídky. Nástroj podporuje systém Windows funkci s názvem *automaticky skrýt*, což způsobí, že okno vyčerpá výstup, když použijete jiné okno. Je-li okno automaticky skryto, jeho název se zobrazí na kartě na okraji integrovaného vývojového prostředí (IDE). Pokud chcete znovu použít okno, přejděte na kartu tak, aby se okno zasunulo zpět do zobrazení.

![Automaticky skrývat](../ide/media/vs2015_auto_hide.png)

> [!NOTE]
> Chcete-li nastavit, zda má automatické skrývání pracovat v oknech nástrojů individuálně nebo jako ukotvené skupiny, zaškrtněte nebo zrušte zaškrtnutí políčka **automaticky skrýt ovlivní aktivní okna nástrojů pouze** v dialogovém okně **Možnosti** . Další informace naleznete v části [Obecné, prostředí, dialogové okno Možnosti](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna nástrojů, která mají povolenou možnost automaticky skrývat, mohou být dočasně posunuta do zobrazení, když je okno aktivní. Chcete-li skrýt okno znovu, vyberte položku mimo aktuální okno. Pokud okno ztratí fokus, karta se zasune zpět mimo zobrazení.

### <a name="specifying-a-second-monitor"></a>Určení druhého monitoru

Pokud máte druhý monitor a váš operační systém jej podporuje, můžete zvolit, který monitor má zobrazit okno. Můžete dokonce seskupit více oken *v počítačích na* jiných monitorech.

> [!TIP]
> Můžete vytvořit více instancí **Průzkumníka řešení** a přesunout na jiný monitor. Klikněte pravým tlačítkem myši okno a zvolte **nové zobrazení Průzkumníka řešení**. Všechna okna můžete vrátit zpět na původní monitor dvojitým kliknutím na klávesovou **zkratku CTRL** .

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, název a přepínání rozložení oken

Rozhraní IDE může vrátit do původního rozložení okna pro kolekci nastavení pomocí **resetovat rozložení okna** příkazu. Když spustíte tento příkaz, provedou se tyto akce:

- Všechna okna jsou přesunuta do jejich výchozích poloh.

- Windows, které jsou uzavřeny ve výchozím rozložení okna, jsou zavřena.

- Windows, které jsou otevřeny v výchozí rozložení okna jsou otevřené.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastní rozložení

Visual Studio umožňuje ukládat až 10 vlastních rozložení oken a rychle mezi nimi přepínat. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, které budou využívat více monitorů s obou oken nástrojů ukotvených a s plovoucí desetinnou čárkou.

Nejprve vytvořte řešení testu, který má dva projekty, každá má jiné optimální rozložení.

#### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvořte projekt uživatelského rozhraní a přizpůsobení rozložení

1. Vytvořte nový C# projekt **aplikace WPF** . Představte si, že v tomto projektu budete vyvíjet uživatelské rozhraní. Chcete maximalizovat prostor pro okno návrháře a jiné okna nástrojů přesunout ze své.

2. Pokud máte více monitorů, o přijetí změn **Průzkumníka řešení** okno a **vlastnosti** okna přes druhý monitor. V systému jednoho monitoru zavřete všechna okna s výjimkou návrháře.

3. Stisknutím **kombinace kláves Ctrl**+**ALT**+**X** zobrazte okno **panelu nástrojů** . Je-li okno ukotveno, přetáhněte jej tak, aby bylo na místě, kde byste ho chtěli umístit jinam.

4. Stisknutím klávesy **F5** vložte aplikaci Visual Studio do režimu ladění. Upravte umístění oken **Automatické**hodnoty, **zásobník volání**a **výstup ladění výstupu** tak, jak chcete. Rozložení, které se chystáte vytvořit, bude platit jak v režimu úprav, tak v režimu ladění.

5. V případě, že vaše rozložení v režimu ladění i v režimu úprav, jak chcete, vyberte možnost **okno** > **Uložit rozložení okna**. Zavolejte toto rozložení "Návrhář".

     Všimněte si, že nové rozložení má přiřazenou další klávesovou zkratku v seznamu rezervovaných **kláves Ctrl**+**ALT**+**1... 0**.

#### <a name="create-a-database-project-and-layout"></a>Vytvořte projekt databáze a rozložení

1. Přidat nový **databázi systému SQL Server** projektu do řešení.

2. V **Průzkumník řešení** klikněte pravým tlačítkem myši na nový projekt a vyberte možnost **Zobrazit v Průzkumník objektů**. Zobrazí se **Průzkumník objektů systému SQL Server** okna, která umožňuje přístup k tabulkám, zobrazení a dalších objektů v databázi. Můžete buď uvolnění toto okno nebo necháte ukotven. Jiné nástroje systému windows upravte požadovaným způsobem. Pro přidání realit můžete přidat skutečnou databázi, ale není to pro tento návod nutné.

3. V případě, že vaše rozložení požadujete, v hlavní nabídce vyberte **okno** > **Uložit rozložení okna**. Volání tohoto rozložení "projekt databáze". (Pro tento projekt se bother s rozložením režimu ladění.)

#### <a name="switch-between-the-layouts"></a>Přepínání rozložení

Chcete-li přepínat mezi rozloženími, použijte klávesové zkratky nebo v hlavní nabídce vyberte možnost **okno** > **použít rozložení okna**.

![Nabídka pro použití rozložení okna](../ide/media/vs2015_applywindowlayout.png)

Po použití rozložení uživatelského rozhraní, Všimněte si, jak je rozložení zachována v režimu úprav i v režimu ladění.

Pokud máte více monitorování nastavení v práci a jednoho monitoru přenosného počítače v domácnostech, můžete vytvořit rozložení, která jsou optimalizovaná pro každý počítač.

> [!NOTE]
> Pokud použijete rozložení pro více monitorů v systému s jedním monitorem, budou plovoucí okna, která jste umístili na druhý monitor, skrytá za oknem aplikace Visual Studio. Tato okna můžete přenést do popředí stisknutím **kombinace kláves ALT + TAB**. Pokud později spustíte Visual Studio s více monitory, můžete obnovit okna na zadané pozice tak, že znovu použijete rozložení.

#### <a name="manage-and-roam-your-layouts"></a>Spravovat a zpřístupnit vaše rozložení

Vlastní rozložení můžete odebrat, přejmenovat nebo změnit jejich pořadí, a to tak, že vyberete **okno** > **spravovat rozložení oken**. Pokud přesunete rozložení, vazba klíče se automaticky upraví tak, aby odrážely novou pozici v seznamu. Vazby nemůže být jinak upravit, a tak může ukládat maximálně 10 rozložení v čase.

![Spravovat rozložení oken](../ide/media/managewindowlayouts.png)

Chcete-li připomenout, k jakému klávesové zkratce je přiřazeno rozložení, vyberte možnost **okno** > **použít rozložení okna**.

Tyto rozloženích automaticky přecházet mezi edicemi Visual Studio a také mezi instancemi Blendu na samostatných počítačích a z libovolnou edici Express do jiné organizace Express. Rozložení však není přenášet mezi Visual Studio, Blend a Express.

## <a name="see-also"></a>Viz také:

- [Postupy: pohyb v integrovaném vývojovém prostředí](../ide/how-to-move-around-in-the-visual-studio-ide.md)
