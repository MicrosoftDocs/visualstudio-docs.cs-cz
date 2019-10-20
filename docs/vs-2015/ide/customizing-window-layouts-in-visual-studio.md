---
title: Přizpůsobení rozložení oken
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 509ec978815ae57e548188941a8de24c5f36d77e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665835"
---
# <a name="customizing-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete přizpůsobit polohu, velikost a chování Windows pro vytváření rozložení oken, která fungují nejlépe pro různé vývojové pracovní postupy. Když rozložení přizpůsobíte, IDE ho zapamatuje. Například pokud změníte umístění ukotvení **Průzkumník řešení** a potom zavřete Visual Studio, při příštím spuštění, a to i v případě, že pracujete na jiném počítači, **Průzkumník řešení** bude ukotven ve stejném umístění. Můžete také zadat název vlastního rozložení a uložit ho a pak přepínat mezi rozloženími jediným příkazem. Můžete například vytvořit rozložení pro úpravy a další pro ladění a mezi nimi přepínat pomocí příkazu **okna &#124; pro použití nabídky rozložení** okna.

## <a name="kinds-of-windows"></a>Druhy oken

### <a name="tool-and-document-windows"></a>Okna nástrojů a dokumentů
 Rozhraní IDE má dva základní typy oken, okna *nástrojů* a *okna dokumentů*. Okna nástrojů zahrnují Průzkumník řešení, Průzkumník serveru, okno Výstup, Seznam chyb, návrháře, okna ladicího programu a tak dále. Systém dokumentů Windows obsahuje soubory zdrojového kódu, libovolné textové soubory, konfigurační soubory a tak dále. Můžete změnit velikost oken nástrojů a přetáhnout je podle jejich záhlaví. Okna dokumentu lze přetáhnout na jejich kartu. Kliknutím pravým tlačítkem myši na kartu nebo záhlaví nastavíte další možnosti okna.

 V nabídce **okna** se zobrazí možnosti pro ukotvení, plovoucí a skrývání oken v integrovaném vývojovém prostředí (IDE). Kliknutím pravým tlačítkem myši na kartu okna nebo záhlaví zobrazíte další možnosti tohoto konkrétního okna. V jednom okamžiku můžete zobrazit víc než jednu instanci některých oken nástrojů. Můžete například zobrazit více než jedno okno webového prohlížeče a můžete vytvořit další instance některých oken nástrojů výběrem možnosti **nové okno** v nabídce **okno** .

### <a name="preview-tab-document-windows"></a>Karta náhled (okna dokumentu)
 Na kartě Náhled můžete zobrazit soubory v editoru bez nutnosti jejich otevírání. Můžete zobrazit náhled souborů tak, že je vyberete v **Průzkumník řešení**, během ladění, když přejdete do souboru s možností přejít k definici a při procházení výsledků hledání. Soubory náhledu se zobrazí na kartě na pravé straně karty dokumentu. Soubor se otevře pro úpravy, pokud ho upravíte nebo zvolíte **otevřít**.

### <a name="tab-groups"></a>Skupiny karet
 Skupiny karet vám při práci se dvěma nebo více otevřenými dokumenty v integrovaném vývojovém prostředí rozšíří možnost spravovat omezený pracovní prostor. Můžete uspořádat více oken dokumentů a oken nástrojů do skupin svislých a vodorovných karet a náhodně dokumenty z jedné skupiny karet do druhé.

### <a name="split-windows"></a>Rozdělit okna
 Pokud je třeba v dokumentu zobrazit nebo upravit dvě umístění najednou, můžete rozdělit okna. Pokud chcete dokument rozdělit do dvou nezávisle přesouvaných oddílů, klikněte na **rozdělit** v nabídce **okna** . Kliknutím na **Odebrat rozdělení** v nabídce **okno** obnovíte jednoduché zobrazení.

### <a name="toolbars"></a>Panely nástrojů
 Panely nástrojů lze uspořádat přetažením nebo pomocí dialogového okna **přizpůsobit** . Další informace o tom, jak umístit a přizpůsobit panely nástrojů, najdete v tématu [Postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arranging-and-docking-windows"></a>Uspořádání a ukotvení oken
 Okna dokumentů a oken nástrojů lze *ukotvit*, takže mají umístění a velikost v rámci rámce okna IDE nebo plovoucí jako samostatné okno nezávislé na integrovaném vývojovém prostředí (IDE). Okna nástrojů lze ukotvit kdekoli uvnitř rámce IDE; některá okna nástrojů lze ukotvit jako okna s kartami v rámečku editoru. Okna dokumentu lze ukotvit v rámci editoru a v pořadí prvků lze připnout na jejich aktuální pozici. Můžete ukotvit více oken a spojit je dohromady v rámci "vory" nebo vně integrovaného vývojového prostředí (IDE). Okna nástrojů můžou být taky skrytá nebo minimalizovaná.

 Okna můžete uspořádat následujícími způsoby:

- Připnout okna dokumentu vlevo od zásobníku karet.

- Okna ukotvení karet do editačního snímku.

- Ukotvěte okna nástrojů k okraji rámce v integrovaném vývojovém prostředí (IDE).

- Obtékání dokumentu nebo nástrojů v systému Windows nad rámec nebo mimo integrované vývojové prostředí (IDE)

- Skryjte okna nástrojů podél okraje integrovaného vývojového prostředí (IDE).

- Zobrazit okna v různých monitorech.

- Obnovení umístění okna do výchozího rozložení nebo uloženého vlastního rozložení.

  Okna nástrojů a dokumentu lze uspořádat přetažením pomocí příkazů v nabídce **okna** a kliknutím pravým tlačítkem myši na záhlaví okna, které chcete uspořádat.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="docking-windows"></a>Ukotvení oken
 Když kliknete a přetáhnete záhlaví okna nástroje nebo kartu okna dokumentu, zobrazí se kosočtverec s vodítkem. Když se během operace přetažení ukazatel myši nachází nad jednou ze šipek ve čtverečku, zobrazí se šedivá oblast, ve které se zobrazí, kde bude okno ukotveno, pokud nyní uvolníte tlačítko myši.

 Chcete-li přesunout okno ukotvit bez přitahování na místo, stiskněte klávesu CTRL při přetahování okna.

 Chcete-li vrátit okno nástrojů nebo okno dokumentu do svého posledního ukotveného umístění, stiskněte klávesu **CTRL** a dvakrát klikněte na záhlaví nebo kartu okna.

 Následující obrázek znázorňuje vodítko pro okna dokumentu, která lze ukotvit pouze v rámci editačního rámce:

 ![Kosočtverec s oknem dokumentu](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")

 Okna nástrojů lze připravit na jednu stranu snímku v integrovaném vývojovém prostředí nebo v rámci editačního rámce. Při přetahování okna nástroje na jiné místo se zobrazí kosočtverec s vodítkem, který vám pomůže ho snadno znovu ukotvit.

 Kosočtverec s nástroji pro okna nástrojů

 ![Panely nástrojů okna nástroje – kosočtverce](../ide/media/vs10guidediamond.png "VS10GuideDiamond")

 Následující ilustrace ukazuje, Průzkumník řešení je ukotvena v novém umístění, které je zobrazeno modře šedivou oblastí:

 ![Ukotvení Průzkumník řešení na nové pozici](../ide/media/vs2015-dock-diamond.png "VS2015_Dock_diamond")

### <a name="closing-and-auto-hiding-tool-windows"></a>Zavření a automatické skrývání oken nástrojů
 Okno nástroje můžete zavřít kliknutím na X v pravém horním rohu záhlaví. Chcete-li znovu otevřít okno, použijte jeho klávesovou zkratku nebo příkaz nabídky. Nástroj podporuje systém Windows funkci s názvem automaticky skrýt, což způsobí, že okno vyčerpá výstup, když použijete jiné okno. Je-li okno automaticky skryto, jeho název se zobrazí na kartě na okraji integrovaného vývojového prostředí (IDE). Chcete-li znovu použít okno, přejděte na kartu, aby se snímky okna znovu zobrazily.

 ![Automaticky skrývat](../ide/media/vs2015-auto-hide.png "vs2015_auto_hide")

> [!NOTE]
> Chcete-li nastavit, zda má automatické skrývání pracovat v oknech nástrojů individuálně nebo jako ukotvené skupiny, zaškrtněte nebo zrušte zaškrtnutí políčka **automaticky skrýt ovlivní aktivní okna nástrojů pouze** v dialogovém okně **Možnosti** . Další informace naleznete v části [Obecné, prostředí, dialogové okno Možnosti](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
> Okna nástrojů, která mají povolenou možnost automaticky skrývat, mohou být dočasně posunuta do zobrazení, když je okno aktivní. Chcete-li znovu skrýt okno, vyberte položku mimo aktuální okno. Když okno ztratí fokus, snímky se vrátí zpátky z pohledu.

### <a name="specifying-a-monitor"></a>Určení monitoru
 Pokud máte druhý monitor a váš operační systém ho podporuje, můžete zvolit, který monitor zobrazí okno. Můžete dokonce seskupit více oken společně v nabídce "vory" na jiných monitorech.

> [!TIP]
> Můžete vytvořit více instancí **Průzkumník řešení** a přesunout je do jiného monitoru. Klikněte pravým tlačítkem myši na okno a vyberte možnost **nové zobrazení Průzkumník řešení**. Všechna okna můžete vrátit zpět na původní monitor dvojitým kliknutím na klávesovou zkratku CTRL.

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, pojmenování a přepínání mezi rozloženími oken
 Rozhraní IDE můžete vrátit do původního rozložení okna pro kolekci nastavení pomocí příkazu **obnovit rozložení okna** . Při spuštění tohoto příkazu dojde k následujícím akcím:

- Všechna okna se přesunou do jejich výchozích umístění.

- Okna, která jsou zavřena ve výchozím rozložení okna, jsou zavřena.

- Okna, která jsou otevřená ve výchozím rozložení okna, se otevřou.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastních rozložení
 Visual Studio 2015 umožňuje ukládat až 10 vlastních rozložení oken a rychle mezi nimi přepínat. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, která využívají více monitorů s integrovanými i plovoucími okny nástrojů.

 Nejprve vytvořte testovací řešení, které má dva projekty, z nichž každý má jiné optimální rozložení.

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvoření projektu uživatelského rozhraní a přizpůsobení rozložení

1. V dialogovém okně **Nový projekt** vytvořte aplikaci Visual C# WPF Desktop a zavolejte ji, ať už chcete. Předstírat, že se jedná o projekt, na kterém budeme pracovat na uživatelském rozhraní, takže chceme maximalizovat prostor pro okno návrháře a přesunout jiné okna nástrojů ze svých možností.

2. Pokud máte více monitorů, vyžádejte si okno **Průzkumník řešení** a okno **vlastnosti** nad druhý monitor. V jednom systému monitorování zkuste zavřít všechna okna kromě návrháře.

3. Stisknutím **kombinace kláves CTRL + ALT + X** Zobrazte sadu nástrojů. Je-li okno ukotveno, přetáhněte jej tak, aby bylo tam tam, kde byste ho chtěli umístit na oba monitory.

4. Stisknutím klávesy F5 vložte aplikaci Visual Studio do režimu ladění. Upravte umístění oken automatické hodnoty, zásobník volání a výstup ladění výstupu tak, jak chcete. Rozložení, které se chystáte vytvořit, bude platit jak v režimu úprav, tak v režimu ladění.

5. V případě, že vaše rozložení v režimu ladění i v režimu úprav odpovídají vašim způsobem, v hlavní nabídce vyberte možnost **okno > Uložit rozložení okna**. Zavolejte toto rozložení "Návrhář".

     Všimněte si, že nové rozložení má přiřazenou další klávesovou zkratku v seznamu rezervovaných kláves CTRL + ALT + 1... 0.

##### <a name="create-a-database-project-and-layout"></a>Vytvoření databázového projektu a rozložení

1. Přidejte do řešení nový projekt **databáze SQL Server** .

2. V Průzkumník řešení klikněte pravým tlačítkem myši na nový projekt a vyberte možnost **Zobrazit v Průzkumník objektů**. Tím se zobrazí okno **Průzkumník objektů systému SQL Server** , které umožňuje přístup k tabulkám, zobrazením a dalším objektům ve vaší databázi. Můžete buď uvolnit toto okno, nebo ho nechat Dock. Upravte ostatní okna nástrojů tak, jak chcete. Pro přidání realit můžete přidat skutečnou databázi, ale není to pro tento návod nutné.

3. V případě, že vaše rozložení požadujete, v hlavní nabídce vyberte **okno > Uložit rozložení okna**. Volání tohoto rozložení "projekt databáze". (Pro tento projekt se bother s rozložením režimu ladění.)

##### <a name="switch-between-the-layouts"></a>Přepínání mezi rozloženími

1. Chcete-li přepínat mezi rozloženími, použijte klávesové zkratky nebo v hlavní nabídce vyberte možnost **okno > použít rozložení okna**.

     ![Nabídka pro použití rozložení okna](../ide/media/vs2015-applywindowlayout.png "VS2015_ApplyWindowLayout")

     Po použití rozložení uživatelského rozhraní si všimněte, jak je rozložení zachované v režimu úprav i v režimu ladění.

     Pokud máte k dispozici nastavení pro více monitorů v práci a jediný monitorované přenosné počítače v domácnosti, můžete vytvořit rozložení optimalizovaná pro každý počítač.

     Poznámka: Pokud použijete rozložení pro více monitorů v systému s jedním monitorem, budou plovoucí okna, která jste umístili na druhý monitor, skrytá za oknem aplikace Visual Studio. Tato okna můžete přenést do popředí stisknutím kombinace kláves ALT + TAB. Pokud později spustíte Visual Studio s více monitory, můžete obnovit okna na zadané pozice tak, že znovu použijete rozložení.

##### <a name="manage-and-roam-your-layouts"></a>Správa a roaming vašich rozložení

1. Vlastní rozložení můžete odebrat, přejmenovat nebo změnit jejich pořadí, a to tak, že vyberete **okno > spravovat rozložení oken**. Pokud přesunete rozložení, vazba klíče se automaticky upraví tak, aby odrážela nové umístění v seznamu. Vazby nelze jinak upravovat, takže můžete současně uložit maximálně 10 rozložení.

     ![Spravovat rozložení oken](../ide/media/managewindowlayouts.png "ManageWindowLayouts")

     Chcete-li připomenout, k jakému klávesové zkratce je přiřazeno rozložení, vyberte možnost **okno > použít rozložení okna**.

     Tato rozložení automaticky procházejí mezi edicemi sady Visual Studio a také mezi různými instancemi Blendu na samostatných počítačích a z libovolné edice Express na jakékoli jiné společnosti. Rozložení ale neumožňuje roaming napříč Visual Studiem, Blendem a Expressem.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Druhy Windows](../misc/kinds-of-windows.md)|Tento článek popisuje rozdíly mezi okny nástrojů a okny dokumentů v prostředí IDE.|
|[Postupy: uspořádání a ukotvení oken](../misc/how-to-arrange-and-dock-windows.md)|Popisuje, jak lze okna ukotvit, automatický skrývat a zobrazit vedle sebe a také jak rozložení oken obnovit.|
|[Návody: Pohyb v integrovaném vývojovém prostředí](../ide/how-to-move-around-in-the-visual-studio-ide.md)|Popisuje, jak lze cyklicky přepínat mezi otevřenými okny v integrovaném vývojovém prostředí (IDE) v pořadí podle používání. Také popisuje, jak můžete přejít na konkrétní dokumenty.|
|[Přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)|Obsahuje informace o kombinacích nastavení a o tom, jaký vliv mají nastavení na rozložení oken, klávesové zkratky a další prvky v prostředí IDE.|
