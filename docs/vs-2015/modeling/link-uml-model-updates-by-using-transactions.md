---
title: Propojení aktualizací modelu UML pomocí transakcí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8930bba76830a6116c3182f3fb2936cd4f1a3e47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657598"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Propojení aktualizací modelu UML pomocí transakcí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při definování rozšíření pro návrháře UML v aplikaci Visual Studio můžete seskupit několik změn do jedné transakce *s názvem propojený kontext zpět*. Chcete-li zjistit, které verze aplikace Visual Studio podporují modely UML, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Ve výchozím nastavení každá změna, kterou váš kód vede k modelu, může být samostatně vrácena uživatelem. Například pokud definujete příkaz nabídky, který zamění názvy dvou tříd UML, může uživatel vyvolat příkaz a pak provést jediné zrušení. To by vrátilo zpět změnu k jednomu názvu, ale ne k druhému, takže model zůstane v nezamýšleném stavu.

 Aby k tomu nedocházelo, váš kód může provést řadu změn v rámci transakce. Změny tak budou vypadat jako jedna změna pro uživatele. Následný příkaz zpět vrátí celou řadu zpět.

 Další výhodou je, že váš kód může vrátit zpět částečně kompletní sadu změn vyvoláním výjimky nebo přerušením transakce.

## <a name="to-group-changes-into-a-single-transaction"></a>Seskupení změn do jedné transakce
 Zajistěte, aby vaše odkazy na projekt zahrnovaly toto sestavení .NET:

 **Microsoft. VisualStudio. Modeling. SDK. [Version]. dll**

 V rámci třídy deklarujte importovanou vlastnost, která má typ <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> :

 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`

 `...`

 `class … {`

 `[Import]`

 `public ILinkedUndoContext LinkedUndoContext { get; set; }`

 V metodě, která upravuje model, vložte své změny do transakce:

 `using (ILinkedUndoTransaction transaction =`

 `LinkedUndoContext.BeginTransaction("my updates"))`

 `{`

 `// code to update model elements or shapes goes here`

 `transaction.Commit();`

 `}`

 Všimněte si následujícího:

- Vždy je nutné zahrnout `Commit()` na konci transakce. Pokud je transakce vyřazena bez potvrzení, transakce bude vrácena zpět. To znamená, že model bude obnoven do svého stavu na začátku transakce.

- Pokud dojde k výjimce, která není zachycena uvnitř transakce, transakce bude vrácena zpět. Je častým vzorem pro uzavření `using` bloku transakce dovnitř `try…catch` bloku.

- Můžete vnořovat transakce.

- Můžete zadat libovolný neprázdný název `BeginTransaction()` .

- Tyto transakce má vliv pouze na úložiště modelu UML. Transakce modelování neovlivňují: proměnné, externí obchody, jako jsou soubory a databáze, diagramy vrstev a modely kódu.

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
 [Programování s rozhraním API UML](../modeling/programming-with-the-uml-api.md) [definuje příkaz nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [, který rozšiřuje modely a diagramy UML](../modeling/extend-uml-models-and-diagrams.md) .
