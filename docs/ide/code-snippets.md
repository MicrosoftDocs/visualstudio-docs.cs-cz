---
title: Fragmenty kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- surround with
- code snippets
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 8ed3f2f8e588aa908827516fee44c1a38ad6a008
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348484"
---
# <a name="code-snippets"></a>Fragmenty kódu

Fragmenty kódu jsou malé bloky opakovaně použitelný kód, který může být vložen do souboru kódu pomocí příkazu kontextové nabídky nebo kombinace klávesových zkratek. Obvykle obsahují bloky kódu běžně používané jako `try-finally` nebo `if-else` blocích, ale je možné vložit celé třídy nebo metody.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [kódu fragmenty kódu (Visual Studio for Mac)](/visualstudio/mac/snippets).

Fragmenty kódu jsou k dispozici pro různé jazyky, včetně C#, C++, Visual Basic, XML a T-SQL, pár. Chcete-li zobrazit všechny dostupné nainstalovaných fragmenty kódu pro jazyk, otevřete **Správce fragmentů kódů** z **nástroje** nabídky v sadě Visual Studio a zvolte jazyk, z rozevírací nabídky v horní části.

![Dialogové okno Správce fragmentů kódu](media/code-snippets-manager.png)

Fragmenty kódu je přístupná v obecné takto:

- V panelu nabídky zvolte **upravit** > **IntelliSense** > **Vložit fragment**

- V nabídce klepněte pravým tlačítkem nebo kontextu v editoru kódu zvolte **fragment** > **Vložit fragment**

- Z klávesnice, stiskněte klávesu **Ctrl**+**K**+**X**

## <a name="expansion-snippets-and-surround-with-snippets"></a>Rozšíření fragmentů a příkazu Obklopit s fragmenty kódu

V sadě Visual Studio existují dva druhy fragment kódu: fragmenty kódu rozšíření, které jsou přidány zadaný kurzoru a mohou nahradit místní fragment kódu, a příkazu Obklopit s fragmenty kódu (C# a C++ pouze), které se přidají okolo vybraného bloku kódu.

Příklad fragment kódu rozšíření: v C# tryf místní slouží k vložení bloku try-finally:

```csharp
try
{

}
finally
{

}
```

Tento fragment kódu lze vložit kliknutím **Vložit fragment** v místní nabídce okna kódu, pak **Visual C#** , zadejte `tryf`a potom stiskněte klávesu **kartu**. Nebo můžete zadat `tryf` a stiskněte klávesu **kartu** dvakrát.

Příklad obklopit fragmentem: v jazyce C++ zástupce `if` lze použít jako fragment vložení nebo jako obklopit fragmentem. Pokud vyberete řádek kódu (například `return FALSE;`) a klikněte na tlačítko **obklopit fragmentem** > **Pokud**, fragment kódu je rozbalený kolem řádku:

```cpp
if (true)
{
    return FALSE;
}
```

## <a name="snippet-replacement-parameters"></a>Fragment kódu nahrazující parametry

Fragmenty kódu může obsahovat náhradní parametry, které jsou zástupné symboly, které je třeba nahradit podle přesný kód, který píšete. V předchozím příkladu `true` je parametr nahrazení, který by nahraďte vhodné podmínky. Nahrazení provedené se opakuje pro každou instanci stejné nahrazení parametrů v tomto fragmentu kódu.

Například v jazyce Visual Basic je fragment kódu, který se vkládá vlastnost. Chcete-li vložit fragment kódu, zvolte **fragment** > **Vložit fragment** nabídce klepněte pravým tlačítkem nebo kontextu v souboru kódu jazyka Visual Basic. Potom kliknutím na možnost **vzorů v kódu** > **vlastnosti, procedury, události** > **definovat vlastnost**.

![Nabídka fragment kódu pro definovat vlastnost](media/code-snippets-vb-property.png)

Následující kód je vložen:

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

Pokud změníte `newPropertyValue` k `m_property`, pak každá instance `newPropertyValue` se změnilo. Pokud změníte `String` k `Int` v deklaraci vlastnosti, pak hodnota metody set se také změní na `Int`.

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření fragmentu kódu](../ide/walkthrough-creating-a-code-snippet.md)
- [Postupy: distribuce fragmentů kódu](../ide/how-to-distribute-code-snippets.md)
- [Osvědčené postupy pro používání fragmentů kódu](../ide/best-practices-for-using-code-snippets.md)
- [Řešení potíží s fragmenty kódu](../ide/troubleshooting-snippets.md)
- [C#fragmenty kódu](../ide/visual-csharp-code-snippets.md)
- [Fragmenty kódu Visual C++](../ide/visual-cpp-code-snippets.md)
- [Referenční informace ke schématu fragmentů kódu](../ide/code-snippets-schema-reference.md)
- [Fragmenty kódu (Visual Studio for Mac)](/visualstudio/mac/snippets)