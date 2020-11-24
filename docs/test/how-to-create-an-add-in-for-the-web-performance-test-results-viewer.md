---
title: Vytvoření Add-In pro prohlížeč Výsledky testů webového výkonu
description: Naučte se vytvořit doplněk sady Visual Studio pro rozšiřování uživatelského rozhraní webového výkonu Výsledky testů Viewer a implementaci tříd nezbytných pro rozšiřování uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8fa3b83fb9a92be0118f4222e92364767affcda
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95441075"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Postupy: vytvoření doplňku pro prohlížeč Výsledky testůho webového výkonu

Uživatelské rozhraní pro **prohlížeč výsledky testůho webového výkonu** můžete roztáhnout pomocí následujících oborů názvů:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Kromě toho je třeba přidat odkaz na knihovnu DLL LoadTestPackage, která se nachází ve složce *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \Enterprise\Common7\IDE\PrivateAssemblies* .

Chcete-li roztáhnout uživatelské rozhraní **webového výkonu výsledky testů Viewer**, je nutné vytvořit doplněk sady Visual Studio a uživatelský ovládací prvek. Následující postupy vysvětlují, jak vytvořit doplněk, uživatelský ovládací prvek a jak implementovat třídy nezbytné pro rozšiřování uživatelského rozhraní **webového výkonu výsledky testů Viewer**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Vytvořte nebo otevřete řešení, které obsahuje webovou aplikaci ASP.NET a projekt testů výkonnosti webu a zátěžového testu.

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Příprava na rozšíření webového výkonu Výsledky testů Vieweru

Buď vytvořte nebo otevřete neprodukční řešení, které můžete experimentovat obsahující webovou aplikaci ASP.NET a projekt testů výkonnosti webu a zátěžového testu s jedním nebo více testy webového výkonu pro webovou aplikaci ASP.NET.

> [!NOTE]
> Můžete vytvořit projekt webové aplikace ASP.NET a projekt zátěžového testu, který obsahuje testy výkonnosti webu, pomocí postupů v tématu Postupy [: vytvoření testu webové služby](../test/how-to-create-a-web-service-test.md) a [generování a spuštění kódovaného testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Vytvoření doplňku pro Visual Studio

Doplněk je kompilovaná knihovna DLL, která běží v integrovaném vývojovém prostředí (IDE) sady Visual Studio. Kompilace pomáhá chránit duševní vlastnictví a zvyšuje výkon. I když lze doplňky vytvořit ručně, může být snazší použít **Průvodce doplňkem**. Tento průvodce vytvoří funkční, ale základní doplněk, který můžete spustit hned po jeho vytvoření. Poté, co **Průvodce doplňky** vygeneruje základní program, můžete do něj přidat kód a přizpůsobit jej.

**Průvodce doplňkem** umožňuje zadat zobrazovaný název a popis pro doplněk. Oba se zobrazí ve **Správci doplňků**. Volitelně můžete nechat průvodce vygenerovat kód, který přidá do nabídky **nástroje** příkaz k otevření doplňku. Můžete také zvolit, že se má zobrazit **vlastní dialog** pro váš doplněk. Po dokončení průvodce máte nový projekt, který má pouze jednu třídu, která implementuje doplněk. Tato třída má název Connect.

Na konci tohoto článku budete používat **Správce doplňků** .

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Vytvoření doplňku pomocí Průvodce Add-In

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a **Nový projekt**.

2. Vytvoří nový projekt **doplňku sady Visual Studio** .

    Spustí se **Průvodce doplňky** sady Visual Studio.

3. Zvolte **Další**.

4. Na stránce **vyberte programovací jazyk** vyberte programovací jazyk, který chcete použít k zápisu doplňku.

   > [!NOTE]
   > Toto téma používá Visual C# pro ukázkový kód.

5. Na stránce **Vybrat hostitele aplikace** vyberte možnost **Visual Studio** a zrušte zaškrtnutí políček **makra aplikace Visual Studio**.

6. Zvolte **Další**.

7. Zadejte název a popis pro doplněk na stránce **Zadejte název a popis** .

     Po vytvoření doplňku se jeho název a popis zobrazí v seznamu **dostupné doplňky** ve **Správci doplňků**. Přidejte do popisu doplňku dostatek podrobností, aby se uživatelé mohli dozvědět, co váš doplněk funguje, jak funguje a tak dále.

8. Zvolte **Další**.

9. Na stránce **zvolit možnosti Add-In** vyberte možnost **Chci načíst doplněk při spuštění hostitelské aplikace**.

10. Zrušte zaškrtnutí zbývajících políček.

11. Na stránce **Výběr informací o nápovědě** můžete určit, jestli se mají informace o doplňku zobrazit v dialogovém okně **o produktu** . Pokud chcete, aby se informace zobrazovaly, zaškrtněte políčko **Ano, chci, aby doplněk nabízel informace v dialogovém okně "o produktu** ".

     Informace, které mohou být přidány do dialogového okna **o** aplikaci Visual Studio, zahrnují číslo verze, podrobnosti o podpoře, údaje o licencích a tak dále.

12. Zvolte **Další**.

13. Možnosti, které jste vybrali, se zobrazí na stránce **Souhrn** , abyste si je mohli prohlédnout. Pokud jste spokojeni, vytvořte doplněk kliknutím na tlačítko **Dokončit** . Pokud chcete něco změnit, klikněte na tlačítko **zpět** .

     Nové řešení a projekt jsou vytvořeny a soubor *Connect.cs* pro nový doplněk se zobrazí v **editoru kódu**.

     Do souboru *Connect.cs* přidáte kód za následujícím postupem, který vytvoří uživatelský ovládací prvek, na který bude odkazovat tento projekt WebPerfTestResultsViewerAddin.

    Po vytvoření doplňku je nutné jej zaregistrovat v aplikaci Visual Studio, aby jej bylo možné aktivovat ve **Správci doplňků**. Můžete to provést pomocí souboru XML, který má příponu názvu souboru *. AddIn* .

    Soubor *. AddIn* popisuje informace, které Visual Studio vyžaduje k zobrazení doplňku ve **Správci doplňků**. Po spuštění sady Visual Studio se vyhledá v umístění souboru *. AddIn* pro všechny dostupné soubory *. AddIn* . Pokud najde nějaké, přečte soubor XML a poskytne **Správci doplňků** informace, které vyžaduje pro spuštění doplňku při kliknutí.

    Soubor *. AddIn* se vytvoří automaticky při vytvoření doplňku pomocí **Průvodce doplňkem**.

### <a name="add-in-file-locations"></a>Umístění souborů doplňku

**Průvodce doplňkem** automaticky vytvoří dvě kopie souborů *. AddIn* , a to následujícím způsobem:

|**Umístění souboru. AddIn**|**Popis**|
|-|----------------------------|-|
|Kořenová složka projektu|Používá se pro nasazení projektu doplňku. Zahrnutí v projektu pro usnadnění úprav a má místní cestu pro nasazení ve stylu XCopy.|
|Složka doplňků|Používá se pro spuštění doplňku v ladicím prostředí. Vždy odkazovat na výstupní cestu aktuální konfigurace sestavení.|

## <a name="create-a-windows-form-control-library-project"></a>Vytvořit projekt knihovny ovládacích prvků formulářů Windows

Doplněk sady Visual Studio vytvořený v předchozím postupu odkazuje na projekt knihovny ovládacích prvků model Windows Forms pro vytvoření instance <xref:System.Windows.Forms.UserControl> třídy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Vytvoření ovládacího prvku, který se má použít ve webovém Výsledky testů Vieweru

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na řešení, vyberte možnost **Přidat** a **Nový projekt**.

2. Vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** .

3. Z **panelu nástrojů** přetáhněte na <xref:System.Windows.Forms.DataGridView> povrch UserControl1.

4. V pravém horním rohu okna klikněte na glyf značky akce ( ![ glyf inteligentních značek ](../test/media/vs_winformsmttagglyph.gif) ) <xref:System.Windows.Forms.DataGridView> a postupujte podle těchto kroků:

    1. Vyberte **Dock v nadřazeném kontejneru**.

    2. Zrušte zaškrtnutí políček **Povolit přidávání**, **Povolit úpravy**, **Povolit odstraňování** a **Povolit změnu pořadí sloupců**.

    3. Vyberte možnost **Přidat sloupec**.

         Zobrazí se dialogové okno **Přidat sloupec** .

    4. V rozevíracím seznamu **typ** vyberte možnost **DataGridViewTextBoxColumn**.

    5. Vymaže text "Sloupec1" v **textu záhlaví**.

    6. Klikněte na tlačítko **Přidat**.

    7. Klikněte na tlačítko **Zavřít**.

5. V okně **vlastnosti** změňte vlastnost **(název)** na <xref:System.Windows.Forms.DataGridView> **resultControlDataGridView**.

6. Klikněte pravým tlačítkem myši na návrhovou plochu a vyberte **Zobrazit kód**.

     V **editoru kódu** se zobrazí soubor *UserControl1.cs* .

7. Změňte název instance <xref:System.Windows.Forms.UserControl> třídy z UserContro1 na resultControl:

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

     V dalším postupu přidáte kód do souboru *Connect.cs* projektu WebPerfTestResultsViewerAddin, který bude odkazovat na třídu resultControl.

     Později do souboru *Connect.cs* přidáte nějaký další kód.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Přidat kód do WebPerfTestResultsViewerAddin

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **odkazy** v projektu WebPerfTestResultsViewerAddin a vyberte možnost **Přidat odkaz**.

2. V dialogovém okně **Přidat odkaz** vyberte kartu **.NET** .

3. Přejděte dolů a vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework** a **System. Windows. Forms**.

4. Vyberte **OK**.

5. Znovu klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.

6. V dialogovém okně **Přidat odkaz** klikněte na kartu **Procházet** .

7. Zvolte rozevírací seznam pro **hledání** a přejděte na *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* a vyberte soubor *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* .

8. Vyberte **OK**.

9. Klikněte pravým tlačítkem myši na uzel projektu WebPerfTestResultsViewerAddin a vyberte možnost **Přidat odkaz**.

10. V dialogovém okně **Přidat odkaz** vyberte kartu **projekty** .

11. V části **název projektu** vyberte projekt **WebPerfTestResultsViewerControl** a klikněte na **tlačítko OK**.

12. Pokud soubor *Connect.cs* ještě není otevřený, klikněte v **Průzkumník řešení** pravým tlačítkem myši na soubor **Connect.cs** v projektu WebPerfTestResultsViewerAddin a vyberte **Zobrazit kód**.

13. V souboru *Connect.cs* přidejte následující příkazy using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Posuňte se dolů k dolnímu okraji souboru *Connect.cs* . Je nutné přidat seznam identifikátorů GUID pro <xref:System.Windows.Forms.UserControl> v případě, že je otevřeno více než jedna instance **webového výkonu výsledky testů Viewer** . Později přidáte kód, který bude používat tento seznam.

     V metodě OnDiscconection se použije druhý seznam řetězců, který budete kódovat později.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. Soubor *Connect.cs* vytvoří instanci třídy s názvem Connect z <xref:Extensibility.IDTExtensibility2> třídy a také obsahuje některé metody pro implementaci doplňku Visual Studio. Jednou z metod je metoda připojení, která přijímá oznámení o načtení doplňku. V metodě připojení použijete třídu LoadTestPackageExt k vytvoření balíčku rozšiřitelnosti pro **prohlížeč webového výkonu výsledky testů Viewer**. Do metody připojení přidejte následující kód:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Přidejte následující kód do třídy připojit k vytvoření metody WebTestResultViewerExt_WindowCreated pro obslužnou rutinu události loadTestPackageExt. WebTestResultViewerExt. WindowCreated, kterou jste přidali v metodě připojení a pro metodu WindowCreated, kterou metoda WebTestResultViewerExt_WindowCreated volá.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Přidejte následující kód do třídy připojit a vytvořte tak metodu WebTestResultViewer_SelectedChanged pro obslužnou rutinu události loadTestPackageExt. WebTestResultViewerExt. SelectionChanged, kterou jste přidali v metodě připojení:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Přidejte následující kód do třídy připojit a vytvořte tak metodu WebTesResultViewer_WindowClosed pro obslužnou rutinu události pro loadTestPackageExt. WebTestResultViewerExt. WindowClosed lze použít, kterou jste přidali v metodě připojení:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Nyní, když byl kód dokončen pro doplněk sady Visual Studio, je nutné přidat metodu aktualizace do resultControl v projektu WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Přidat kód do WebPerfTestResultsViewerControl

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu WebPerfTestResultsViewerControl a vyberte možnost **vlastnosti**.

2. Vyberte kartu **aplikace** a pak zvolte rozevírací seznam **cílové rozhraní** a vyberte **.NET Framework 4** (nebo novější). Zavřete okno **vlastnosti** .

   To je nutné, aby bylo možné podporovat reference knihoven DLL, které jsou potřeba pro rozšíření **webového výkonu výsledky testů Vieweru**.

3. V **Průzkumník řešení** projektu WebPerfTestResultsViewerControl klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.

4. V dialogovém okně **Přidat odkaz** klikněte na kartu **.NET** .

5. Přejděte dolů a vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework**.

6. Vyberte **OK**.

7. V souboru *UserControl1.cs* přidejte následující příkazy using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Přidejte metodu aktualizace, která je volána a předala WebTestRequestResult z metody WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged v souboru *Connect.cs* . Metoda Update naplní ovládací prvek DataGridView pomocí různých vlastností předaných do něj v WebTestRequestResult.

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

- V nabídce **sestavení** vyberte **Sestavit řešení**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrace doplňku WebPerfTestResultsViewerAddin

1. V nabídce **nástroje** vyberte **Správce doplňků**.

2. Zobrazí se dialogové okno **Správce doplňků** .

3. Zaškrtněte políčko u doplňku WebPerfTestResultsViewerAddin ve sloupci **dostupné doplňky** a zrušte zaškrtnutí políček pod sloupci **spouštěcí** a **příkazový řádek** .

4. Vyberte **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Spustit test výkonnosti webu pomocí nástroje Web Výsledky testů Viewer

1. Spusťte test výkonnosti webu a uvidíte, že se v **prohlížeči výsledky testůho webového výkonu** zobrazí karta nový s názvem Sample.

2. Kliknutím na kartu zobrazíte vlastnosti zobrazené v ovládacím prvku DataGridView.

## <a name="net-security"></a>Zabezpečení .NET

Aby bylo možné zvýšit zabezpečení zabráněním škodlivým doplňkům v automatické aktivaci, aplikace Visual Studio poskytuje nastavení na stránce **Možnosti nástrojů** s názvem **doplněk/zabezpečení maker**.

Kromě toho tato stránka možností umožňuje určit složky, ve kterých aplikace Visual Studio vyhledává *. Registrační soubory doplňku* . To zlepšuje zabezpečení tím, že umožňuje omezit umístění, kde *.* Lze číst registrační soubory doplňku. To pomáhá zabránit škodlivému *. Soubory AddIn* z neúmyslného použití.

**Nastavení zabezpečení doplňku**

Nastavení na stránce možnosti pro zabezpečení doplňku jsou následující:

- **Umožňuje načtení součástí doplňku.** Ve výchozím nastavení je zaškrtnuto. Je-li toto políčko zaškrtnuto, doplňky mohou být načteny v aplikaci Visual Studio. Když není vybraná, doplňky se v aplikaci Visual Studio zakazují načíst.

- **Umožňuje načtení součástí doplňku z adresy URL.** Nevybráno ve výchozím nastavení. Když je tato možnost vybraná, doplňky se dají načíst z externích webů. Není-li toto políčko zaškrtnuto, vzdálené doplňky mají zakázáno načítání v aplikaci Visual Studio. Pokud doplněk z nějakého důvodu nelze načíst, nelze jej načíst z webu. Toto nastavení řídí pouze načtení knihovny DLL doplňku. Rozhraní *. Registrační soubory doplňku* musí být vždy umístěny v místním systému.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
