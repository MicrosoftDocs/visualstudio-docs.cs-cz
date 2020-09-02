---
title: 'Návod: Vytvoření základního editoru a registrace typu souboru editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 14296aa335ba6710d4d9eac8e5338af7463c0aac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687639"
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Návod: Vytvoření základního editoru a registrace typu souboru editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak vytvořit VSPackage, který spouští [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základní editor, když je načten soubor s příponou názvu souboru. myext.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Umístění pro šablonu projektu balíčku sady Visual Studio  
 Šablona projektu balíčku sady Visual Studio se dá najít ve třech různých umístěních v dialogovém okně **Nový projekt** :  
  
1. V části rozšíření Visual Basic. Výchozí jazyk projektu je Visual Basic.  
  
2. V části rozšiřitelnost jazyka C#. Výchozím jazykem projektu je C#.  
  
3. V rámci rozšíření jiných typů projektů. Výchozí jazyk projektu je C++.  
  
### <a name="to-create-the-vspackage"></a>Vytvoření balíčku VSPackage  
  
- Spusťte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] a vytvořte [!INCLUDE[csprcs](../includes/csprcs-md.md)] VSPackage s názvem `MyPackage` , jak je popsáno v [návodu: vytvoření příkazu nabídky VSPackage](https://msdn.microsoft.com/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Přidání objektu pro vytváření editoru  
  
1. Klikněte pravým tlačítkem na projekt **MyPackage** , přejděte na **Přidat** a pak klikněte na **Třída**.  
  
2. V dialogovém okně **Přidat novou položku** se ujistěte, že je vybraná Šablona **třídy** , zadejte `EditorFactory.cs` název a potom kliknutím na **Přidat** přidejte třídu do projektu.  
  
     Soubor EditorFactory.cs by měl být automaticky otevřen.  
  
3. Odkazujte na následující sestavení z kódu.  
  
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
  
4. Přidejte do třídy identifikátor GUID `EditorFactory` přidáním `Guid` atributu bezprostředně před deklarací třídy.  
  
     Nový identifikátor GUID můžete vygenerovat pomocí guidgen.exe programu na příkazovém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řádku nebo kliknutím na **vytvořit GUID** v nabídce **nástroje** . Použitý identifikátor GUID je pouze příkladem; Nepoužívejte ho v projektu.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5. V definici třídy přidejte dvě soukromé proměnné, které obsahují nadřazený balíček a poskytovatele služeb.  
  
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
  
6. Přidejte konstruktor veřejné třídy, který přijímá jeden parametr typu <xref:Microsoft.VisualStudio.Shell.Package> :  
  
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
  
7. Upravte `EditorFactory` deklaraci třídy pro odvození z <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8. Klikněte pravým tlačítkem myši <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , klikněte na **implementovat rozhraní**a pak na **implementovat rozhraní explicitně**.  
  
     Tím přidáte čtyři metody, které musí být implementovány v <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> rozhraní.  
  
9. Obsah metody `IVsEditorFactory.Close` nahraďte následujícím kódem.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Nahraďte obsah `IVsEditorFactory.SetSite` pomocí následujícího kódu.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Obsah metody `IVsEditorFactory.MapLogicalView` nahraďte následujícím kódem.  
  
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
  
12. Obsah metody `IVsEditorFactory.CreateEditorInstance` nahraďte následujícím kódem.  
  
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
  
13. Zkompilujte projekt a ujistěte se, že nejsou k dispozici žádné chyby.  
  
### <a name="to-register-the-editor-factory"></a>Registrace objektu pro vytváření editoru  
  
1. V **Průzkumník řešení**dvakrát klikněte na soubor Resources. resx a otevřete ho v tabulce řetězců, ve které je vybraná položka **řetězec1** .  
  
2. Změňte název identifikátoru na `IDS_EDITORNAME` a text na **MyPackage Editor.** Tento řetězec se zobrazí jako název vašeho editoru.  
  
3. Otevřete soubor VSPackage. resx a přidejte nový řetězec, nastavte název na **101** a hodnotu na `IDS_EDITORNAME` . To poskytuje balíčku s ID prostředku pro přístup k právě vytvořenému řetězci.  
  
    > [!NOTE]
    > Pokud soubor VSPackage. resx obsahuje jiný řetězec, který je `name` nastaven na **101**, nahraďte jinou jedinečnou číselnou hodnotu, a to v následujících krocích.  
  
4. V **Průzkumník řešení**otevřete soubor MyPackagePackage.cs.  
  
     Toto je hlavní soubor balíčku.  
  
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
  
     <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>Atribut přidruží příponu souboru. myext ke svému objektu pro vytváření editoru, aby se pokaždé, když je načten soubor s tímto rozšířením, vyvolal váš objekt pro vytváření editoru.  
  
6. Přidejte do třídy soukromou proměnnou `MyPackage` těsně před konstruktor a poskytněte jí typ `EditorFactory` .  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7. Vyhledejte `Initialize` metodu (je možné, že budete muset otevřít `Package Members` skrytou oblast) a po volání do přidat následující kód `base.Initialize()` .  
  
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
  
8. Zkompilujte program a ujistěte se, že nejsou k dispozici žádné chyby.  
  
     Tento krok registruje objekt pro vytváření editoru v experimentálním podregistru pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Pokud se zobrazí výzva k přepsání souboru Resource. h, klikněte na tlačítko **OK**.  
  
9. Vytvořte ukázkový soubor s názvem TextFile1. myext.  
  
10. Stisknutím klávesy **F5** otevřete instanci experimentálního [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
11. V experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nabídce v nabídce **soubor** přejděte na **otevřít** a pak klikněte na **soubor**.  
  
12. Vyhledejte TextFile1. myext a klikněte na **otevřít**.  
  
     Soubor by se teď měl načíst.  
  
## <a name="robust-programming"></a>Robustní programování  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Základní editor zpracovává širokou škálu textových typů souborů a úzce spolupracuje s jazykovými službami, aby poskytoval bohatou sadu funkcí, jako je například zvýrazňování syntaxe, shoda složených závorek a seznam dokončování slov a členů v technologii IntelliSense. Pokud pracujete s textovými soubory, můžete základní editor použít společně s vlastní jazykovou službou, která podporuje vaše konkrétní typy souborů.  
  
 VSPackage může vyvolat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základní editor tím, že poskytuje objekt pro vytváření editoru. Tento objekt pro vytváření editoru se používá vždy, když je načtený soubor, který je k němu přidružen. Pokud je soubor součástí projektu, pak se základní editor automaticky vyvolá, pokud není přepsáno rozhraním VSPackage. Pokud je však soubor načten mimo projekt, musí být základní editor explicitně vyvolán rozhraním VSPackage.  
  
 Další informace o základním editoru naleznete v části [uvnitř základního editoru](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Viz také  
 [Uvnitř základního editoru](../extensibility/inside-the-core-editor.md)   
 [Vytvoření instance základního editoru pomocí zastaralého rozhraní API](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
