---
title: Rozšíření vašeho DSL pomocí MEF
description: Zjistěte, jak můžete rozšířit jazyk specifický pro doménu (DSL) pomocí Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388877"
---
# <a name="extend-your-dsl-by-using-mef"></a>Rozšíření vašeho DSL pomocí MEF

Jazyk specifický pro doménu (DSL) můžete rozšířit pomocí Managed Extensibility Framework (MEF). Vy nebo jiní vývojáři budete moct psát rozšíření pro DSL beze změny definice DSL a kódu programu. Mezi tato rozšíření patří příkazy nabídky, obslužné rutiny přetahování a ověřování. Uživatelé budou moct nainstalovat váš DSL a potom pro něj volitelně nainstalovat rozšíření.

Kromě toho, když ve svém DSL povolíte MEF, může být jednodušší napsat některé funkce vašeho DSL, i když jsou všechny sestavené společně s DSL.

Další informace o MEF najdete v Managed Extensibility Framework [(MEF).](/dotnet/framework/mef/index)

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Povolení rozšíření DSL o MEF

1. V projektu **DslPackage** vytvořte **novou složku MefExtension.** Přidejte do něj následující soubory:

     Název souboru: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Nastavte identifikátor GUID v tomto souboru tak, aby byl stejný jako IDENTIFIKÁTOR GUID CommandSetId definovaný ve složce DslPackage\GeneratedCode\Constants.tt

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

    Pokud přidáte tento soubor, je nutné povolit ověřování v DSL pomocí alespoň jednoho z přepínačů **v EditoruValidation** v průzkumníku DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Název souboru: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. V projektu **Dsl** vytvořte **novou složku MefExtension.** Přidejte do něj následující soubory:

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

3. Do existujícího souboru s názvem **DslPackage\Commands.vsct** přidejte následující řádek:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Vložte řádek za existující `<Include>` direktivu.

4. Otevřete *DslDefinition.dsl*.

5. V Průzkumníku DSL vyberte **Editor\Validation.**

6. V okno Vlastnosti se ujistěte, že alespoň jedna z vlastností s názvem **Uses** je `true` .

7. Na panelu **Průzkumník řešení** klikněte na **Transformovat všechny šablony.**

     Pod každým souborem, který jste přidali, se zobrazí soubory pobočky.

8. Sestavte a spusťte řešení a ověřte, že stále funguje.

Váš DSL je teď povolený mef. Příkazy nabídky, obslužné rutiny gest a ověřovací omezení můžete psát jako rozšíření MEF. Tato rozšíření můžete napsat do řešení DSL společně s jiným vlastním kódem. Vy nebo jiní vývojáři můžete navíc psát samostatné Visual Studio rozšíření vašeho DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Vytvoření rozšíření pro DSL s podporou MEF

Pokud máte přístup k DSL s podporou MEF vytvořenému sami nebo někým jiným, můžete pro něj napsat rozšíření. Rozšíření lze použít k přidání příkazů nabídky, obslužných rutin gest nebo ověřovacích omezení. K vytváření těchto rozšíření použijete řešení Visual Studio rozšíření (VSIX). Řešení má dvě části: projekt knihovny tříd, který sestaví sestavení kódu, a projekt VSIX, který sestavení zabalíčky zabalíčky.

### <a name="to-create-a-dsl-extension-vsix"></a>Vytvoření rozšíření DSL v rozšíření VSIX

1. Vytvořte nový **projekt knihovny** tříd.

2. V novém projektu přidejte odkaz na sestavení DSL.

   - Toto sestavení má obvykle název, který končí na ".Dsl.dll".

   - Pokud máte přístup k projektu DSL, najdete soubor sestavení v adresáři **Dsl \\ Bin. \\ \***

   - Pokud máte přístup k souboru DSL VSIX, můžete sestavení najít tak, že změníte příponu názvu souboru VSIX na ".zip". Dekomprimuje .zip soubor.

3. Přidejte odkazy na následující sestavení .NET:

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Vytvořte nový projekt **VSIX.**

5. V Průzkumník řešení klikněte pravým tlačítkem na projekt VSIX **a** zvolte Nastavit jako s **úvodní projekt.**

6. V novém projektu otevřete **source.extension.vsixmanifest**.

7. Klikněte **na Přidat obsah.** V dialogovém okně nastavte **Typ obsahu** na **Součást MEF** a Zdrojový **projekt** na projekt knihovny tříd.

8. Přidejte odkaz VSIX na DSL.

   1. V **souboru source.extension.vsixmanifest klikněte** na Přidat **odkaz.**

   2. V dialogovém okně klikněte na **Přidat datovou část** a vyhledejte soubor VSIX DSL. Soubor VSIX je sestaven v řešení DSL v **přihrádce \\ \\ \* DslPackage.**

       To umožňuje uživatelům nainstalovat DSL a vaše rozšíření ve stejnou dobu. Pokud už uživatel nainstaloval DSL, nainstaluje se jenom vaše rozšíření.

9. Zkontrolujte a aktualizujte ostatní pole **source.extension.vsixmanifest**. Klikněte **na Vybrat edice** a ověřte, Visual Studio jsou nastavené správné edice.

10. Přidejte kód do projektu knihovny tříd. Jako vodítko použijte příklady v další části.

     Můžete přidat libovolný počet tříd příkazů, gest a ověřování.

11. Pokud chcete rozšíření otestovat, stiskněte **klávesu F5**. V experimentální instanci Visual Studio vytvořte nebo otevřete příklad souboru DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Psaní rozšíření MEF pro seznamy DSL

Rozšíření můžete psát v projektu kódu sestavení samostatného řešení rozšíření DSL. MEF můžete také použít ve svém projektu DslPackage jako pohodlný způsob psaní příkazů, gest a ověřovacího kódu jako součásti DSL.

### <a name="menu-commands"></a>Příkazy nabídky

Pokud chcete napsat příkaz nabídky, definujte třídu, která implementuje třídu a před ji předá atributem definovaným v <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> DSL s názvem *YourDsl* `CommandExtension` . Můžete napsat více než jednu třídu příkazů nabídky.

`QueryStatus()` se volá vždy, když uživatel klikne pravým tlačítkem na diagram. Měl by zkontrolovat aktuální výběr a nastavit tak, `command.Enabled` aby indikovat, kdy se příkaz použije.

```csharp
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

### <a name="gesture-handlers"></a>Obslužné rutiny gest

Obslužná rutina gest se může zabývat objekty přetažená do diagramu odkudkoli, uvnitř nebo Visual Studio. Následující příklad umožňuje uživateli přetáhnout soubory z Průzkumník Windows do diagramu. Vytvoří prvky, které obsahují názvy souborů.

Můžete napsat obslužné rutiny pro zpracování přetahování z jiných modelů DSL a modelů UML. Další informace najdete v tématu [Postupy: Přidání obslužné rutiny přetahování myší.](../modeling/how-to-add-a-drag-and-drop-handler.md)

```csharp
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

### <a name="validation-constraints"></a>Omezení ověřování

Metody ověřování jsou označeny `ValidationExtension` atributem, který je generován pomocí DSL, a také pomocí <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . Metoda se může objevit v jakékoli třídě, která není označena atributem.

Další informace najdete v tématu [Ověřování v jazyce Domain-Specific.](../modeling/validation-in-a-domain-specific-language.md)

```csharp
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

- [Odesílání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Postupy: Přidání obslužné rutiny operace přetažení myší](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Ověřování v jazyce specifickém pro doménu](../modeling/validation-in-a-domain-specific-language.md)
