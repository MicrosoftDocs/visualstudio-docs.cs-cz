---
title: Vložení diagramu do formuláře Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 487105350fe5c62a9451bccc5713c6506c76bf1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669693"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Vložení diagramu do formuláře Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram DSL můžete vložit do ovládacího prvku systému Windows, který se zobrazí v okně [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="embedding-a-diagram"></a>Vložení diagramu

#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Vložení diagramu DSL do ovládacího prvku Windows

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
    private MyDSLDSLDocView docView;

    ```

4. Přidejte nový soubor do projektu DslPackage s následujícím obsahem:

    ```
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

5. Chcete-li otestovat DSL, stiskněte klávesu F5 a otevřete ukázkový soubor modelu. Diagram se zobrazí uvnitř ovládacího prvku. Sada nástrojů a další funkce pracují normálně.

#### <a name="updating-the-form-using-store-events"></a>Aktualizace formuláře pomocí událostí úložiště

1. V návrháři formuláře přidejte **seznam** s názvem `listBox1`. Tím se zobrazí seznam elementů v modelu. Bude se uchovávat v synchronism s modelem pomocí *událostí úložiště*. Další informace najdete v tématu [obslužné rutiny událostí rozšiřovat změny mimo model](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. V souboru vlastního kódu přepište další metody do třídy objekt DocView:

    ```

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

    ```

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

4. Chcete-li otestovat DSL, stiskněte klávesu F5 a v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otevřete vzorový soubor modelu.

     Všimněte si, že seznam obsahuje seznam prvků v modelu a že je správný po přidání nebo odstranění a po vrácení a opakování.

## <a name="see-also"></a>Viz také
 [Navigace a aktualizace modelu v psaní kódu programového kódu](../modeling/navigating-and-updating-a-model-in-program-code.md) [pro přizpůsobení jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)
