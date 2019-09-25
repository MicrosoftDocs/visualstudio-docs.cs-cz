---
title: Akce sestavení pro soubory
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254427"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu sady Visual Studio mají akci sestavení. Akce sestavení Určuje, co se stane se souborem při kompilování projektu.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac najdete v tématu [Akce sestavení v Visual Studio pro Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Nastavit akci sestavení

Chcete-li nastavit akci sestavení pro soubor, otevřete vlastnosti souboru v okně **vlastnosti** tak, že vyberete soubor v **Průzkumník řešení** a stisknete **klávesu ALT**+**ENTER**. Nebo klikněte pravým tlačítkem na soubor v **Průzkumník řešení** a vyberte **vlastnosti**. V okně **vlastnosti** v části Upřesnit použijte rozevírací seznam vedle **Možnosti** **sestavit akci** pro nastavení akce sestavení pro daný soubor.

![Akce sestavení pro soubor v aplikaci Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Sestavit hodnoty akcí

Některé nejběžnější akce sestavení pro C# a Visual Basic soubory projektu jsou:

|Akce sestavení | Typy projektů | Popis |
|-|-|
| **AdditionalFiles** | C#Visual Basic | Nezdrojový textový soubor, který se předává kompilátoru C# nebo Visual Basic jako vstup. Tato akce sestavení slouží hlavně k poskytnutí vstupů [analyzátorům](../code-quality/roslyn-analyzers-overview.md) , na které se odkazuje v projektu za účelem ověření kvality kódu. Další informace najdete v tématu [použití dalších souborů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **ApplicationDefinition** | WPF | Soubor, který definuje vaši aplikaci. Při prvním vytvoření projektu se jedná o *App. XAML*. |
| **CodeAnalysisDictionary** | .NET | Vlastní slovník slov, který je používán analýzou kódu pro kontrolu pravopisu. Viz [jak: Přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Sestavení** | Jakýmikoli | Soubor je předán kompilátoru jako zdrojový soubor.|
| **Obsah** | .NET | Soubor označený jako **obsah** lze načíst jako datový proud voláním <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>. Pro projekty ASP.NET jsou tyto soubory zahrnuty jako součást webu při jeho nasazení.|
| **Vazbě designdata** | WPF | Slouží k tomu, aby byly uživatelské ovládací prvky zobrazovány v době návrhu s použitím fiktivních typů a ukázkových dat, pro soubory ViewModel XAML. |
| **DesignDataWithDesignTimeCreateable** | WPF | Podobně jako **vazbě designdata**, ale se skutečnými typy.  |
| **Vložený prostředek** | .NET | Soubor je předán kompilátoru jako prostředek, který má být vložen do sestavení. Můžete zavolat <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> pro čtení souboru ze sestavení.|
| **EntityDeploy** | .NET | Pro Entity Framework (EF). edmx soubory, které určují nasazení artefaktů EF. |
| **Fakes** | .NET | Používá se pro testovací rozhraní napodobeniny od společnosti Microsoft. Viz [izolování testovaného kódu pomocí napodobenin společnosti Microsoft](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Žádné** | Jakýmikoli | Soubor není součástí sestavení jakýmkoli způsobem. Tato hodnota se dá použít například pro soubory dokumentace, například soubory Readme.|
| **Stránka** | WPF | Zkompilujte soubor XAML do binárního souboru. BAML pro rychlejší načítání v době běhu. |
| **Prostředek** | WPF | Určuje, že se má soubor vložit do souboru prostředků manifestu sestavení s příponou *. g. Resources*. |
| **Vytváření** | .NET | Používá se pro soubor. přistupující objekt, který obsahuje seznam sestavených názvů souborů sestavení, jednu na řádek. Pro každé sestavení v seznamu vygenerujte veřejné třídy s názvy `ClassName_Accessor` , které jsou stejně jako originály, ale s veřejnými metodami namísto privátních metod. Používá se pro testování částí. |
| **Úvodní obrazovka** | WPF | Určuje soubor obrázku, který se má zobrazit v době spuštění aplikace. |
| **XamlAppDef** | Windows Workflow Foundation | Vydá pokyn sestavení k sestavení souboru XAML pracovního postupu do sestavení pomocí vloženého pracovního postupu. |

> [!NOTE]
> Další akce sestavení mohou být definovány pro konkrétní typy projektů, takže seznam akcí sestavení závisí na typu projektu a hodnoty mohou být zobrazeny, které nejsou v tomto seznamu.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Možnosti kompilátoru Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Akce sestavení (Visual Studio pro Mac)](/visualstudio/mac/build-actions)
