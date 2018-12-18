---
title: Definování obslužné rutiny odkazu pracovní položky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7ce74627d1d2d48ab02e0b124fbc38949f1f76f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733070"
---
# <a name="define-a-work-item-link-handler"></a>Definování obslužné rutiny odkazu pracovní položky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vytvořit rozšíření integrace sady Visual Studio, který reaguje, když uživatel vytvoří nebo odstraní spojení mezi prvkem modelu UML a pracovní položky. Například když se uživatel rozhodne novou pracovní položku propojit prvek modelu, váš kód může inicializovat pole pracovní položky z hodnot v modelu.  
  
## <a name="set-up-a-uml-extension-solution"></a>Nastavte řešení rozšíření UML  
 To vám umožní vyvíjet obslužné rutiny a pak je distribuovat ostatním uživatelům. Budete muset nastavit dva projekty sady Visual Studio:  
  
-   Projekt knihovny tříd obsahující kód obslužné rutiny odkazu.  
  
-   Projekt VSIX, který funguje jako kontejner pro instalaci příkazu. Pokud chcete, můžete zahrnout další součásti do stejného VSIX.  
  
#### <a name="to-set-up-the-visual-studio-solution"></a>Nastavit řešení sady Visual Studio  
  
1.  Vytvořte projekt knihovny tříd, jeho přidání do existujícího VSIX řešení nebo vytvoření nového řešení.  
  
    1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**, v prostředním sloupci klikněte na tlačítko **knihovny tříd**.  
  
    3.  Nastavte **řešení** označující, zda chcete vytvořit nové řešení nebo přidat součást do řešení VSIX, který jste již otevřeli.  
  
    4.  Nastavte projekt název a umístění a klikněte na tlačítko OK.  
  
2.  Pokud ho vaše řešení již neobsahuje, vytvořte projekt VSIX.  
  
    1.  V **Průzkumníka řešení**, v místní nabídce řešení zvolte **přidat**, **nový projekt**.  
  
    2.  V části **nainstalované šablony**, rozbalte **Visual C#** nebo **jazyka Visual Basic**a pak vyberte **rozšiřitelnost**. V prostředním sloupci zvolte **projekt VSIX**.  
  
3.  Nastavte projekt VSIX jako projekt po spuštění řešení.  
  
    -   V Průzkumníku řešení v místní nabídce projektu VSIX zvolte **nastavit jako spouštěný projekt**.  
  
4.  V **source.extension.vsixmanifest**v části **obsahu**, přidejte projekt knihovny tříd jako komponentu MEF.  
  
    1.  Na **metadat** kartu, nastavte název souboru VSIX.  
  
    2.  Na **cíle instalace** kartu, nastavte verze sady Visual Studio jako cíle.  
  
    3.  Na **prostředky** kartě **nový**a v dialogovém okně nastavte:  
  
         **Typ** = **Komponenta MEF**  
  
         **Zdroj** = **projekt v aktuálním řešení**  
  
         **Projekt** = *váš projekt knihovny tříd*  
  
## <a name="defining-the-work-item-link-handler"></a>Definování obslužné rutiny odkazu pracovní položky  
 Všechny tyto úlohy proveďte v projektu knihovny tříd.  
  
### <a name="project-references"></a>Odkazy na projekt  
 Přidejte následující [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] sestavení do odkazů projektu:  
  
 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`  
  
 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`  
  
 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`  
  
 `Microsoft.VisualStudio.Uml.Interfaces`  
  
 `System.ComponentModel.Composition`  
  
 `System.Drawing` – používá ukázkový kód  
  
 Pokud nelze najít jeden z těchto odkazů pod **.Net** kartě **přidat odkaz** dialogové okno, pomocí karty Procházet jej najděte ve \Common7\IDE\ \Program Files\Microsoft sady Visual Studio [verze] PrivateAssemblies\\.  
  
### <a name="import-the-work-item-namespace"></a>Import Namespace pracovní položky  
 Ve vaší [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu **odkazy**, přidejte odkazy na následující sestavení:  
  
- Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll  
  
  Ve svém kódu programu importujte následující obory názvů:  
  
```  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;  
using System.Linq;  
```  
  
### <a name="define-the-linked-work-item-event-handler"></a>Definovat obslužnou rutinu události propojené pracovní položky  
 Přidejte soubor třídy do projektu knihovny tříd a nastavte jeho obsah následujícím způsobem. Změňte název oboru názvů a třídy dle.  
  
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
 Pro účely testování spusťte obslužnou rutina odkazu v režimu ladění.  
  
> [!WARNING]
>  Musíte už být připojení k TFS zdrojového kódu ovládacího prvku (SCC) vytvořit nebo propojit s pracovní položkou. Pokud se pokusíte otevřít připojení k jiné SCC TFS, Visual Studio automaticky zavře aktuální řešení. Ujistěte se, že jste již připojeni k příslušné SCC než se pokusíte vytvořit nebo propojit s pracovní položkou. V pozdějších verzích sady Visual Studio příkazy nabídky nejsou k dispozici v případě, že nejste připojeni k SCC.  
  
#### <a name="to-test-the-link-handler"></a>Testování obslužné rutiny odkazu  
  
1.  Stisknutím klávesy **F5**, nebo **ladění** nabídce zvolte **spustit ladění**.  
  
     Experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] spustí.  
  
     **Řešení potíží s**: Pokud se nová [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nespustí, ujistěte se, že projekt VSIX je nastaven jako projekt po spuštění řešení.  
  
2.  V experimentální instanci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]otevřete nebo vytvořte projekt modelování a otevřete nebo vytvořte diagram modelování.  
  
3.  Vytvořte element modelu, jako je třída UML a nastavte jeho jméno.  
  
4.  Klikněte pravým tlačítkem na prvek a potom klikněte na tlačítko **vytvořit pracovní položku**.  
  
    -   Pokud podnabídka zobrazí **otevřít připojení k Team Foundation serveru**, budete muset zavřít projekt se připojte k příslušné sady TFS a restartujte tento postup.  
  
    -   Pokud dílčí nabídka zobrazí seznam typů pracovních položek, klikněte na jednu.  
  
         Otevře se formulář nové pracovní položky.  
  
5.  Ověřte, zda název pracovní položky je stejný jako prvek modelu, pokud jste použili ukázkový kód v předchozí části. Tento příklad ukazuje `OnWorkItemCreated()` pracoval.  
  
6.  Vyplňte formulář, uložte a zavřete pracovní položku.  
  
7.  Ověřte, že je pracovní položka nyní zbarvena červeně. Tento příklad ukazuje `OnWorkItemLinked()` ve vzorovém kódu.  
  
     **Řešení potíží s**: Pokud se metody obslužné rutiny nespustily, zkontrolujte, zda:  
  
    -   Projekt knihovny tříd je uveden jako Komponenta MEF na **obsahu** seznamu v **source.extensions.manifest** v projektu VSIX.  
  
    -   Správné `Export` je připojena ke třídě obslužné rutiny a třída implementuje `ILinkedWorkItemExtension`.  
  
    -   Parametry všech vlastností `Import` a `Export` jsou platné.  
  
## <a name="about-the-work-item-handler-code"></a>O kódu obslužné rutiny pracovní položky  
  
### <a name="listening-for-new-work-items"></a>Poslouchání nových pracovních položek  
 `OnWorkItemCreated` je volána, když uživatel zvolí vytvoření nové pracovní položky spojen s prvky modelu. Váš kód může inicializovat pole pracovní položky. Pracovní položka je pak budou zobrazena uživateli, který můžete aktualizovat pole a uložení pracovní položky. Odkaz na prvek modelu není vytvořen, dokud pracovní položky se úspěšně uložily.  
  
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
  
### <a name="listening-for-link-creation"></a>Poslouchání vytvoření propojení  
 `OnWorkItemLinked` je volána hned po vytvoření propojení. Je volána, zda je odkaz na novou pracovní položku nebo existující položky. Se volá jednou pro každou pracovní položku.  
  
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
>  Chcete-li tento příklad fungoval, musíte přidat odkaz na projekt `System.Drawing.dll`a importovat obor názvů `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation`. Tyto doplňky však nejsou požadována pro jiné implementace `OnWorkItemLinked`.  
  
### <a name="listening-for-link-removal"></a>Poslouchání odstranění propojení  
 `OnWorkItemRemoved` je volána těsně před každý odkaz na pracovní položku, která je odstraňována. Pokud odstranění prvku modelu budou odebrány všechny odkazy.  
  
```  
public void OnWorkItemRemoved  
         (IElement element, string serverUri, int workItemId)  
{...}  
```  
  
## <a name="updating-a-work-item"></a>Aktualizace pracovní položky  
 Pomocí oborů názvů Team Foundation, můžete pracovat s pracovní položkou.  
  
 Pokud chcete použít v následujícím příkladu, přidejte tato sestavení .NET do odkazů vašeho projektu:  
  
-   Microsoft.TeamFoundation.Client.dll  
  
-   Microsoft.TeamFoundation.WorkItemTracking.Client.dll  
  
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
  
## <a name="accessing-the-work-item-reference-links"></a>Přístup k odkazům pracovní položky  
 Odkazy je možné otevřít následujícím způsobem:  
  
```  
//Get:  
string linkString = element.GetReference(ReferenceConstants.WorkItem);  
// Set:  
element.AddReference(ReferenceConstants.WorkItem, linkString, true);  
  
```  
  
 Formát `linkString` je:  
  
 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`  
  
 kde:  
  
- Identifikátor URI serveru bude:  
  
   `http://tfServer:8080/tfs/projectCollection`  
  
   Je důležité v případě `projectCollection`.  
  
- `RepositoryGuid` můžete získat z připojení TFS:  
  
  ```csharp  
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;  
  RepositoryGuid= tpc.InstanceId;  
  
  ```  
  
  Další informace o referencích naleznete v tématu [připojení referenčních řetězců k UML model prvky](../modeling/attach-reference-strings-to-uml-model-elements.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.TeamFoundation.WorkItemTracking.Client.WorkItemStore?displayProperty=fullName>   
 [Propojení prvků modelu a pracovních položek](../modeling/link-model-elements-and-work-items.md)   
 [Připojení referenčních řetězců k prvkům modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)   
 [Definování a instalace rozšíření modelování](../modeling/define-and-install-a-modeling-extension.md)   
 [Programování pomocí rozhraní API UML](../modeling/programming-with-the-uml-api.md)



