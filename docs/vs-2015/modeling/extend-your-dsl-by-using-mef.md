---
title: Rozšíření vašeho DSL pomocí MEF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd5e4727c4352ca27d905bad608c4a1c17284f9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930635"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozšíření vašeho DSL pomocí MEF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete rozšíření jazyka specifického pro doménu (DSL) pomocí Managed Extensibility Framework (MEF). Vy nebo jiní vývojáři budou moct psát rozšíření pro DSL beze změny v definici DSL a kódu programu. Taková rozšíření zahrnují příkazy nabídek, přetahování myší obslužné rutiny a ověření. Uživatelé budou moct nainstalovat vašeho DSL a volitelně nainstalovat rozšíření pro něj.  
  
 Kromě toho když povolíte MEF v vašeho DSL, může být jednodušší psaní, některé funkce tohoto kódu DSL, i v případě, že všechna sestavení společně s DSL.  
  
 Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Povolit vašeho DSL prodloužit pomocí MEF  
  
1. Vytvořte novou složku s názvem **MefExtension** uvnitř **DslPackage** projektu. Přidejte do ní následující soubory:  
  
    Název souboru: `CommandExtensionVSCT.tt`  
  
   > [!IMPORTANT]
   >  Nastavte identifikátor GUID v tomto souboru bude stejná jako CommandSetId identifikátor GUID, který je definován v DslPackage\GeneratedCode\Constants.tt  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#  
   // CmdSet Guid must be defined before master template is included  
   // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt  
   Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");  
   string menuidCommandsExtensionBaseId="0x4000";  
   #>  
   <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>  
   ```  
  
    Název souboru: `CommandExtensionRegistrar.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
   ```  
  
    Název souboru: `ValidationExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
   ```  
  
    Název souboru: `ValidationExtensionRegistrar.tt`  
  
    Pokud chcete přidat tento soubor, musíte povolit ověřování v vašeho DSL pomocí alespoň jeden z parametrů v **EditorValidation** v Průzkumník DSL.  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
   ```  
  
    Název souboru: `PackageExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
   ```  
  
2. Vytvořte novou složku s názvem **MefExtension** uvnitř **Dsl** projektu. Přidejte do ní následující soubory:  
  
    Název souboru: `DesignerExtensionMetaDataAttribute.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
   ```  
  
    Název souboru: `GestureExtensionEnablement.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
   ```  
  
    Název souboru: `GestureExtensionController.tt`  
  
   ```  
   <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
   <#@ include file="Dsl\GestureExtensionController.tt" #>  
   ```  
  
3. Přidejte následující řádek do existujícího souboru s názvem **DslPackage\Commands.vsct**:  
  
   ```  
   <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
   ```  
  
    Vložit řádek za stávající `<Include>` směrnice.  
  
4. `Open DslDefinition.dsl.`  
  
5. V Průzkumníku DSL vyberte **Editor\Validation**.  
  
6. V okně Vlastnosti, ujistěte se, že nejméně jedna z vlastností s názvem **používá...**  je `true`.  
  
7. V panelu nástrojů Průzkumníka řešení, klikněte na tlačítko **Transformovat všechny šablony**.  
  
    Podpůrné soubory se zobrazí pod všechny soubory, které jste přidali.  
  
8. Sestavení a spuštění řešení Chcete-li ověřit, že stále funguje.  
  
   Vaše DSL je nyní povoleno rozhraní MEF. Příkazy nabídky, obslužné rutiny gesta a omezení ověření můžete psát jako rozšíření MEF. Tato rozšíření můžete psát ve vašem řešení DSL společně s další vlastní kód. Kromě toho vy nebo jiní vývojáři psát samostatné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření, která rozšíření vašeho DSL.  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>Vytvoření rozšíření pro DSL povolené rozhraní MEF  
 Pokud máte přístup k DSL povolené MEF vytvořené sobě nebo někomu jinému, můžete psát rozšíření pro něj. Rozšíření lze použít k přidání příkazy, obslužné rutiny gesta nebo omezení ověření. K vytváření těchto rozšíření, můžete použít [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení Extension (VSIX). Řešení se skládá ze dvou částí: projekt knihovny tříd, který vytváří sestavení kódu a projekt VSIX, která zabalí sestavení.  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>Vytvoření DSL rozšíření VSIX  
  
1. Vytvořte nový projekt knihovny tříd. Chcete-li to provést, v **nový projekt** dialogu **jazyka Visual Basic** nebo **Visual C#** a pak vyberte **knihovny tříd**.  
  
2. V nový projekt knihovny tříd přidejte odkaz na sestavení DSL.  
  
   - Toto sestavení obsahuje obvykle název, který končí na ". DSL.dll".  
  
   - Pokud máte přístup k projektu DSL, můžete najít soubor sestavení v adresáři **Dsl\bin\\\\***  
  
   - Pokud máte přístup k souboru DSL VSIX, můžete najít sestavení tak, že změníte příponu názvu souboru VSIX na ".zip". Soubor .zip dekomprimujte.  
  
3. Přidejte odkazy na následující sestavení .NET:  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
   -   System.ComponentModel.Composition.dll  
  
   -   System.Windows.Forms.dll  
  
4. Vytvořte VSIX projekt ve stejném řešení. Chcete-li to provést, v **nový projekt** dialogového okna rozbalte **jazyka Visual Basic** nebo **Visual C#**, klikněte na tlačítko **rozšiřitelnost**a pak vyberte  **Projekt VSIX**.  
  
5. V Průzkumníku řešení klikněte pravým tlačítkem na projekt VSIX a potom klikněte na tlačítko **nastavit jako spouštěný projekt**.  
  
6. V novém projektu, otevřete **source.extension.vsixmanifest**.  
  
7. Klikněte na tlačítko **přidat obsah**. V dialogovém okně nastavte **typ obsahu** k **Komponenta MEF**, a **zdrojový projekt** do projektu knihovny tříd.  
  
8. Přidáte odkaz VSIX na DSL.  
  
   1. V **source.extension.vsixmanifest**, klikněte na tlačítko **přidat odkaz**  
  
   2. V dialogovém okně klikněte na tlačítko **přidat datové části** a vyhledejte soubor VSIX DSL. Soubor VSIX je součástí řešení DSL v ** DslPackage\bin\\\\***.  
  
       To umožňuje uživatelům s instalací DSL a rozšíření ve stejnou dobu. Pokud uživatel již nainstaloval DSL, nainstaluje se pouze rozšíření.  
  
9. Zkontrolujte a aktualizujte pole z **source.extension.vsixmanifest**. Klikněte na tlačítko **vybrat vydání** a ověřte, že správné [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] edice jsou nastavené.  
  
10. Přidání kódu do projektu knihovny tříd. V příkladech v následující části použijte jako vodítko.  
  
     Můžete přidat libovolný počet příkazu, gesta a ověření třídy.  
  
11. Chcete-li otestovat rozšíření, stiskněte **F5**. V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], vytvoření nebo otevření ukázkového souboru DSL.  
  
## <a name="writing-mef-extensions-for-dsls"></a>Zápis rozšíření rozhraní MEF pro DSL  
 Tvorba rozšíření v projektu kódu sestavení samostatné řešení rozšíření DSL. MEF lze také použít ve vašem projektu DslPackage jako pohodlný způsob, jak psát příkazy, gesta a ověřovací kód jako součást DSL.  
  
### <a name="menu-commands"></a>Příkazy nabídky  
 Chcete-li zapsat příkazu nabídky, definovat třídu, která implementuje <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> a předpony třídě s atributem, který je definován v vašeho DSL, s názvem *YourDsl*`CommandExtension`. Můžete vytvořit více než jedné třídy příkazu nabídky.  
  
 `QueryStatus()` je volána pokaždé, když uživatel klepne pravým tlačítkem myši v diagramu. By měl zkontrolovat aktuální výběr a nastavte `command.Enabled` k označení, kdy příkaz se vztahuje.  
  
```  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl; // My DSL  
using Company.MyDsl.ExtensionEnablement; // My DSL  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension  
  
namespace MyMefExtension  
{  
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:  
  [MyDslCommandExtension]   
  public class MyCommandClass : ICommandExtension  
  {   
    /// <summary>  
    /// Provides access to current document and selection.  
    /// </summary>  
    [Import]  
    IVsSelectionContext SelectionContext { get; set; }  
  
    /// <summary>  
    /// Called when the user selects this command.  
    /// </summary>  
    /// <param name="command"></param>  
    public void Execute(IMenuCommand command)  
    {  
      // Transaction is required if you want to update elements.  
      using (Transaction t = SelectionContext.CurrentStore  
              .TransactionManager.BeginTransaction("fix names"))  
      {  
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)  
        {  
          ExampleElement element = shape.ModelElement as ExampleElement;  
          element.Name = element.Name + " !";  
        }  
        t.Commit();  
      }  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines whether the command should appear.  
    /// This method should set command.Enabled and command.Visible.  
    /// </summary>  
    /// <param name="command"></param>  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled =  
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);  
    }  
  
    /// <summary>  
    /// Called when the user right-clicks the diagram.  
    /// Determines the text of the command in the menu.  
    /// </summary>  
    public string Text  
    {  
      get { return "My menu command"; }  
    }  
  }  
}  
  
```  
  
### <a name="gesture-handlers"></a>Obslužné rutiny gesta  
 Obslužné rutiny gesta můžete vyřešit objekty přetáhnout do diagramu z libovolného místa, uvnitř nebo vně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Následující příklad umožňuje uživateli přetáhnout soubory do diagramu z Průzkumníka Windows. Vytvoří prvky, které obsahují názvy souborů.  
  
 Můžete napsat obslužné rutiny řešit drags z jiných DSL modely a modelech UML. Další informace najdete v tématu [postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
```  
  
using System.ComponentModel.Composition;  
using System.Linq;  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling; // Transactions  
using Microsoft.VisualStudio.Modeling.Diagrams;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;   
  
namespace MefExtension  
{  
  [MyDslGestureExtension]  
  class MyGestureExtension : IGestureExtension  
  {  
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)  
    {  
      System.Windows.Forms.MessageBox.Show("double click!");  
    }  
  
    /// <summary>  
    /// Called when the user drags anything over the diagram.  
    /// Return true if the dragged object can be dropped on the current target.  
    /// </summary>  
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>  
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>  
    /// <returns></returns>  
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      // This handler only allows items to be dropped onto the diagram:  
      return targetMergeElement is MefDsl2Diagram &&  
      // And only accepts files dragged from Windows Explorer:  
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");  
    }  
  
    /// <summary>  
    /// Called when the user drops an item onto the diagram.  
    /// </summary>  
    /// <param name="targetDropElement"></param>  
    /// <param name="diagramDragEventArgs"></param>  
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)  
    {  
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;  
      if (diagram == null) return;  
  
      // This handler only accepts files dragged from Windows Explorer:  
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];  
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;   
  
      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))  
      {  
        // Create an element to represent each file:  
        foreach (string fileName in draggedFileNames)  
        {  
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);  
          element.Name = fileName;  
  
          // This method of adding the new element allows the position  
          // of the shape to be specified:            
          ElementGroup group = new ElementGroup(element);  
          diagram.ElementOperations.MergeElementGroupPrototype(  
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
  
```  
  
### <a name="validation-constraints"></a>Omezení ověření  
 Metody ověřování jsou označené nástrojem `ValidationExtension` atribut, který je generována pomocí DSL a také podle <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>. Metoda může objevit v jakékoli třídy, které není označeno pomocí atributu.  
  
 Další informace najdete v tématu [ověřování v jazyka specifického pro doménu](../modeling/validation-in-a-domain-specific-language.md).  
  
```  
using Company.MyDsl;  
using Company.MyDsl.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.Validation;  
  
namespace MefExtension  
{  
  class MyValidationExtension // Can be any class.  
  {  
    // SAMPLE VALIDATION METHOD.  
    // All validation methods have the following attributes.  
  
    // Specific to the extended DSL:  
    [MyDslValidationExtension]   
  
    // Determines when validation is applied:  
    [ValidationMethod(  
       ValidationCategories.Save  
     | ValidationCategories.Open  
     | ValidationCategories.Menu)]  
  
    /// <summary>  
    /// When validation is executed, this method is invoked  
    /// for every element in the model that is an instance  
    /// of the second parameter type.  
    /// </summary>  
    /// <param name="context">For reporting errors</param>  
    /// <param name="elementToValidate"></param>  
    private void ValidateClassNames  
      (ValidationContext context,  
       // Type determines to what elements this will be applied:  
       ExampleElement elementToValidate)  
    {   
      // Write code here to test values and links.  
      if (elementToValidate.Name.IndexOf(' ') >= 0)  
      {  
        // Log any unacceptable values:  
        context.LogError(  
          // Description:  
          "Name must not contain spaces"   
          // Error code unique to this type of error:  
          , "MyDsl001"   
          // Element to highlight when user double-clicks error:  
          , elementToValidate);   
} } } }  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Rozhraní Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [Postupy: přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)



