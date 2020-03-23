---
title: 'Postupy: Rozdělení třídy na částečné třídy (návrhář tříd)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 48672e2d316828019ede7097306517b270062327
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588678"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Postup: Rozdělení třídy na částečné třídy v Návrháři tříd

Klíčové `partial` slovo (`Partial` v jazyce Visual Basic) můžete rozdělit deklaraci třídy nebo struktury mezi několik deklarací. Můžete použít libovolný počet částečných deklarací.

Deklarace mohou být v jednom nebo ve více zdrojových souborech. Všechny deklarace musí být ve stejném sestavení a ve stejném oboru názvů.

Částečné třídy jsou užitečné v několika situacích. Například na velkém projektu, například oddělení třídy do více souborů umožňuje více než jeden programátor pracovat na projektu současně. Při práci s kódem, který generuje Visual Studio, můžete změnit třídu bez nutnosti znovu vytvořit zdrojový soubor. (Příklady kódu, který generuje Visual Studio patří Windows Forms a obálka webové služby kód.) Můžete tedy vytvořit kód, který používá automaticky generované třídy bez nutnosti měnit soubor, který vytvoří Visual Studio.

Existují dva druhy částečných metod. V C#se nazývají deklarování a implementace; v jazyce Visual Basic se nazývají deklarace a implementace.

**Návrhář tříd** podporuje částečné třídy a metody. Obrazec typu v diagramu třídy odkazuje na jedno umístění deklarace pro částečnou třídu. Pokud je částečná třída definována ve více souborech, můžete určit, které umístění deklarace **Návrhář třídy** použije, nastavením vlastnosti **Nové umístění člena** v okně **Vlastnosti.** To znamená, že když poklepete na obrazec **třídy, Návrhář třídy** přejde do zdrojového souboru, který obsahuje deklaraci třídy identifikovanou vlastností **New Member Location.** Když poklepete na částečnou metodu ve tvaru **třídy, Návrhář třídy** přejde na deklaraci částečné metody. Také v okně **Vlastnosti** vlastnost i vlastnost **Název souboru** odkazuje na umístění deklarace. Pro částečné třídy **název souboru** uvádí všechny soubory, které obsahují deklarace a kód implementace pro tuto třídu. Pro částečné metody však **název souboru** uvádí pouze soubor, který obsahuje deklaraci částečné metody.

Následující příklady rozdělit definici `Employee` třídy do dvou deklarací, z nichž každá definuje jiný postup. Dvě částečné definice v příkladech může být v jednom zdrojovém souboru nebo ve dvou různých zdrojových souborů.

> [!NOTE]
> Visual Basic používá definice částečné třídy k oddělení kódu generovaného aplikací Visual Studio od kódu vytvořeného uživatelem. Kód je rozdělen na samostatné zdrojové soubory. **Návrhář formulářů systému Windows** například definuje `Form`částečné třídy pro ovládací prvky, jako je například . V těchto ovládacích prvcích byste neměli upravovat generovaný kód.

Další informace o částečných typech v jazyce Visual Basic naleznete v [tématu Partial](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Příklad

Chcete-li rozdělit definici `partial` třídy, použijte klíčové slovo (`Partial` v jazyce Visual Basic), jak je znázorněno v následujícím příkladu:

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="see-also"></a>Viz také

- [Dílčí třídy a metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [částečné (typ) (C# Reference)](/dotnet/csharp/language-reference/keywords/partial-type)
- [částečné (metoda) (C# Reference)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
