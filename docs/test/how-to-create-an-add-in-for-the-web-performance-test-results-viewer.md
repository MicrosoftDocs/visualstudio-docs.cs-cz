---
title: Vytvoření doplňku pro prohlížeč výsledků testu výkonnosti webu
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589081"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Postupy: vytvoření doplňku pro prohlížeč Výsledky testůho webového výkonu

Můžete rozšířit uživatelské rozhraní pro **prohlížeče výsledků testu výkonnosti webu** pomocí následujících oborů názvů:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Kromě toho je třeba přidat odkaz na knihovnu DLL LoadTestPackage, která se nachází ve složce *% ProgramFiles (x86)% \ Microsoft Visual Studio\\\<verze > Složka \Enterprise\Common7\IDE\PrivateAssemblies* .

K rozšíření **prohlížeče výsledků testu výkonnosti webu**prvku uživatelského rozhraní, je nutné vytvořit doplněk sady Visual Studio a uživatelský ovládací prvek. Následující postupy vysvětlují, jak vytvořit doplněk, uživatelský ovládací prvek a jak implementovat třídy nezbytné pro rozšíření **prohlížeče výsledků testu výkonnosti webu**prvku uživatelského rozhraní.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>Vytvořte nebo otevřete řešení, které obsahuje webovou aplikaci ASP.NET a projekt testu výkonu a zatížení webu

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Příprava na rozšíření prohlížeče výsledků testu výkonnosti webu

Vytvořte nebo otevřete neprovozní řešení, můžete experimentovat s obsahující webovou aplikaci ASP.NET a výkonnosti webu a zátěžového testování projektu pomocí jedné nebo více testů výkonnosti webu pro webové aplikace ASP.NET.

> [!NOTE]
> Můžete vytvořit webovou aplikaci ASP.NET a projekt, který obsahuje testy výkonnosti webu pomocí následujících postupů v testu webového výkonu a zatížení [postupy: vytvoření testu webové služby](../test/how-to-create-a-web-service-test.md) a [generování a spuštění programového webového test výkonnosti](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="create-a-visual-studio-add-in"></a>Vytvoření doplňku sady Visual Studio

Doplněk je zkompilovaná knihovna DLL, která běží v prostředí integrovaného vývojového (prostředí IDE) sady Visual Studio. Kompilace pomáhá chránit duševní vlastnictví a zvyšuje výkon. Ačkoli doplňky můžete vytvořit ručně, může být pro vás to usnadňuje používání **Průvodce doplňkem**. Tento průvodce vytvoří funkční, ale základní doplněk, který můžete spustit ihned po jeho vytvoření. Po **Průvodce doplňkem** vygeneruje základní program, můžete k němu přidat kód a přizpůsobit jej.

**Průvodce doplňkem** umožňuje zadat zobrazovaný název a popis pro váš doplněk. Oba se objeví v **Add-In správce**. Volitelně můžete použít průvodce vygenerovat kód, který přidá **nástroje** nabídce příkaz pro otevření doplňku. Můžete také zobrazit vlastní **o** dialogové okno pro váš doplněk. Po dokončení průvodce máte nový projekt, který má pouze jednu třídu, která implementuje doplněk. Tato třída má název připojení.

Budete používat **Add-In správce** na konci tohoto článku.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>K vytvoření doplňku pomocí Průvodce doplňku

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, zvolte **přidat**a pak vyberte **nový projekt**.

2. Vytvoří nový projekt **doplňku sady Visual Studio** .

    Visual Studio **Průvodce doplňkem** spustí.

3. Zvolte **Další**.

4. Na **zvolte programovací jazyk** vyberte programovací jazyk, který chcete použít k zápisu doplňku.

   > [!NOTE]
   > Toto téma používá Visual C# pro ukázkový kód.

5. Na **zvolte hostitele aplikace** stránce **sady Visual Studio** a zrušte zaškrtnutí **makra sady Visual Studio**.

6. Zvolte **Další**.

7. Zadejte název a popis pro doplněk na **zadejte název a popis** stránky.

     Po doplněk se vytvoří, jeho název a popis se zobrazí v **dostupné doplňky** seznamu v **Add-In správce**. Přidáte dostatek podrobností do popisu doplňku tak, aby uživatelé zjistit, co doplněk dělá, jak to funguje a tak dále.

8. Zvolte **Další**.

9. Na **zvolte možnosti doplňku** stránce **chtěl bych tento doplněk načíst při spuštění aplikace hostitele**.

10. Zrušte zaškrtnutí ostatních políček.

11. Na **výběr nápovědy o informací** stránky, můžete zadat, jestli se mají informace o doplňku zobrazit v **o** dialogové okno. Pokud chcete zobrazit informace, vyberte **Ano, chtěl bych tento doplněk nabízel informace pole o** zaškrtávací políčko.

     Informace, které lze přidat do sady Visual Studio **o** dialogové okno obsahuje číslo verze, podrobnosti o odborné pomoci, údaje o licencích a tak dále.

12. Zvolte **Další**.

13. Vybrané možnosti se zobrazí na **Souhrn** stránky ke kontrole. Pokud jste spokojeni, vyberte **Dokončit** k vytvoření doplňku. Pokud chcete něco změnit, zvolte **zpět** tlačítko.

     Vytvoří se nové řešení a projektu a *Connect.cs* soubor pro nový doplněk se zobrazí v **Editor kódu**.

     Přidejte kód do *Connect.cs* soubor po následujícím postupu, který vytvoří uživatelský ovládací prvek, který bude odkazovat tento projekt WebPerfTestResultsViewerAddin.

    Po doplněk, zaregistrujte ho pomocí sady Visual Studio předtím, než je možné ho aktivovat v **Add-In správce**. Můžete to provést pomocí souboru XML, který má *.addin* příponu názvu souboru.

    *.Addin* soubor popisuje informace, které Visual Studio vyžaduje pro zobrazení doplňku v **Add-In správce**. Když Visual Studio spustí, podívá se do *.addin* umístění pro všechny souborů k dispozici *.addin* soubory. Pokud najde všechny, přečte soubor XML a poskytuje **Add-In správce** informace, které vyžaduje pro spuštění doplňku po klepnutí.

    *.Addin* soubor je vytvořen automaticky při vytvoření doplňku pomocí **Průvodce doplňkem**.

### <a name="add-in-file-locations"></a>Umístění souboru doplňku

Dvě kopie *.addin* soubory jsou automaticky vytvářeny **Průvodce doplňkem**, následujícím způsobem:

|**. Umístění souboru doplňku**|**Popis**|
|-|----------------------------|-|
|Kořenové složky projektu|Používá se pro nasazení projektu doplňku. Zahrnutý v projektu pro snadné úpravy a má místní cestu pro nasazení stylu XCopy.|
|Složka doplňku|Používá pro spuštění doplňku v prostředí ladění. Měly by vždy směrovat na výstupní cestu aktuální konfigurace sestavení.|

## <a name="create-a-windows-form-control-library-project"></a>Vytvoření projektu ovládacího prvku knihovny formulář Windows

Doplněk sady Visual Studio vytvořili v předchozí proceduře odkazuje na projekt Knihovna ovládacích prvků Windows Forms k vytvoření instance <xref:System.Windows.Forms.UserControl> třídy.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Vytvoření ovládacího prvku pro prohlížeč výsledků testu webu

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení, zvolte **přidat**a pak vyberte **nový projekt**.

2. Vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** .

3. Z **nástrojů**, přetáhněte <xref:System.Windows.Forms.DataGridView> na povrch userControl1.

4. Klikněte na akci označit piktogram (![piktogram inteligentní](../test/media/vs_winformsmttagglyph.gif)) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> a postupujte podle těchto kroků:

    1. Zvolte **ukotvit v nadřazeném kontejneru**.

    2. Zrušte zaškrtnutí políček u **povolit přidání**, **povolit úpravy**, **Povolit odstranění** a **povolit změnu pořadí sloupců**.

    3. Zvolte **přidat sloupec**.

         **Přidat sloupec** se zobrazí dialogové okno.

    4. V **typ** rozevíracího seznamu vyberte **DataGridViewTextBoxColumn**.

    5. Odstraňte text "Sloupec1" v **text záhlaví**.

    6. Zvolte **přidat**.

    7. Zvolte **Zavřít**.

5. V **vlastnosti** okno Změnit **(název)** vlastnost <xref:System.Windows.Forms.DataGridView> k **resultControlDataGridView**.

6. Klikněte pravým tlačítkem na návrhové ploše a vyberte **zobrazit kód**.

     *UserControl1.cs* soubor se zobrazí v **Editor kódu**.

7. Změna názvu instance <xref:System.Windows.Forms.UserControl> třídy z UserContro1 na resultControl:

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

     V dalším postupu přidáte kód do projektu WebPerfTestResultsViewerAddin *Connect.cs* soubor, který bude odkazovat na třídu resultControl.

     Budete přidávat další kód pro *Connect.cs* souboru později.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>Přidejte kód do doplňku WebPerfTestResultsViewerAddin

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši **odkazy** uzel projektu WebPerfTestResultsViewerAddin a vyberte **přidat odkaz**.

2. V **přidat odkaz** dialogového okna zvolte **.NET** kartu.

3. Přejděte dolů a vyberte možnost **Microsoft.VisualStudio.QualityTools.WebTestFramework** a **System.Windows.Forms**.

4. Vyberte **OK**.

5. Klikněte pravým tlačítkem myši **odkazy** uzel znovu a vyberte možnost **přidat odkaz**.

6. V **přidat odkaz** dialogového okna zvolte **Procházet** kartu.

7. Zvolte rozevírací seznam pro **Hledat v** a přejděte do *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* a vyberte  *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* souboru.

8. Vyberte **OK**.

9. Klikněte pravým tlačítkem na uzel projektu WebPerfTestResultsViewerAddin a vyberte **přidat odkaz**.

10. V **přidat odkaz** dialogového okna zvolte **projekty** kartu.

11. V části **název projektu**, vyberte **WebPerfTestResultsViewerControl** projekt a zvolte **OK**.

12. Pokud *Connect.cs* soubor není stále otevřen v **Průzkumníku řešení**, klikněte pravým tlačítkem myši **Connect.cs** v projektu WebPerfTestResultsViewerAddin a vyberte možnost  **Zobrazení kódu**.

13. V *Connect.cs* přidejte následující příkazy Using:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. Přejděte do dolní části *Connect.cs* souboru. Je třeba přidat seznam identifikátorů GUID pro <xref:System.Windows.Forms.UserControl> v případě více než jednu instanci **prohlížeče výsledků testu výkonnosti webu** je otevřený. Přidáte později kód, který používá tento seznam.

     Druhý seznam řetězce se používá v metodě OnDiscconection, která bude kódována později.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* soubor vytvoří instanci třídy s názvem připojení ze <xref:Extensibility.IDTExtensibility2> třídy a také obsahuje některé metody pro implementaci doplňku sady Visual Studio. Jednou z metod je metoda OnConnection, která obdrží oznámení, že doplněk se načítá. V metodě OnConnection použijete třídu LoadTestPackageExt pro vytvoření balíčku rozšíření pro **prohlížeče výsledků testu výkonnosti webu**. Přidejte následující kód do metody OnConnection:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. Přidejte následující kód do třídy připojení pro vytvoření metody WebTestResultViewerExt_WindowCreated metoda pro události loadtestpackageext.webtestresultviewerext.windowcreated jste přidali v metodě OnConnection a pro metodu WindowCreated, který volání metody WebTestResultViewerExt_WindowCreated.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. Přidejte následující kód do třídy připojení pro vytvoření metody webtestresultviewer_selectedchanged pro obslužnou rutinu události loadTestPackageExt.WebTestResultViewerExt.SelectionChanged, kterou jste přidali v metodě OnConnection:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. Přidejte následující kód do třídy připojení pro vytvoření metody webtesresultviewer_windowclosed pro obslužnou rutinu události pro loadTestPackageExt.WebTestResultViewerExt.WindowClosed, kterou jste přidali v metodě OnConnection:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Teď, když kód dokončen pro doplněk Visual Studio, budete muset přidat metodu aktualizace do resultControl v projektu WebPerfTestResultsViewerControl.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>Přidejte kód do ovládacího prvku WebPerfTestResultsViewerControl

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu WebPerfTestResultsViewerControl a vyberte **vlastnosti**.

2. Vyberte kartu **aplikace** a pak zvolte rozevírací seznam **cílové rozhraní** a vyberte **.NET Framework 4** (nebo novější). Zavřete okno **vlastnosti** .

   To je nutné pro podporu odkazů na knihovnu DLL, které jsou potřeba pro rozšíření **prohlížeče výsledků testu výkonnosti webu**.

3. V **Průzkumníka řešení**, v projektu WebPerfTestResultsViewerControl klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz**.

4. V **přidat odkaz** dialogové okno, klikněte na tlačítko **.NET** kartu.

5. Přejděte dolů a vyberte možnost **Microsoft.VisualStudio.QualityTools.WebTestFramework**.

6. Vyberte **OK**.

7. V *UserControl1.cs* přidejte následující příkazy Using:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Přidáte volanou metodu aktualizace, která předala WebTestRequestResult z metody WebPerfTestResultsViewerAddin webtestresultviewer_selectedchanged v *Connect.cs* souboru. Metoda aktualizovat naplní ovládací prvek DataGridView různými vlastnostmi, které do ní předány v WebTestRequestResult.

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

- Na **sestavení** nabídce vyberte možnost **sestavit řešení**.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>Registrace doplňku WebPerfTestResultsViewerAddin

1. Na **nástroje** nabídce vyberte možnost **Add-in správce**.

2. **Add-in správce** se zobrazí dialogové okno.

3. Zaškrtněte políčko pro doplněk WebPerfTestResultsViewerAddin ve **dostupné doplňky** sloupce a zrušte zaškrtnutí políček v sloupcích **spuštění** a **příkazového řádku**sloupce.

4. Vyberte **OK**.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Spustit test výkonnosti webu pomocí nástroje Web Výsledky testů Viewer

1. Spuštění testu výkonnosti webu a zobrazí se doplňku WebPerfTestResultsViewerAddin nová karta s názvem zobrazí v ukázkové **prohlížeče výsledků testu výkonnosti webu**.

2. Klepněte na kartu pro zobrazení vlastnosti zobrazených v ovládacím prvku DataGridView.

## <a name="net-security"></a>Zabezpečení .NET

Chcete-li zlepšit zabezpečení zabráněním škodlivým doplňkům v automatické aktivaci, Visual Studio obsahuje nastavení na **možnosti nástrojů** stránku s názvem **přidat doplňků/maker zabezpečení**.

Kromě toho tato stránka možností umožňuje určit složky, ve kterých hledá sady Visual Studio *. Doplněk* registrační soubory. To vylepšuje zabezpečení tím, že je možné omezit místa kde *. Doplněk* lze číst soubory registrace. To pomáhá zabránit škodlivým *. Doplněk* soubory z neúmyslným použitím.

**Nastavení zabezpečení doplňku**

Nastavení na stránce Možnosti pro doplněk zabezpečení jsou následující:

- **Povolit přidat součásti pro načtení.** Ve výchozím nastavení je zaškrtnuto. Vyberete-li toto políčko, doplňky mohou načíst v sadě Visual Studio. Pokud není vybrána, doplňky mají zakázáno načítání v aplikaci Visual Studio.

- **Povolit přidat součásti pro načtení z adresy URL.** Nejsou vybrány ve výchozím nastavení. Pokud je vybráno, je možné načíst doplňky z externích webových stránek. Pokud není vybrána, vzdálené doplňky mají zakázáno načítání v aplikaci Visual Studio. Pokud z nějakého důvodu nelze načíst doplněk, pak jej nelze načíst z webu. Toto nastavení řídí pouze načítání DLL doplňku. *. Doplněk* registrační soubory musí být vždy umístěny v místním systému.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
