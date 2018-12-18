---
title: Přizpůsobení rozložení oken
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e37adb6296a805b8a0fd06196e7ccf1acf5bc32e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057558"
---
# <a name="customizing-window-layouts-in-visual-studio"></a>Přizpůsobení rozložení oken v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V sadě Visual Studio můžete přizpůsobit pozici, velikost a chování systému windows vytvořit rozložení oken, které nejlépe vyhovují různých vývojových pracovních postupů. Při přizpůsobování rozložení prostředí IDE pamatuje ho. Například, pokud změníte umístění ukotvení **Průzkumníka řešení** a pak zavřete sadu Visual Studio, při příštím spuštění, i v případě, že pracujete v jiném počítači, **Průzkumníka řešení** bude ukotven na stejném místě. Můžete také pojmenujte vlastní rozložení a uložte ho a potom přepínejte mezi rozložení pomocí jediného příkazu. Například můžete vytvořit zobrazení pro úpravy a druhý pro ladění a přepínat mezi nimi technologií **okno &#124; použít rozložení oken** příkazu nabídky.

## <a name="kinds-of-windows"></a>Druhy oken

### <a name="tool-and-document-windows"></a>Nástroje a dokument Windows
 Integrované vývojové prostředí má dva základní typy, *okna nástrojů* a *dokumentu windows*. Nástroje systému windows zahrnují Průzkumníku řešení, Průzkumníka serveru, okno výstup, seznam chyb, návrháři, okna ladicího programu a tak dále. Okna dokumentů obsahují soubory zdrojového kódu, libovolných textových souborů, konfigurační soubory a tak dále. Okna nástrojů můžete velikost a přetáhnout pomocí jejich záhlaví. Okna dokumentu můžete přetáhnout podle jejich karty. Klikněte pravým tlačítkem na panelu kartu nebo záhlaví a nastavit další možnosti v okně.

 **Okno** nabídce se zobrazí možnosti pro ukotvení plovoucí desetinné čárky a skrytí oken v integrovaném vývojovém prostředí. Klikněte pravým tlačítkem na řádku okna kartu nebo název zobrazíte další možnosti pro toto konkrétní okno. Najednou můžete zobrazit více než jeden výskyt určitých oken nástrojů. Například můžete zobrazit více než jeden okno webového prohlížeče a můžete vytvořit další instance některých oknech nástrojů výběrem **nové okno** na **okno** nabídky.

### <a name="preview-tab-document-windows"></a>Kartu náhledu (okna dokumentu)
 Na kartě Preview můžete zobrazit soubory v editoru bez jejich otevírání. Soubory můžete zobrazit náhled výběrem v **Průzkumníka řešení**, během ladění při krokování s vnořením souborů a přejít k definici a když při procházení výsledek hledání. Soubory ve verzi Preview se zobrazí na kartě na pravé straně zásobník karet dokumentů. Soubor se otevře pro úpravy, pokud ho upravit nebo zvolte **otevřít**.

### <a name="tab-groups"></a>Skupiny karet
 Skupiny karet rozšířit vaši schopnost spravovat pracovní prostor omezený, když pracujete s dvěma nebo více otevřených dokumentů v integrovaném vývojovém prostředí. Více oken dokumentů a okna nástrojů můžete uspořádat do svislý nebo vodorovný skupin karet a shuffle dokumenty z jedné skupiny karet do jiného.

### <a name="split-windows"></a>Rozdělení Windows
 Až budete mít k zobrazení nebo úpravám dvě místa současně v dokumentu, můžete rozdělit systém windows. Pokud chcete rozdělit dokumentu na dva oddíly nezávisle na sobě posouvání, klikněte na tlačítko **rozdělení** na **okno** nabídky. Klikněte na tlačítko **odebrat rozdělení** na **okno** nabídky k obnovení jednoho zobrazení.

### <a name="toolbars"></a>Panely nástrojů
 Panely nástrojů lze uspořádat přetažením nebo pomocí **vlastní** dialogové okno. Další informace o tom, jak umístit a přizpůsobení panelů nástrojů naleznete v tématu [postupy: přizpůsobení nabídek a panelů nástrojů](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="arranging-and-docking-windows"></a>Rozvržení a dokování Windows
 Obě dokumentu systému windows a nástroj windows může být *ukotvených*, tak, aby byly na pozici a velikost v rámci okna rámce IDE nebo s plovoucí desetinnou čárkou jako samostatné okno nezávisle na integrovaném vývojovém prostředí. Panely nástrojů lze ukotvit kdekoli v rámci integrovaného vývojového prostředí; Některé panely nástrojů lze ukotvit jako oken s kartami v rámci editoru. Okna dokumentu lze ukotvit v rámci editoru a je možné připnout svoje aktuální umístění v pořadí karet. Můžete ukotvit více oken uvolnění společně "přilepením" přes nebo mimo rozhraní IDE. Nástroje systému windows můžete také skrytý nebo minimalizovat.

 Uspořádat okna následujícími způsoby:

- Připnete také okna windows vlevo na kartu.

- Okna dokování karet pro úpravy snímků.

- Ukotvení oken nástrojů k okraji rámečku v rozhraní IDE.

- Plovoucí dokument nebo nástroje okna přes nebo mimo rozhraní IDE.

- Skryjte panel nástrojů k okraji rozhraní IDE.

- Zobrazení oken na různých monitorech.

- Obnovení umístění okna do výchozího rozložení nebo uložené vlastní rozložení.

  Okna nástroje dokument lze uspořádat přetažením pomocí příkazů na **okno** nabídky a kliknutím pravým tlačítkem myši záhlaví okna, které uspořádáváte.

> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="docking-windows"></a>Ukotvení Windows
 Když klikněte a přetáhněte záhlaví panelu nástrojů nebo okna dokumentu na kartě, zobrazí se kosočtverce vodítka. Během operace přetažení když ukazatel myši je nad jednu ze šipek v kosočtverec, na vystínovanou oblast se zobrazí, který ukazuje, kde Ukotvit okno Pokud nyní uvolněte tlačítko myši.

 Chcete-li přesunout ukotvitelné okno bez přitahování na místě, zvolte klávesu Ctrl při přetahování okna.

 Chcete-li vrátit okno nástroje nebo okno dokumentu na poslední ukotvené umístění, stiskněte **CTRL** při poklepání na záhlaví okna nebo karty v okně.

 Směrová růžice okna dokumentu, které může být ukotven pouze v editačním rámci naleznete na následujícím obrázku:

 ![Kosočtverce vodítka okna dokumentu](../ide/media/documentwindowguidediamonds.png "Documentwindowguidediamonds")

 Okna nástrojů můžete připevnit na jedné straně rámu v integrovaném vývojovém prostředí nebo v editačním rámci. Kosočtverce vodítka se zobrazí při přetažení okna nástrojů do jiného umístění, aby vám usnadnily dokování okna.

 Směrová růžice v oknech nástrojů

 ![Nástroj pro okno Průvodce diamanty](../ide/media/vs10guidediamond.png "VS10GuideDiamond")

 Průzkumník řešení je ukotven na nové umístění, které se zobrazí modré vystínovanou oblast na následujícím obrázku:

 ![Průzkumník řešení na nové pozici ukotvení](../ide/media/vs2015-dock-diamond.png "VS2015_Dock_diamond")

### <a name="closing-and-auto-hiding-tool-windows"></a>Uzavření a automatického skrytí oken nástrojů
 Kliknutím na křížek v pravém horním rohu záhlaví; můžete zavřít okno nástroje znovu otevřete okno, příkazem jeho klávesnice nebo v místní nabídce. Okna nástrojů podporují funkci s názvem automaticky skrýt, což způsobí, že okno snímku odjede stranou stranou při použití jiného okna. Když je okno skryto automaticky, zobrazí se jeho název na kartě na okraji rozhraní IDE. Pokud chcete znovu použít okno, přejděte na kartu tak, aby se okno zasunulo zpět do zobrazení.

 ![Automaticky skrýt](../ide/media/vs2015-auto-hide.png "vs2015_auto_hide")

> [!NOTE]
>  Chcete-li nastavit, zda možnost automaticky skrýt pracuje v nástroji windows samostatně nebo jako ukotvené skupiny, zaškrtněte nebo zrušte **automaticky skrýt ovlivní pouze aktivní okna nástrojů** v **možnosti** dialogové okno. Další informace najdete v tématu [Obecné, prostředí, dialogové okno Možnosti](../ide/reference/general-environment-options-dialog-box.md).

> [!NOTE]
>  Okna nástrojů, které mají povolenou funkci automaticky skrýt se mohou dočasně ukázat ve zobrazení, pokud má okno fokus. Chcete-li skrýt okno znovu, vyberte položku mimo aktuální okno. Pokud okno ztratí fokus, karta se zasune zpět mimo zobrazení.

### <a name="specifying-a-monitor"></a>Určení monitoru
 Pokud máte druhý monitor a váš operační systém jej podporuje, můžete zvolit, který monitor má zobrazit okno. Můžete dokonce seskupit více oken v "do"řad na jiných monitorech.

> [!TIP]
>  Můžete vytvořit více instancí **Průzkumníka řešení** a přesunout na jiný monitor. Klikněte pravým tlačítkem myši okno a zvolte **nové zobrazení Průzkumníka řešení**. Všechna okna můžete vrátit zpět na původní monitor poklikáním při výběru klávesy Ctrl.

### <a name="reset-name-and-switch-between-window-layouts"></a>Resetování, název a přepínání rozložení oken
 Rozhraní IDE může vrátit do původního rozložení okna pro kolekci nastavení pomocí **resetovat rozložení okna** příkazu. Když spustíte tento příkaz, provedou se tyto akce:

-   Všechna okna jsou přesunuta do jejich výchozích poloh.

-   Windows, které jsou uzavřeny ve výchozím rozložení okna, jsou zavřena.

-   Windows, které jsou otevřeny v výchozí rozložení okna jsou otevřené.

### <a name="create-and-save-custom-layouts"></a>Vytvoření a uložení vlastní rozložení
 Visual Studio 2015 můžete uložit až 10 vlastní rozložení oken a rychle přepínat mezi nimi. Následující kroky ukazují, jak vytvořit, uložit, vyvolat a spravovat vlastní rozložení, které budou využívat více monitorů s obou oken nástrojů ukotvených a s plovoucí desetinnou čárkou.

 Nejprve vytvořte řešení testu, který má dva projekty, každá má jiné optimální rozložení.

##### <a name="create-a-ui-project-and-customize-the-layout"></a>Vytvořte projekt uživatelského rozhraní a přizpůsobení rozložení

1.  V **nový projekt** dialogové okno, vytvořte Visual C# WPF aplikace klasické pracovní plochy a volat libovolně. Předstírají, že je projekt kde budeme pracovat v uživatelském rozhraní, proto jsme pro maximalizaci místa pro okna návrháře a eliminuje přesunout jiné nástroje systému windows.

2.  Pokud máte více monitorů, o přijetí změn **Průzkumníka řešení** okno a **vlastnosti** okna přes druhý monitor. V systému jednoho monitoru zavřete všechna okna s výjimkou návrháře.

3.  Stisknutím klávesy **Ctrl + Alt + X** zobrazíte panelu nástrojů. Pokud je toto okno ukotveno, přetáhněte ho tak, aby ho čísel s plovoucí čárkou někde, kde byste chtěli, umístěte na buď monitoru.

4.  Stisknutím klávesy F5 do sady Visual Studio v režimu ladění. Upravte polohu příkazu automatické hodnoty, zásobník volání a výstup ladění systému windows, jak je potřebujete. Rozložení, který se chystáte vytvořit, platit pro úpravy režimu i režimu ladění.

5.  Když vašich rozložení v režimu ladění i v režimu úprav jsou, jak chcete, z hlavní nabídky zvolte **okna > Uložit rozložení oken**. Volání toto rozložení "Designer".

     Všimněte si, že vaše nové rozložení je přiřazena další klávesovou zkratku ze seznamu vyhrazené klávesy Ctrl + Alt + 1... 0.

##### <a name="create-a-database-project-and-layout"></a>Vytvořte projekt databáze a rozložení

1.  Přidat nový **databázi systému SQL Server** projektu do řešení.

2.  Klikněte pravým tlačítkem na nový projekt v Průzkumníku řešení a zvolte **zobrazení v Průzkumníku objektů**. Zobrazí se **Průzkumník objektů systému SQL Server** okna, která umožňuje přístup k tabulkám, zobrazení a dalších objektů v databázi. Můžete buď uvolnění toto okno nebo necháte ukotven. Jiné nástroje systému windows upravte požadovaným způsobem. Pro přidání realitu můžete přidat databázi aplikace skutečný, ale není nutné v tomto návodu.

3.  Když rozložení je, jak chcete, z hlavní nabídky zvolte **okna > Uložit rozložení oken**. Volání toto rozložení "DB projektu." (Budeme se zabývat rozložení režimu ladění pro tento projekt.)

##### <a name="switch-between-the-layouts"></a>Přepínání rozložení

1.  Přepínat mezi rozložením, pomocí klávesové zkratky nebo v hlavní nabídce zvolte **okna > použít rozložení oken**.

     ![Použít rozložení nabídka okna](../ide/media/vs2015-applywindowlayout.png "VS2015_ApplyWindowLayout")

     Po použití rozložení uživatelského rozhraní, Všimněte si, jak je rozložení zachována v režimu úprav i v režimu ladění.

     Pokud máte více monitorování nastavení v práci a jednoho monitoru přenosného počítače v domácnostech, můžete vytvořit rozložení, která jsou optimalizovaná pro každý počítač.

     Poznámka: Pokud použijete rozložení více monitorů jedním monitorování systému, okna s plovoucí desetinnou čárkou, které se umístí na druhém monitoru budou nyní být skrytá pod možností okno sady Visual Studio. Tato okna je možné přenést do popředí stisknutím kombinace kláves Alt + Tab. Při dalším otevření sady Visual Studio s více monitory, můžete obnovit systému windows na zadané pozici rozložení použitím znovu.

##### <a name="manage-and-roam-your-layouts"></a>Spravovat a zpřístupnit vaše rozložení

1.  Můžete odebrat, přejmenovat nebo změnit pořadí vlastních rozložení výběrem **okna > Spravovat rozložení oken**. Pokud přesunete rozložení, vazba klíče se automaticky upraví tak, aby odrážely novou pozici v seznamu. Vazby nemůže být jinak upravit, a tak může ukládat maximálně 10 rozložení v čase.

     ![Spravovat rozložení oken](../ide/media/managewindowlayouts.png "ManageWindowLayouts")

     Abyste nezapomněli, které klávesnice zástupce je přiřazený k rozložení, zvolte **okna > použít rozložení oken**.

     Tyto rozloženích automaticky přecházet mezi edicemi Visual Studio a také mezi instancemi Blendu na samostatných počítačích a z libovolnou edici Express do jiné organizace Express. Rozložení však není přenášet mezi Visual Studio, Blend a Express.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Druhy Windows](../misc/kinds-of-windows.md)|Tento článek popisuje rozdíly mezi okny nástrojů a okny dokumentů v prostředí IDE.|
|[Postupy: rozvržení a dokování Windows](../misc/how-to-arrange-and-dock-windows.md)|Popisuje, jak lze okna ukotvit, automatický skrývat a zobrazit vedle sebe a také jak rozložení oken obnovit.|
|[Návody: Pohyb v integrovaném vývojovém prostředí](../ide/how-to-move-around-in-the-visual-studio-ide.md)|Popisuje, jak lze cyklicky přepínat mezi otevřenými okny v integrovaném vývojovém prostředí (IDE) v pořadí podle používání. Také popisuje, jak můžete přejít na konkrétní dokumenty.|
|[Přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)|Obsahuje informace o kombinacích nastavení a o tom, jaký vliv mají nastavení na rozložení oken, klávesové zkratky a další prvky v prostředí IDE.|
