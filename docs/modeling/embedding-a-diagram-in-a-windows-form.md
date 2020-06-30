---
title: Vložení diagramu do formuláře Windows
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e81a5ff10cd6e309ffbf17e40ffbaa9ec88f185
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547625"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Vložení diagramu do formuláře Windows

Diagram DSL lze vložit do ovládacího prvku systému Windows, který se zobrazí v okně aplikace Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Vložení diagramu DSL do ovládacího prvku Windows

1. Přidejte do projektu DslPackage nový soubor **uživatelského ovládacího prvku** .

2. Přidejte ovládací prvek panel do uživatelského ovládacího prvku. Tento panel bude obsahovat diagram DSL.

     Přidejte další ovládací prvky, které požadujete.

     Nastavte vlastnosti kotvy ovládacích prvků.

3. V Průzkumník řešení klikněte pravým tlačítkem myši na soubor uživatelského ovládacího prvku a klikněte na možnost **Zobrazit kód**. Přidejte tento konstruktor a proměnnou do kódu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Přidejte nový soubor do projektu DslPackage s následujícím obsahem:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Chcete-li otestovat DSL, stiskněte klávesu **F5** a otevřete ukázkový soubor modelu. Diagram se zobrazí uvnitř ovládacího prvku. Sada nástrojů a další funkce pracují normálně.

## <a name="update-the-form-using-store-events"></a>Aktualizace formuláře pomocí událostí úložiště

1. V návrháři formuláře přidejte **seznam** s názvem `listBox1` . Tím se zobrazí seznam elementů v modelu. Je synchronizován s modelem pomocí *událostí úložiště*. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. V souboru vlastního kódu přepište další metody do třídy objekt DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. Do kódu za uživatelským ovládacím prvkem vložte metody pro poslech přidaných a odebraných prvků:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. K otestování DSL stiskněte klávesu **F5** a v experimentální instanci sady Visual Studio otevřete vzorový soubor modelu.

     Všimněte si, že seznam obsahuje seznam prvků v modelu a že je správný po přidání nebo odstranění a po vrácení a opakování.

## <a name="see-also"></a>Viz také

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
