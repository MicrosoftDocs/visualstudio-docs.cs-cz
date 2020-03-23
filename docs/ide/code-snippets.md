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
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: c06f9f7dc7e5a672e3fd5da3f3fc834fe223a783
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585415"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou malé bloky opakovaně použitelného kódu, které lze vložit do souboru kódu pomocí příkazu nabídky pravým tlačítkem myši (kontextová nabídka) nebo kombinace klávesových zkratek. Obvykle obsahují běžně používané bloky kódu, jako `try-finally` jsou bloky nebo `if-else` bloky, ale mohou být použity k vložení celých tříd nebo metod.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. V jazyce Visual Studio for Mac najdete v [tématu Fragmenty kódu (Visual Studio pro Mac).](/visualstudio/mac/snippets)

Fragmenty kódu jsou k dispozici pro velké množství jazyků, včetně C#, C++, Visual Basic, XML a T-SQL, abychom jmenovali několik. Chcete-li zobrazit všechny dostupné nainstalované úryvky pro jazyk, otevřete **Správce výstřižků kódu** z nabídky **Nástroje** (nebo stiskněte **kombinaci kláves Ctrl**+**K**, **Ctrl**+**B**) a zvolte jazyk z rozbalovací nabídky nahoře.

![Dialogové okno Správce výstřižků kódu](media/code-snippets-manager.png)

Fragmenty kódu lze přistupovat následujícími obecnými způsoby:

- Na řádku nabídek zvolte **Upravit** > **výstřižek vložení** technologie**IntelliSense.** > 

- Z nabídky pravým tlačítkem nebo v místní nabídce v editoru kódu zvolte Úryvek **Snippet** > **vložit úryvek.**

- Na klávesnici stiskněte **ctrl**+**k**,**Ctrl**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Výstřižky pro rozšíření a prostorové úryvky

V sadě Visual Studio existují dva druhy fragmentu kódu: fragmenty rozšíření, které jsou přidány v zadaném bodě vložení a mohou nahradit zástupce výstřižku a prostorové fragmenty (pouze C# a C++), které jsou přidány kolem vybraného bloku kódu.

Příklad fragmentu rozšíření: v c# zástupce tryf se používá k vložení try-finally bloku:

```csharp
try
{

}
finally
{

}
```

Tento fragment můžete vložit klepnutím na příkaz **Vložit výstřižk** v nabídce (kontextová nabídka) okna kódu, potom na **Visual C#**, zadejte `tryf`a stiskněte **klávesu Tab**. Nebo můžete zadat `tryf` a stisknout **klávesu Tab** dvakrát.

Příklad úryvku surround-with: v jazyce C++ lze zástupce `if` použít buď jako fragment vložení, nebo jako prostorový úryvek. Pokud vyberete řádek kódu `return FALSE;`(například ) a pak **zvolíte Prostorovat podle** > **,** fragment se rozbalí kolem řádku:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Parametry nahrazení úryvku

Výstřižky mohou obsahovat náhradní parametry, což jsou zástupné symboly, které je nutné nahradit, aby odpovídaly přesnému kódu, který píšete. V předchozím `true` příkladu je náhradní parametr, který byste nahradit příslušnou podmínku. Nahrazení, které provedete, se opakuje pro každou instanci stejného parametru nahrazení ve fragmentu.

Například v jazyce Visual Basic je fragment kódu, který vloží vlastnost. Chcete-li vložit výstřižek, zvolte **Výstřižk** > **vložit výstřižek** z nabídky pravým kliknutím nebo kontextovou nabídkou v souboru kódu jazyka Visual Basic. Potom zvolte **Vlastnosti vzorů** > **kódu, procedury, události** > **definujte vlastnost**.

![Nabídka fragmentu kódu pro definovat vlastnost](media/code-snippets-vb-property.png)

Vkládá se nový kód:

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

Pokud `newPropertyValue` změníte `m_property`na , `newPropertyValue` pak se změní každá instance. Pokud `String` změníte `Int` na v deklaraci vlastnosti, pak hodnota `Int`v metodě set se také změní na .

## <a name="see-also"></a>Viz také

- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Postup: Distribuce fragmentů kódu](../ide/how-to-distribute-code-snippets.md)
- [Doporučené postupy pro použití fragmentů kódu](../ide/best-practices-for-using-code-snippets.md)
- [Poradce při potížích s výstřižky](../ide/troubleshooting-snippets.md)
- [Fragmenty kódu Jazyka C#](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kódu Jazyka C++](../ide/visual-cpp-code-snippets.md)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
- [Fragmenty kódu (Visual Studio pro Mac)](/visualstudio/mac/snippets)
