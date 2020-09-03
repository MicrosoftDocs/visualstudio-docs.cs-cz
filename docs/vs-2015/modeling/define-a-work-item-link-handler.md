---
title: Definovat obslužnou rutinu propojení pracovní položky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 380aaa5bed1e30c549334bc004ea38e3f0bdb762
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669926"
---
# <a name="define-a-work-item-link-handler"></a>Definování obslužné rutiny odkazu pracovní položky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit integrační rozšíření sady Visual Studio, které reaguje, když uživatel vytvoří nebo odstraní propojení mezi prvkem modelu UML a pracovní položkou. Například když se uživatel rozhodne propojit novou pracovní položku s prvkem modelu, váš kód může inicializovat pole pracovní položky z hodnot v modelu.

## <a name="set-up-a-uml-extension-solution"></a>Nastavení řešení rozšíření UML
 To vám umožní vyvíjet obslužné rutiny a pak je distribuovat dalším uživatelům. Musíte nastavit dva projekty sady Visual Studio:

- Projekt knihovny tříd obsahující kód obslužné rutiny odkazu

- Projekt VSIX, který slouží jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další komponenty do stejného VSIX.

#### <a name="to-set-up-the-visual-studio-solution"></a>Nastavení řešení v sadě Visual Studio

1. Vytvořte projekt knihovny tříd, buď jej přidejte do stávajícího řešení VSIX, nebo vytvořte nové řešení.

    1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

    2. V části **Nainstalované šablony**rozbalte položku **Visual C#** nebo **Visual Basic**a potom v prostředním sloupci klikněte na **Knihovna tříd**.

    3. Nastavte **řešení** tak, aby označovalo, zda chcete vytvořit nové řešení nebo přidat komponentu do řešení VSIX, které jste již otevřeli.

    4. Nastavte název projektu a umístění a klikněte na tlačítko OK.

2. Vytvořte projekt VSIX, pokud ho vaše řešení ještě neobsahuje.

    1. V **Průzkumník řešení**v místní nabídce řešení vyberte možnost **Přidat**, **Nový projekt**.

    2. V části **Nainstalované šablony**rozbalte položku **Visual C#** nebo **Visual Basic**a potom vyberte možnost **rozšiřitelnost**. V prostředním sloupci vyberte **projekt VSIX**.

3. Nastavte projekt VSIX jako projekt po spuštění řešení.

    - V Průzkumník řešení v místní nabídce projektu VSIX vyberte **nastavit jako spouštěný projekt**.

4. V části **source. extension. vsixmanifest**v části **obsah**přidejte projekt knihovny tříd jako komponentu MEF.

    1. Na kartě **metadata** nastavte název VSIX.

    2. Na kartě **cíle instalace** nastavte jako cíle verze sady Visual Studio.

    3. Na kartě **assets (prostředky** ) vyberte **Nový**a v dialogovém okně nastavte:

         **Typ**  =  **Komponenta MEF**

         **Zdroj**  =  **Projekt v aktuálním řešení**

         **Projekt**  =  *Váš projekt knihovny tříd*

## <a name="defining-the-work-item-link-handler"></a>Definování obslužné rutiny propojení pracovní položky
 Proveďte všechny následující úkoly v projektu knihovny tříd.

### <a name="project-references"></a>Odkazy na projekty
 [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)]Do odkazů projektu přidejte následující sestavení:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing` – používá se v ukázkovém kódu

 Pokud některý z těchto odkazů nemůžete najít na kartě **.NET** v dialogovém okně **Přidat odkaz** , najděte ho pomocí karty Procházet ve složce \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies \\ .

### <a name="import-the-work-item-namespace"></a>Importovat obor názvů pracovní položky
 V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **odkazech**na projekt přidejte odkazy na následující sestavení:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  V kódu programu importujte následující obory názvů:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Definice obslužné rutiny události propojené pracovní položky
 Přidejte soubor třídy do projektu knihovny tříd a nastavte jeho obsah následujícím způsobem. Změňte název oboru názvů a třídy na libovolný, co dáváte přednost.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Testování obslužné rutiny odkazu
 Pro účely testování spusťte obslužnou rutinu propojení v režimu ladění.

> [!WARNING]
> Aby bylo možné vytvořit nebo propojit pracovní položku, musíte být již připojeni ke správě zdrojového kódu TFS (SCC). Pokud se pokusíte otevřít připojení k jinému SCC TFS, Visual Studio automaticky zavře aktuální řešení. Před pokusem o vytvoření nebo propojení pracovní položky se ujistěte, že jste již připojeni k odpovídajícímu SCC. V novějších verzích sady Visual Studio nejsou příkazy nabídky k dispozici, pokud nejste připojeni k SCC.

#### <a name="to-test-the-link-handler"></a>Testování obslužné rutiny odkazu

1. Stiskněte klávesu **F5**nebo v nabídce **ladění** zvolte možnost **Spustit ladění**.

     Spustí se experimentální instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Řešení potíží**: Pokud se nový [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí, ujistěte se, že projekt VSIX je nastaven jako spouštěný projekt řešení.

2. V experimentální [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování.

3. Vytvořte prvek modelu, jako je třída UML, a nastavte jeho název.

4. Klikněte pravým tlačítkem na prvek a pak klikněte na **vytvořit pracovní položku**.

    - Pokud se v podnabídce zobrazuje **otevření Team Foundation Server připojení**, bude nutné projekt zavřít, připojit se k příslušnému serveru TFS a tento postup restartovat.

    - Pokud se v podnabídce zobrazuje seznam typů pracovních položek, klikněte na jednu.

         Otevře se formulář nové pracovní položky.

5. Ověřte, zda je název pracovní položky stejný jako prvek modelu, pokud jste použili vzorový kód v předchozí části. Tento příklad ukazuje `OnWorkItemCreated()` , že pracoval.

6. Vyplňte formulář a uložte a zavřete pracovní položku.

7. Ověřte, zda je pracovní položka nyní barevná a červená. To ukazuje `OnWorkItemLinked()` vzorový kód.

     **Řešení potíží**: Pokud se obslužné rutiny nespouštějí, ověřte, že:

    - Projekt knihovny tříd je uveden jako Komponenta MEF v seznamu **obsahu** v souboru **source. Extensions. manifest** v projektu VSIX.

    - Správný `Export` atribut je připojen ke třídě obslužné rutiny a třída implementuje `ILinkedWorkItemExtension` .

    - Parametry všech `Import` `Export` atributů a jsou platné.

## <a name="about-the-work-item-handler-code"></a>O kódu obslužné rutiny pracovní položky

### <a name="listening-for-new-work-items"></a>Poslouchání nových pracovních položek
 `OnWorkItemCreated` se volá, když se uživatel rozhodne vytvořit novou pracovní položku, která se má propojit s prvky modelu. Váš kód může inicializovat pole pracovní položky. Pracovní položka je pak prezentována uživateli, který může aktualizovat pole a uložit pracovní položku. Odkaz na prvek modelu není vytvořen, dokud nebude pracovní položka úspěšně uložena.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Naslouchání vytvoření odkazu
 `OnWorkItemLinked` se volá hned po vytvoření odkazu. Nazývá se to, zda je odkaz na novou pracovní položku nebo existující položku. Je volána jednou pro každou pracovní položku.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Chcete-li tento příklad fungovat, je nutné přidat odkaz na projekt `System.Drawing.dll` a importovat obor názvů `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation` . Nicméně tyto dodatky nejsou vyžadovány pro jiné implementace nástroje `OnWorkItemLinked` .

### <a name="listening-for-link-removal"></a>Naslouchání odebrání odkazu
 `OnWorkItemRemoved` je volána jednou před každým odstraněným odkazem pracovní položky. Pokud je prvek modelu odstraněn, budou všechny jeho odkazy odebrány.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>Aktualizace pracovní položky
 Pomocí oborů názvů Team Foundation můžete manipulovat s pracovní položkou.

 Chcete-li použít následující příklad, přidejte tato sestavení .NET do odkazů projektu:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Přístup k odkazům na pracovní položky
 K odkazům můžete přistupovat následujícím způsobem:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 Formát `linkString` je:

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 kde:

- Identifikátor URI vašeho serveru by byl:

   `http://tfServer:8080/tfs/projectCollection`

   Případ je důležitý v `projectCollection` .

- `RepositoryGuid` lze získat z připojení TFS:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Další informace o odkazech naleznete v tématu [připojení referenčních řetězců k prvkům modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Viz také

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)
- [Připojení referenčních řetězců k elementům modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)
- [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)
