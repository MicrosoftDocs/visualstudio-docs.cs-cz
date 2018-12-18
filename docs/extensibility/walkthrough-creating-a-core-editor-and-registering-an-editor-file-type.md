---
title: Základní Editor vytváří a registruje typem souboru Editor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e00b96d1f5361d3d5260296532be47636f430d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921454"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>Návod: Vytvoření základní editor a registraci typu souboru editoru
Tento návod ukazuje, jak vytvořit VSPackage, která se spustí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základním editoru při otevření souboru se *.myext* příponu názvu souboru je načtena.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro Visual Studio balíček šablony projektu  
 Šablona projektu balíček Visual Studio najdete ve třech různých umístěních v **nový projekt** dialogové okno:  
  
1.  V části **rozšiřitelnosti Visual Basic**. Je výchozí jazyk projektu jazyka Visual Basic.  
  
2.  V části **rozšíření jazyka C#**. Je výchozí jazyk projektu C#.  
  
3.  V části **jiný projekt typy rozšíření**. Výchozí jazyk projektu je C++.  
  
### <a name="to-create-the-vspackage"></a>Vytvoření sady VSPackage  
  
- Spustit [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a vytvořit [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage s názvem `MyPackage`, jak je uvedeno v [návod: vytvoření příkazu nabídky VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Chcete-li přidat objekt factory editoru  
  
1. Klikněte pravým tlačítkem myši **MyPackage** projektu, přejděte na **přidat**a potom klikněte na tlačítko **třídy**.  
  
2. V **přidat novou položku** dialogové okno pole, ujistěte se, že **třídy** šablonu vyberou, typ `EditorFactory.cs` pro název a pak klikněte na tlačítko **přidat** přidání třídy do projektu.  
  
    *EditorFactory.cs* soubor by měl zobrazit automaticky.  
  
3. Odkazujte na následující sestavení z vašeho kódu.  
  
   ```vb  
   Imports System.Runtime.InteropServices  
   Imports Microsoft.VisualStudio  
   Imports Microsoft.VisualStudio.Shell  
   Imports Microsoft.VisualStudio.Shell.Interop  
   Imports Microsoft.VisualStudio.OLE.Interop  
   Imports Microsoft.VisualStudio.TextManager.Interop  
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
   ```  
  
   ```csharp  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Shell;  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio.OLE.Interop;  
   using Microsoft.VisualStudio.TextManager.Interop;  
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
   ```  
  
4. Přidejte identifikátor GUID `EditorFactory` třídy tak, že přidáte `Guid` atribut bezprostředně před deklaraci třídy.  
  
    Nový identifikátor GUID můžete vygenerovat pomocí *guidgen.exe* programování na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] příkazového řádku, nebo kliknutím na **Create GUID** na **nástroje** nabídky. Identifikátor GUID se tady použít. je pouze příklad; Nepoužívejte ho ve vašem projektu.  
  
   ```vb  
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
   ```  
  
   ```csharp  
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
   ```  
  
5. V definici třídy přidejte dvě soukromé proměnné tak, aby obsahovala nadřazeného balíčku a poskytovatele služeb.  
  
   ```vb  
   Class EditorFactory  
       Private parentPackage As Package  
       Private serviceProvider As IOleServiceProvider  
   ```  
  
   ```csharp  
   class EditorFactory  
   {  
       private Package parentPackage;  
       private IOleServiceProvider serviceProvider;  
   }  
  
   ```  
  
6. Přidejte konstruktor veřejnou třídu, která přijímá jeden parametr typu <xref:Microsoft.VisualStudio.Shell.Package>:  
  
   ```vb  
   Public Sub New(ByVal parentPackage As Package)  
       Me.parentPackage = parentPackage  
   End Sub  
   ```  
  
   ```csharp  
   public EditorFactory(Package parentPackage)  
   {  
       this.parentPackage = parentPackage;  
   }  
   ```  
  
7. Upravit `EditorFactory` deklarace jsou odvozeny z třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní.  
  
   ```vb  
   Class EditorFactory Implements IVsEditorFacto  
   ```  
  
   ```csharp  
   class EditorFactory : IVsEditorFactory  
  
   ```  
  
8. Klikněte pravým tlačítkem na <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, klikněte na tlačítko **implementovat rozhraní**a potom klikněte na tlačítko **implementovat rozhraní explicitně**.  
  
    Tento krok přidává čtyři metody, které je třeba implementovat v <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní.  
  
9. Nahraďte obsah `IVsEditorFactory.Close` metodu s následujícím kódem.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Nahraďte obsah `IVsEditorFactory.SetSite` následujícím kódem.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Nahraďte obsah `IVsEditorFactory.MapLogicalView` metodu s následujícím kódem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Nahraďte obsah `IVsEditorFactory.CreateEditorInstance` metodu s následujícím kódem.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Kompilace projektu a ujistěte se, že zde nejsou žádné chyby.  
  
### <a name="to-register-the-editor-factory"></a>K registraci objekt factory editoru  
  
1. V **Průzkumníka řešení**, dvakrát klikněte **Resources.resx** soubor a otevře se do tabulky řetězců, ve kterém položka **řetězec1 je** vybrané.  
  
2. Změna názvu identifikátor, který `IDS_EDITORNAME` a text, který má **MyPackage editoru.** Tento řetězec se zobrazí jako název editoru.  
  
3. Otevřít **VSPackage.resx** souboru, přidejte nový řetězec, nastavte název na **101**a nastavte hodnotu na `IDS_EDITORNAME`. Tento krok obsahuje balíček s ID prostředku pro přístup k řetězci, který jste vytvořili.  
  
   > [!NOTE]
   >  Pokud **VSPackage.resx** soubor obsahuje jiný řetězec, který `name` atribut nastaven na **101**, jiný jedinečný, číselná hodnota, nahraďte tady a v následujících krocích.  
  
4. V **Průzkumníka řešení**, otevřete **MyPackagePackage.cs** souboru.  
  
    Tento soubor je soubor hlavního balíčku.  
  
5. Přidejte následující atributy uživatele těsně před `Guid` atribut.  
  
   ```vb  
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
         ".myext", 32, NameResourceID:=101 )> _  
   ```  
  
   ```csharp  
   [ProvideEditorFactory(typeof(EditorFactory), 101)]  
   [ProvideEditorExtension(typeof(EditorFactory),   
         ".myext", 32, NameResourceID = 101)]   
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> Atribut přidruží *.myext* příponu s vaší továrna editoru souboru tak, aby pokaždé, když soubor, který je, že se načte rozšíření, je vyvolán objekt pro vytváření editoru.  
  
6. Přidejte privátní proměnnou, která `MyPackage` třídu před konstruktor a přiřaďte mu typ `EditorFactory`.  
  
   ```vb  
   Private editorFactory As EditorFactory  
   ```  
  
   ```csharp  
   private EditorFactory editorFactory;  
   ```  
  
7. Najít `Initialize` – metoda (možná budete muset otevřít `Package Members` počet skrytých oblastí:) a přidejte následující kód po volání `base.Initialize()`.  
  
   ```vb  
   'Create our editor factory and register it.   
   Me.editorFactory = New EditorFactory(Me)  
   MyBase.RegisterEditorFactory(Me.editorFactory)  
   ```  
  
   ```csharp  
   // Create our editor factory and register it.  
   this.editorFactory = new EditorFactory(this);  
   base.RegisterEditorFactory(this.editorFactory);  
  
   ```  
  
8. Kompilace programu a ujistěte se, že zde nejsou žádné chyby.  
  
    Tento krok zaregistruje objekt factory editoru v experimentální podregistru pro [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pokud se zobrazí výzva k přepsání *resource.h* souboru, klikněte na tlačítko **OK**.  
  
9. Vytvoření ukázkového souboru s názvem *TextFile1.myext*.  
  
10. Stisknutím klávesy **F5** otevřete instancí experimentální instanci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. V experimentální instanci [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]na **souboru** nabídky, přejděte k **otevřít** a potom klikněte na tlačítko **souboru**.  
  
12. Najít **TextFile1.myext** a potom klikněte na tlačítko **otevřít**.  
  
     Nyní by se měly načíst soubor.  
  
## <a name="robust-programming"></a>Robustní programování  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Základní editor zpracovává širokou škálu typů textového souboru a funguje úzce u jazykové služby poskytují bohatou sadu funkcí, jako jsou zvýraznění syntaxe, párování složených závorek a slova doplňování technologie IntelliSense, a seznam dokončování členů. Pokud pracujete s textové soubory, můžete použít základní editor společně se službou vlastního jazyka, který podporuje vaši určité typy souborů.  
  
 Můžete vyvolat VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní editor zadáním objektu pro vytváření editoru. Tento objekt pro vytváření editoru se používá pokaždé, když je načten soubor, který k němu má přidružené. Pokud je soubor součástí projektu, základní editor je automaticky vyvolána, pokud není přepsán vašeho balíčku VSPackage. Nicméně pokud je soubor načten mimo projekt, základní editor musí explicitně vyvolat vašeho balíčku VSPackage.  
  
 Další informace o základní editor najdete v tématu [uvnitř základní editor](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Viz také:  
 [V editoru core](../extensibility/inside-the-core-editor.md)   
 [Vytvořit instanci editoru core pomocí starší verze rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)