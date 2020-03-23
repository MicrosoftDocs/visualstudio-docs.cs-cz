---
title: Vytvořit doplněk pro prohlížeč výsledků testů výkonu webu
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6da2686a5a68325101e7161a51a8144e7ef42b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589081"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Postup: Vytvoření doplňku pro prohlížeč výsledků testů výkonnosti webu

Uživatelské prostředí pro prohlížeč **výsledků testů výkonu webu** můžete rozšířit pomocí následujících oborů názvů:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Dále je třeba přidat odkaz na dll Služby LoadTestPackage, která je umístěna ve složce *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<verze>\Enterprise\Common7\IDE\PrivateAssemblies.*

Chcete-li rozšířit uživatelské rozhraní **prohlížeče výsledků webového testu výkonu,** je nutné vytvořit doplněk sady Visual Studio a uživatelský ovládací prvek. Následující postupy vysvětlují, jak vytvořit doplněk, uživatelský ovládací prvek a jak implementovat třídy nezbytné k rozšíření uživatelského rozhraní **prohlížeče výsledků prohlížeče výsledků testu webu.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Vytvoření nebo otevření řešení, které obsahuje ASP.NET webovou aplikaci a projekt webového výkonu a zátěžového testu

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Příprava na rozšíření prohlížeče výsledků testů výkonu webu

Vytvořte nebo otevřete neprodukční řešení, se kterým můžete experimentovat, se kterým je ASP.NET webová aplikace a webový výkon a projekt zátěžového testu s jedním nebo více testy výkonu webu pro ASP.NET webovou aplikaci.

> [!NOTE]
> Můžete vytvořit ASP.NET webové aplikace a výkonu webu a zatížení testovací projekt, který obsahuje testy výkonu webu podle postupů [v: Vytvořit test webové služby](../test/how-to-create-a-web-service-test.md) a [generovat a spustit kódovaný test výkonu webu](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Vytvoření doplňku sady Visual Studio

Doplněk je zkompilovaná dll, která běží v integrovaném vývojovém prostředí sady Visual Studio (IDE). Kompilace pomáhá chránit vaše duševní vlastnictví a zlepšuje výkon. Přestože doplňky můžete vytvořit ručně, může být jednodušší použít **Průvodce doplňky**. Tento průvodce vytvoří funkční, ale základní doplněk, který lze spustit ihned po jeho vytvoření. Poté, co **Průvodce doplňkem** vygeneruje základní program, můžete do něj přidat kód a přizpůsobit jej.

**Průvodce doplňkem** umožňuje zadat zobrazovaný název a popis doplňku. Obě se zobrazí ve **Správci doplňků**. Volitelně můžete nechat průvodce vygenerovat kód, který přidá do nabídky **Nástroje** příkaz k otevření doplňku. Můžete také zvolit zobrazení vlastního dialogového okna **Informace** pro doplněk. Po dokončení průvodce máte nový projekt, který má pouze jednu třídu, která implementuje doplněk. Tato třída se nazývá Connect.

Budete používat **Správce doplňků** na konci tohoto článku.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Vytvoření doplňku pomocí Průvodce doplňkem

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na řešení, zvolte **Přidat**a pak vyberte **Nový projekt**.

2. Vytvořte nový projekt **doplňku sady Visual Studio.**

    Spustí se **Průvodce doplňkem** sady Visual Studio.

3. Zvolte **Další**.

4. Na stránce **Vybrat programovací jazyk** vyberte programovací jazyk, který chcete použít k napsání doplňku.

   > [!NOTE]
   > Toto téma používá visual c# pro ukázkový kód.

5. Na stránce **Vybrat hostitele aplikace** vyberte Visual **Studio** a zrušte **zaškrtnutí políčka Makra sady Visual Studio**.

6. Zvolte **Další**.

7. Na stránce Zadejte název a popis doplňku na stránce **Zadejte název a popis.**

     Po vytvoření doplňku se jeho název a popis zobrazí v seznamu **Dostupné doplňky ve** **Správci doplňků**. Přidejte k popisu doplňku dostatek podrobností, aby se uživatelé mohli dozvědět, co váš doplněk dělá, jak funguje a tak dále.

8. Zvolte **Další**.

9. Na stránce **Zvolit možnosti doplňku** vyberte **chcete, aby se doplněk načítaný při spuštění hostitelské aplikace**.

10. Zrušte zaškrtnutí zbývajících políček.

11. Na stránce **Výběr informací nápovědy** můžete určit, zda se mají informace o doplňku zobrazit v dialogovém okně **Informace.** Pokud chcete, aby se informace zobrazily, zaškrtněte políčko **Ano, chci, aby můj doplněk nabízel informace o doplňku.**

     Informace, které lze přidat do dialogového okna Visual Studio **O** zahrnuje číslo verze, podrobnosti o podpoře, licenční data a tak dále.

12. Zvolte **Další**.

13. Vybrané možnosti se zobrazí na stránce **Souhrn,** které můžete zkontrolovat. Pokud jste spokojeni, zvolte **Dokončit** a vytvořte doplněk. Pokud chcete něco změnit, zvolte tlačítko **Zpět.**

     Nové řešení a projekt jsou vytvořeny a *soubor Connect.cs* pro nový doplněk se zobrazí v **Editoru kódu**.

     Kód přidáte do souboru *Connect.cs* po následujícím postupu, který vytvoří uživatelský ovládací prvek, na který bude odkazovat tento projekt WebPerfTestResultsViewerAddin.

    Po vytvoření doplňku je nutné jej zaregistrovat v sadě Visual Studio, aby mohl být aktivován ve **Správci doplňků**. To provést pomocí souboru XML, který má příponu *addin.*

    Soubor *ADDIN* popisuje informace, které Visual Studio potřebuje k zobrazení doplňku ve **Správci doplňků**. Při spuštění sady Visual Studio vyhledá v umístění souboru *ADDIN* všechny dostupné soubory *ADDIN.* Pokud nějaký vyhledá, přečte soubor XML a poskytne **Správci doplňků** informace, které vyžaduje ke spuštění doplňku po klepnutí.

    Soubor *ADDIN* se vytvoří automaticky při vytváření doplňku pomocí **Průvodce doplňkem**.

### <a name="add-in-file-locations"></a>Umístění souborů doplňku

**Průvodcem doplňkem**jsou automaticky vytvořeny dvě kopie souborů *addin:*

|**. Umístění souboru Doplňku**|**Popis**|
|-|----------------------------|-|
|Kořenová složka projektu|Používá se pro nasazení projektu doplňku. Součástí projektu pro snadné úpravy a má místní cestu pro nasazení stylu XCopy.|
|Složka doplňku|Používá se pro spuštění doplňku v prostředí ladění. By vždy přejděte na výstupní cestu aktuální konfigurace sestavení.|

## <a name="create-a-windows-form-control-library-project"></a>Vytvoření projektu knihovny řízení formulářů systému Windows

Doplněk visual studio vytvořený v předchozím postupu odkazuje na projekt knihovny ovládacího <xref:System.Windows.Forms.UserControl> prvku systému Windows a vytvoří instanci třídy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Vytvoření ovládacího prvku, který bude použit v prohlížeči výsledků webových testů

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na řešení, zvolte **Přidat**a pak vyberte **Nový projekt**.

2. Vytvořte nový projekt **knihovny řízení formulářů systému Windows.**

3. Z **panelu nástrojů** <xref:System.Windows.Forms.DataGridView> přetáhněte a na povrch userControl1.

4. Klikněte na glyf značky akce (Flyfg)![](../test/media/vs_winformsmttagglyph.gif)v pravém horním rohu a <xref:System.Windows.Forms.DataGridView> postupujte takto:

    1. Zvolte **Dock v nadřazeném kontejneru**.

    2. Zrušte zaškrtnutí políček **Povolit přidávání**, **Povolit úpravy**, **Povolit odstranění** a **Povolit změnu pořadí sloupců**.

    3. Zvolte **Přidat sloupec**.

         Zobrazí se dialogové okno **Přidat sloupec.**

    4. V rozevíracím seznamu **Typ** vyberte **položku DataGridViewTextBoxColumn**.

    5. Zrušte zaškrtnutí textu "Sloupec 1" v **textu záhlaví**.

    6. Zvolte **Přidat**.

    7. Zvolte **Zavřít**.

5. V okně **Vlastnosti** změňte vlastnost **(Name)** <xref:System.Windows.Forms.DataGridView> vlastnosti **resultControlDataGridView**.

6. Klepněte pravým tlačítkem myši na návrhovou plochu a vyberte **příkaz Zobrazit kód**.

     Soubor *UserControl1.cs* se zobrazí v **Editoru kódu**.

7. Změňte název instance <xref:System.Windows.Forms.UserControl> třídy z UserContro1 resultControl:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     V dalším postupu přidáte kód do *Connect.cs* souboru projektu WebPerfTestResultsViewerAddin, který bude odkazovat na třídu resultControl.

     Do souboru *Connect.cs* budete později přidávat další kód.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Přidání kódu do doplňku WebPerfTestResultsViewerAddin

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Reference** v projektu WebPerfTestResultsViewerAddin a vyberte příkaz **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** zvolte kartu **.NET.**

3. Posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a **System.Windows.Forms**.

4. Vyberte **OK**.

5. Znovu klepněte pravým tlačítkem myši na uzel **Odkazy** a vyberte **přidat odkaz**.

6. V dialogovém okně **Přidat odkaz** zvolte kartu **Procházet.**

7. Zvolte rozevírací seznam **Pro Hledat a** přejděte na *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* a vyberte soubor *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll.*

8. Vyberte **OK**.

9. Klepněte pravým tlačítkem myši na uzel projektu WebPerfTestResultsViewerAddin a vyberte **příkaz Přidat odkaz**.

10. V dialogovém okně **Přidat odkaz** zvolte kartu **Projekty.**

11. V části **Název projektu**vyberte projekt **WebPerfTestResultsViewerControl** a zvolte **OK**.

12. Pokud *Connect.cs* soubor ještě není otevřený, klepněte v **Průzkumníku řešení**pravým tlačítkem myši na **soubor Connect.cs** v projektu WebPerfTestResultsViewerAddin a vyberte zobrazit **kód**.

13. Do *souboru Connect.cs* přidejte následující příkazy Using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Posuňte se dolů do dolní části *Connect.cs* souboru. Je třeba přidat seznam identifikátorů GUID <xref:System.Windows.Forms.UserControl> pro případ, že je otevřena více než jedna instance prohlížeče výsledků testů výkonu **webu.** Budete přidávat kód později, který používá tento seznam.

     Druhý Seznam řetězec se používá v OnDiscconection metoda, kterou budete kód ovat později.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Soubor *Connect.cs* konkretizuje třídu <xref:Extensibility.IDTExtensibility2> s názvem Připojit ze třídy a také obsahuje některé metody pro implementaci doplňku sady Visual Studio. Jednou z metod je metoda OnConnection, která obdrží oznámení, že doplněk je načítán. V metodě OnConnection použijete třídu LoadTestPackageExt k vytvoření balíčku rozšiřitelnosti pro **prohlížeč výsledků testu výkonu webu**. Přidejte následující kód do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Přidejte následující kód do třídy connect a vytvořte metodu WebTestResultViewerExt_WindowCreated pro metodu loadTestPackageExt.WebTestResultViewerExt.WindowCreated obslužnou rutinu události, kterou jste přidali do metody OnConnection a metody WindowCreated, která volání metody WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Přidejte do třídy connect následující kód pro vytvoření metody WebTestResultViewer_SelectedChanged pro loadTestPackageExt.WebTestResultViewerExt.SelectionChanged obslužnou rutinu události, kterou jste přidali do metody OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Přidejte následující kód do třídy connect a vytvořte metodu WebTesResultViewer_WindowClosed pro obslužnou rutinu události pro loadTestPackageExt.WebTestResultViewerExt.WindowZavřeno, které jste přidali do metody OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Nyní, když byl kód dokončen pro doplněk sady Visual Studio, je třeba přidat metodu Update do resultControl v projektu WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Přidání kódu do ovládacího prvku WebPerfTestResultsViewer

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel projektu WebPerfTestResultsViewerControl a vyberte příkaz **Vlastnosti**.

2. Vyberte kartu **Aplikace** a pak zvolte rozevírací seznam **Cílová architektura** a vyberte **rozhraní .NET Framework 4** (nebo novější). Zavřete okno **Vlastnosti.**

   To je nutné pro podporu odkazů dll, které jsou potřebné pro rozšíření **prohlížeče výsledků testů výkonu webu**.

3. V **Průzkumníku řešení**klikněte v projektu WebPerfTestResultsViewerControl pravým tlačítkem myši na uzel **Odkazy** a vyberte **přidat odkaz**.

4. V dialogovém okně **Přidat odkaz** klepněte na kartu **.NET.**

5. Posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Vyberte **OK**.

7. Do *souboru UserControl1.cs* přidejte následující příkazy Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Přidejte metodu Update, která je volána a předána metodě WebTestRequestResult z metody WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged v *souboru Connect.cs.* Update Metoda naplní DataGridView s různými vlastnostmi, které jí byly předány v WebTestRequestResult.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Sestavení řešení

- V nabídce **Build** vyberte **Build Solution**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrace doplňku WebPerfTestResultsViewerAddin

1. V nabídce **Nástroje** vyberte **Správce doplňků**.

2. Zobrazí se dialogové okno **Správce doplňků.**

3. Zaškrtněte políčko pro doplněk WebPerfTestResultsViewerAddin ve sloupci **Dostupné doplňky** a zrušte zaškrtnutí políček pod sloupci **Po spuštění** a **Příkazový řádek.**

4. Vyberte **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Spuštění testu výkonu webu pomocí prohlížeče výsledků webových testů

1. Spusťte test výkonu webu a uvidíte novou kartu doplňku WebPerfTestResultsViewerAddin s názvem Ukázka zobrazená v **prohlížeči výsledků testů výkonnosti webu**.

2. Zvolte kartu, chcete-li zobrazit vlastnosti prezentované v zobrazení DataGridView.

## <a name="net-security"></a>Zabezpečení .NET

Chcete-li zlepšit zabezpečení tím, že zabráníte automatické aktivaci škodlivých doplňků, poskytuje sada Visual Studio nastavení na stránce **Možnosti nástrojů** s názvem **Zabezpečení doplňků a maker**.

Kromě toho tato stránka možností umožňuje určit složky, ve kterých aplikace Visual Studio vyhledává *. AddIn* registrační soubory. To zlepšuje zabezpečení tím, že umožňuje omezit umístění, kde *. AddIn* registrační soubory lze číst. To pomáhá zabránit škodlivým . * AddIn* soubory z neúmyslně používá.

**Nastavení zabezpečení doplňku**

Nastavení na stránce možností zabezpečení doplňku jsou následující:

- **Povolit načtení součástí doplňků.** Ve výchozím nastavení je zaškrtnuto. Když je tato možnost vybrána, mohou se doplňky načítat v sadě Visual Studio. Pokud není vybráno, doplňky jsou zakázány načítání v sadě Visual Studio.

- **Povolit načtení součástí doplňků z adresy URL.** Ve výchozím nastavení není vybráno. Pokud je tato možnost vybrána, lze doplňky načíst z externích webů. Pokud není vybráno, vzdálené doplňky jsou zakázány načítání v sadě Visual Studio. Pokud doplněk nelze načíst z nějakého důvodu, pak nelze načíst z webu. Toto nastavení řídí pouze načítání přidávací dll. V *. Registrační soubory addinmusí* být vždy umístěny v místním systému.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
