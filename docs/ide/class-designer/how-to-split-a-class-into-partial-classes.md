---
title: Rozdělení třídy na dílčí třídy
description: Naučte se používat klíčové slovo Partial k rozdělení deklarace třídy nebo struktury mezi několik deklarací v Návrhář tříd.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d6eb6e72dc409a642dcf8e1a4c7a7389529375c7
ms.sourcegitcommit: 60e5a8a7ee91854356797d05f3b502572c4a4884
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2020
ms.locfileid: "96933516"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Postupy: rozdělení třídy na částečné třídy v Návrhář tříd

Můžete použít `partial` klíčové slovo ( `Partial` v Visual Basic) k rozdělení deklarace třídy nebo struktury mezi několika deklaracemi. Můžete použít tolik částečných deklarací, kolik chcete.

Deklarace můžou být v jednom nebo ve více zdrojových souborech. Všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.

Částečné třídy jsou užitečné v několika situacích. Ve velkém projektu, například oddělení třídy do více souborů, umožňuje více než jeden programátor pracovat na projektu současně. Když pracujete s kódem, který aplikace Visual Studio generuje, můžete změnit třídu, aniž by bylo nutné znovu vytvořit zdrojový soubor. (Příklady kódu, které Visual Studio generuje, zahrnuje model Windows Forms a kód obálky webové služby.) Můžete tedy vytvořit kód, který používá automaticky generované třídy bez nutnosti upravovat soubor, který aplikace Visual Studio vytvoří.

Existují dva druhy částečných metod. V jazyce C# se nazývají deklarace a implementace; v Visual Basic se nazývají deklarace a implementace.

**Návrhář tříd** podporuje částečné třídy a metody. Tvar typu v diagramu tříd odkazuje na jedno umístění deklarace pro částečnou třídu. Je-li částečná třída definována ve více souborech, můžete určit, která umístění deklarace **Návrhář tříd** bude použita, nastavením vlastnosti **umístění nového člena** v okně **vlastnosti** . To znamená, že když dvakrát kliknete na obrazec třídy, **Návrhář tříd** přejde ke zdrojovému souboru, který obsahuje deklaraci třídy identifikovanou vlastností **umístění nového člena** . Když dvakrát kliknete na částečnou metodu v obrazci třídy, **Návrhář tříd** přejít k deklaraci částečné metody. V okně **vlastnosti** také odkazuje vlastnost **název souboru** na umístění deklarace. Pro částečné třídy, **název souboru** obsahuje seznam všech souborů, které obsahují deklaraci a implementační kód pro danou třídu. U částečných metod však **název souboru** obsahuje pouze soubor, který obsahuje deklaraci částečné metody.

V následujících příkladech je rozdělena definice třídy `Employee` do dvou deklarací, z nichž každá definuje jiný postup. Dvě částečné definice v příkladech mohou být v jednom zdrojovém souboru nebo ve dvou různých zdrojových souborech.

> [!NOTE]
> Visual Basic používá definice částečné třídy pro oddělení kódu generovaného pomocí sady Visual Studio od uživatelsky vytvořeného kódu. Kód je rozdělen do diskrétních zdrojových souborů. Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako například `Form` . V těchto ovládacích prvcích byste neměli upravovat generovaný kód.

Další informace o částečných typech v Visual Basic naleznete v tématu [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Příklad

Chcete-li rozdělit definici třídy, použijte `partial` klíčové slovo ( `Partial` v Visual Basic), jak je znázorněno v následujícím příkladu:

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

- [Částečné třídy a metody](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [Partial (typ) (Referenční dokumentace jazyka C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [Partial (metoda) (Referenční dokumentace jazyka C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
