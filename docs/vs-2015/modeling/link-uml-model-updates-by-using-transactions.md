---
title: Propojení aktualizací modelu UML pomocí transakcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb8bb5dfd5238871324b786f120d618d70f14b43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800403"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Propojení aktualizací modelu UML pomocí transakcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při definování rozšíření do návrhářů UML v sadě Visual Studio, můžete seskupit několik změn do jediné transakce s názvem *propojená operace vrácení zpět kontext*. Pokud chcete zobrazit, které verze sady Visual Studio podporují modelech UML, naleznete v tématu [podporované verze pro nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Ve výchozím nastavení mohou být všechny změny, které provede v kódu modelu samostatně anulovány uživatelem. Například pokud definujete příkaz nabídky, který zaměňuje názvy dvou tříd modelu UML, uživatel může vyvolat příkaz a poté provést jedno vrácení zpět. To by vrátilo zpět změnu jednoho názvu, ale nikoli u druhého, čímž zůstane váš model v nežádoucího stavu.  
  
 Abyste tomu předešli, váš kód může provést řadu změn v rámci transakce. Díky tomu změny jako jediné změny uživateli. Následný příkaz zrušení vrátí zpět celou řadu.  
  
 Další výhodou je, že váš kód může vrátit zpět částečně dokončené sady změn vyvoláním výjimky nebo přerušením transakce.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Seskupení změn do jediné transakce  
 Zajistěte, aby že projekt odkazy zahrnoval tento sestavení .NET:  
  
 **Microsoft.VisualStudio.Modeling.Sdk. DLL [verze]**  
  
 Uvnitř své třídy deklarujte importovanou vlastnost, která má typ <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 V metodě, která upravuje model uzavřete změny v transakci:  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Všimněte si následujícího:  
  
-   Musí vždy zahrnovat `Commit()` na konci transakce. Pokud je transakce vyřazena bez potvrzení, transakce bude vrácena zpět. To znamená, že model se obnoví do stavu při zahájení transakce.  
  
-   Pokud dojde k výjimce, která není zachycena uvnitř transakce, transakce bude vrácena zpět. Je časté vzor k uzavření `using` transakce dovnitř bloku `try…catch` bloku.  
  
-   Můžete vnořovat transakce.  
  
-   Můžete zadat libovolný neprázdný název a `BeginTransaction()`.  
  
-   Tyto transakcemi má vliv pouze Store modelu UML. Modelování transakci nemá vliv: proměnné, externí úložiště, jako jsou soubory a databáze, diagramy vrstev a modely kódu.  
  
## <a name="example"></a>Příklad  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>Viz také  
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md)   
 [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Rozšíření modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)



