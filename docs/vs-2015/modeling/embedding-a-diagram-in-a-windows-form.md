---
title: Vložení diagramu do formuláře Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 04ecf5bd7bfc91e03f48e624d208a5b4f29b10b7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292523"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Vložení diagramu do formuláře Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL diagram můžete vložit v ovládacím prvku Windows, která je zobrazená [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna.  
  
## <a name="embedding-a-diagram"></a>Vložení diagramu do  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Chcete-li vložit DSL diagram v ovládacím prvku Windows  
  
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
    private MyDSLDSLDocView docView;  
  
    ```  
  
4.  Přidejte nový soubor do projektu DslPackage s následujícím obsahem:  
  
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
  
5.  K otestování DSL, stiskněte klávesu F5 a otevření ukázkového souboru modelu. Diagramu se zobrazí uvnitř ovládacího prvku. Panelu nástrojů a dalších funkcí normálně pracovat.  
  
#### <a name="updating-the-form-using-store-events"></a>Aktualizace na formulář pomocí možnosti Store události  
  
1.  V Návrháři formulářů, přidejte **ListBox** s názvem `listBox1`. Bude se zobrazovat seznam prvků modelu. Se zachovají v synchronism pomocí modelu *uložení událostí*. Další informace najdete v tématu [obslužné rutiny rozšíření změny mimo the Model událostí](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2.  V souboru vlastního kódu přepište další metody pro třídu DocView:  
  
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
  
3.  V kódu uživatelského ovládacího prvku vložte metody k naslouchání pro prvky, přidat nebo odebrat:  
  
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
  
4.  K otestování DSL, stiskněte klávesu F5 a v experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otevřete ukázkový soubor modelu.  
  
     Všimněte si, že pole se seznamem zobrazuje seznam prvků modelu a jestli je správně po jakékoli přidání nebo odstranění a zpět a znovu.  
  
## <a name="see-also"></a>Viz také  
 [Procházení a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Zápis kódu pro úpravu jazyka specifického pro doménu](../modeling/writing-code-to-customise-a-domain-specific-language.md)

