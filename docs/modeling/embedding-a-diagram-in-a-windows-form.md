---
title: Vložení diagramu do formuláře Windows
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7afd12aa6277983f8b50eb1d7adfdd8396f8f960
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567266"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Vložení diagramu do formuláře Windows

DSL diagram můžete vložit v ovládacím prvku Windows, které se zobrazí v okně aplikace Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Vložení diagramu do DSL v ovládacím prvku Windows

1.  Přidat nový **uživatelský ovládací prvek** soubor do projektu DslPackage.

2.  Přidejte ovládací prvek Panel uživatelského ovládacího prvku. Tento panel bude obsahovat DSL Diagram.

     Přidejte další ovládací prvky, které požadujete.

     Nastavte vlastnosti ukotvení ovládacích prvků.

3.  V Průzkumníku řešení klikněte pravým tlačítkem myši na soubor uživatelského ovládacího prvku a klikněte na tlačítko **zobrazit kód**. Přidejte tento konstruktor a proměnné do kódu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4.  Přidejte nový soubor do projektu DslPackage s následujícím obsahem:

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

5.  Chcete-li otestovat DSL, stiskněte **F5** a otevření ukázkového souboru modelu. Diagramu se zobrazí uvnitř ovládacího prvku. Panelu nástrojů a dalších funkcí normálně pracovat.

## <a name="update-the-form-using-store-events"></a>Aktualizovat formulář pomocí úložiště událostí

1.  V Návrháři formulářů, přidejte **ListBox** s názvem `listBox1`. Bude se zobrazovat seznam prvků modelu. Je synchronizován s použitím modelu *uložení událostí*. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2.  V souboru vlastního kódu přepište další metody pro třídu DocView:

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

3.  V kódu uživatelského ovládacího prvku vložte metody k naslouchání pro prvky, přidat nebo odebrat:

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

4.  Chcete-li otestovat DSL, stiskněte **F5** a v experimentální instanci sady Visual Studio, otevřete ukázkový soubor modelu.

     Všimněte si, že pole se seznamem zobrazuje seznam prvků modelu a jestli je správně po jakékoli přidání nebo odstranění a zpět a znovu.

## <a name="see-also"></a>Viz také:

- [Navigace v modelu a aktualizace modelu v kódu programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
