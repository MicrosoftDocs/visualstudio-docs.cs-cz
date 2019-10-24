---
title: Fragmenty kódu
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 09f6e2e9b4b89c7e6fd1fe9a342d4fd05b12e7a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747971"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou malé bloky opakovaně použitelného kódu, který lze vložit do souboru kódu pomocí příkazu nabídky po kliknutí pravým tlačítkem myši (kontextová nabídka) nebo kombinace klávesových zkratek. Obvykle obsahují často používané bloky kódu, například `try-finally` nebo `if-else` bloky, ale lze je použít k vložení celé třídy nebo metod.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [fragmenty kódu (Visual Studio pro Mac)](/visualstudio/mac/snippets).

Fragmenty kódu jsou k dispozici pro mnoho jazyků, včetně C#, C++, Visual Basic, XML a T-SQL, pro pojmenování. Chcete-li zobrazit všechny dostupné fragmenty nainstalované pro jazyk, otevřete **Správce fragmentů kódů** z nabídky **nástroje** (nebo stiskněte klávesovou zkratku **ctrl** +**K**, **CTRL** +**B**) a zvolte jazyk z rozevírací nabídky. v horní části.

![Dialogové okno Správce fragmentů kódů](media/code-snippets-manager.png)

K fragmentům kódu je možné přistupovat následujícími obecnými způsoby:

- Na panelu nabídek vyberte možnost **upravit**  > **IntelliSense**  > **Vložit fragment**

- V editoru kódu kliknutím pravým tlačítkem myši nebo v kontextové nabídce vyberte **fragment**  > **Vložit fragment**

- Na klávesnici stiskněte **ctrl** +**K**,**CTRL** +**X** .

## <a name="expansion-snippets-and-surround-with-snippets"></a>Fragmenty rozšíření a obklopení s fragmenty

V aplikaci Visual Studio existují dva druhy fragmentů kódu: fragmenty rozšíření, které jsou přidány v zadaném místě vložení a mohou nahradit zástupce fragmentu a obklopit s fragmenty (C# a C++ pouze), které jsou přidány kolem vybraného bloku kódu.

Příklad fragmentu rozšíření: v C# místní tryf se používá k vložení bloku try-finally:

```csharp
try
{

}
finally
{

}
```

Tento fragment kódu můžete vložit kliknutím na **Vložit fragment** v místní nabídce (kontextové nabídce) v okně kódu, potom **vizuálu C#** , zadáním `tryf` a stisknutím klávesy **TAB**. Můžete také zadat `tryf` a stisknout klávesu **TAB** dvakrát.

Příklad obklopit s fragmentem kódu: v C++ zástupce `if` lze použít buď jako fragment vložení, nebo jako obklopit s fragmentem kódu. Pokud vyberete řádek kódu (například `return FALSE;`) a pak zvolíte možnost **uzavřít s**  > ,**Pokud**je, fragment kódu se rozbalí kolem řádku:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry nahrazení fragmentů

Fragmenty kódu mohou obsahovat náhradní parametry, což jsou zástupné symboly, které je nutné nahradit, aby odpovídaly přesnému kódu, který píšete. V předchozím příkladu `true` je náhradní parametr, který byste nahradili odpovídající podmínkou. Náhrada, kterou provedete, se opakuje pro každou instanci stejného parametru nahrazení ve fragmentu.

Například v Visual Basic existuje fragment kódu, který vloží vlastnost. Chcete-li vložit fragment kódu, vyberte možnost **fragment kódu**  > **Vložit fragment** z místní nabídky nebo z kontextové nabídky v souboru kódu Visual Basic. Pak zvolte **vzory kódu**  > **vlastnosti, procedury, události**  > **definovat vlastnost**.

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

Změníte-li `newPropertyValue` na `m_property`, dojde ke změně každé instance `newPropertyValue`. Změníte-li `String` na `Int` v deklaraci vlastnosti, pak je hodnota v metodě set také změněna na `Int`.

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Postupy: distribuce fragmentů kódu](../ide/how-to-distribute-code-snippets.md)
- [Osvědčené postupy pro používání fragmentů kódu](../ide/best-practices-for-using-code-snippets.md)
- [Řešení potíží s fragmenty](../ide/troubleshooting-snippets.md)
- [C#fragmenty kódu](../ide/visual-csharp-code-snippets.md)
- [C++fragmenty kódu](../ide/visual-cpp-code-snippets.md)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
- [Fragmenty kódu (Visual Studio pro Mac)](/visualstudio/mac/snippets)
