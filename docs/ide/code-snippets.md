---
title: Fragmenty kódu
description: Přečtěte si o fragmentech kódu a o tom, jak jsou malými bloky opakovaně použitelného kódu, který lze vložit do souboru kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 52059dd464ad0c720a4a2e77a961b7d6f3525c6d
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006390"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou malé bloky opakovaně použitelného kódu, který lze vložit do souboru kódu pomocí příkazu nabídky po kliknutí pravým tlačítkem myši (kontextová nabídka) nebo kombinace klávesových zkratek. Obvykle obsahují často používané bloky kódu `try-finally` , například nebo `if-else` bloky, ale lze je použít k vložení celé třídy nebo metod.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [fragmenty kódu (Visual Studio pro Mac)](/visualstudio/mac/snippets).

Fragmenty kódu jsou k dispozici pro mnoho jazyků, včetně C#, C++, Visual Basic, XML a T-SQL, pro pojmenování několika málo. Chcete-li zobrazit všechny dostupné nainstalované fragmenty pro jazyk, otevřete **Správce fragmentů kódů** z nabídky **nástroje** (nebo stiskněte klávesy **CTRL** + **K**, **CTRL** + **B**) a zvolte jazyk z rozevírací nabídky v horní části.

![Dialogové okno Správce fragmentů kódů](media/code-snippets-manager.png)

K fragmentům kódu je možné přistupovat následujícími obecnými způsoby:

- Na panelu nabídek vyberte možnost **Upravit**  >  **IntelliSense**  >  **Vložit fragment** .

- V editoru kódu kliknutím pravým tlačítkem myši nebo v místní nabídce vyberte **fragment** kódu  >  **Vložit fragment**

- Na klávesnici stiskněte klávesu **CTRL** + **K**,**CTRL** + **X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty rozšíření a obklopení s fragmenty

V aplikaci Visual Studio existují dva druhy fragmentů kódu: fragmenty rozšíření, které jsou přidány v zadaném místě vložení a mohou nahradit zástupce fragmentu a obklopit pomocí fragmentů (pouze C# a C++), které jsou přidány kolem vybraného bloku kódu.

Příklad fragmentu rozšíření: v jazyce C# je pro vložení bloku try-finally použit zástupce tryf:

```csharp
try
{

}
finally
{

}
```

Tento fragment kódu lze vložit kliknutím na tlačítko **Vložit fragment** v místní nabídce (kontextová nabídka) v okně kódu, poté na položku **Visual C#** a poté zadat `tryf` příkaz a stiskněte klávesu **TAB**. Nebo můžete zadat `tryf` a stisknout klávesu **TAB** dvakrát.

Příklad obklopit s fragmentem kódu: v jazyce C++ zástupce `if` lze použít buď jako fragment vložení, nebo jako obklopit s fragmentem kódu. Pokud vyberete řádek kódu (například `return FALSE;` ) a pak zvolíte možnost **uzavřít pomocí**  >  **if**, fragment kódu se rozbalí kolem řádku:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry nahrazení fragmentů

Fragmenty kódu mohou obsahovat náhradní parametry, což jsou zástupné symboly, které je nutné nahradit, aby odpovídaly přesnému kódu, který píšete. V předchozím příkladu `true` je náhradní parametr, který byste nahradili příslušnou podmínkou. Náhrada, kterou provedete, se opakuje pro každou instanci stejného parametru nahrazení ve fragmentu.

Například v Visual Basic existuje fragment kódu, který vloží vlastnost. Chcete-li **Vložit fragment kódu, vyberte možnost**  >  **Vložit fragment kódu** z místní nabídky nebo z kontextové nabídky v souboru kódu Visual Basic. Pak zvolte vlastnosti **vzorů kódu**  >  **, procedury, události**  >  **definují vlastnost**.

![Nabídka fragmentu kódu pro definování vlastnosti](media/code-snippets-vb-property.png)

Je vložen následující kód:

```vb
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property
```

Změníte-li `newPropertyValue` na `m_property` , pak dojde ke změně každé instance `newPropertyValue` . Pokud se `String` `Int` v deklaraci vlastnosti změní na, pak je hodnota v metodě set také změněna na `Int` .

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Postupy: distribuce fragmentů kódu](../ide/how-to-distribute-code-snippets.md)
- [Osvědčené postupy pro používání fragmentů kódu](../ide/best-practices-for-using-code-snippets.md)
- [Řešení potíží s fragmenty](../ide/troubleshooting-snippets.md)
- [Fragmenty kódu v jazyce C#](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kódu C++](../ide/visual-cpp-code-snippets.md)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
- [Fragmenty kódu (Visual Studio pro Mac)](/visualstudio/mac/snippets)
