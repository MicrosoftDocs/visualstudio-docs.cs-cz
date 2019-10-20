---
title: 'Postupy: rozdělení třídy na částečné třídy (Návrhář tříd) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e93ebc58e4e9b6092921e4155fe3d821bb552c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670706"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Postupy: Rozdělení třídy na částečné třídy (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete rozdělit deklaraci třídy nebo struktury mezi několik deklarací pomocí klíčového slova `Partial` v Visual Basic nebo klíčového slova `partial` ve vizuálu C#. Můžete použít libovolný počet částečných deklarací, v kolika různých zdrojových souborech chcete, nebo v jednom zdrojovém souboru. Nicméně všechny deklarace musí být ve stejném sestavení a stejném oboru názvů.

 Částečné třídy jsou užitečné v několika situacích. Například při práci na velkých projektech, oddělení třídy na více než jeden soubor umožňuje více než jeden programátor pracovat současně. Když pracujete s kódem, který aplikace Visual Studio generuje, můžete změnit třídu, aniž by bylo nutné znovu vytvořit zdrojový soubor. (Příklady kódu, které Visual Studio generuje, zahrnuje model Windows Forms a kód obálky webové služby.) Můžete tedy vytvořit kód, který používá automaticky generované třídy bez nutnosti upravovat soubor, který aplikace Visual Studio vytvoří.

 Existují dva druhy částečných metod. V jazyce C#Visual se nazývají deklarace a implementace; v Visual Basic se nazývají deklarace a implementace.

 Návrhář tříd podporuje částečné třídy a metody. Tvar typu v diagramu tříd odkazuje na jedno umístění deklarace pro částečnou třídu. Je-li částečná třída definována ve více souborech, můžete určit, která umístění deklarace Návrhář tříd bude použita, nastavením vlastnosti **umístění nového člena** v okně **vlastnosti** . To znamená, že když dvakrát kliknete na obrazec třídy, Návrhář tříd přejde ke zdrojovému souboru, který obsahuje deklaraci třídy identifikovanou vlastností **umístění nového člena** . Když dvakrát kliknete na částečnou metodu v obrazci třídy, Návrhář tříd přejít k deklaraci částečné metody. V okně **vlastnosti** také odkazuje vlastnost **název souboru** na umístění deklarace. Pro částečné třídy, **název souboru** obsahuje seznam všech souborů, které obsahují deklaraci a implementační kód pro danou třídu. U částečných metod však **název souboru** obsahuje pouze soubor, který obsahuje deklaraci částečné metody.

 V následujících příkladech je rozdělena definice třídy `Employee` do dvou deklarací, z nichž každá definuje jiný postup. Dvě částečné definice v příkladech mohou být v jednom zdrojovém souboru nebo ve dvou různých zdrojových souborech.

> [!NOTE]
> Visual Basic používá definice částečné třídy pro oddělení sady Visual Studio – generovaný kód z uživatelsky vytvořeného kódu. Kód je rozdělen do diskrétních zdrojových souborů. Například **Návrhář formuláře Windows** definuje částečné třídy pro ovládací prvky, jako je například `Form`. V těchto ovládacích prvcích byste neměli upravovat generovaný kód.

 Další informace o částečných typech v Visual Basic naleznete v tématu [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).

## <a name="example"></a>Příklad
 Chcete-li rozdělit definici třídy v Visual Basic, použijte klíčové slovo `Partial`, jak je znázorněno v následujícím příkladu.

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

## <a name="example"></a>Příklad
 Chcete-li v vizuálu C#rozdělit definici třídy, použijte klíčové slovo `partial`, jak je znázorněno v následujícím příkladu.

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

## <a name="see-also"></a>Viz také
 Částečné [třídy a metody](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [částečné (typ)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334) částečná [(metoda)C# (Reference)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137) [Partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
