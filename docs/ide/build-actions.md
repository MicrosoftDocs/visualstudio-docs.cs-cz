---
title: Vytváření akcí pro soubory
ms.date: 11/19/2018
ms.technology: vs-ide-compile
ms.topic: reference
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35136ac0b7b0104f1812df7a9bf8ba81f6907374
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79301984"
---
# <a name="build-actions"></a>Akce sestavení

Všechny soubory v projektu sady Visual Studio mají akci sestavení. Akce sestavení řídí, co se stane se souborem při kompilaci projektu.

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Vytváření akcí ve Visual Studiu pro Mac](/visualstudio/mac/build-actions).

## <a name="set-a-build-action"></a>Nastavení akce sestavení

Chcete-li nastavit akci sestavení pro soubor, otevřete vlastnosti souboru v okně **Vlastnosti** tak, že soubor vyberete v **Průzkumníku řešení** a stisknete **klávesu Alt**+**Enter**. Nebo klikněte pravým tlačítkem myši na soubor v **Průzkumníku řešení** a zvolte **Vlastnosti**. V okně **Vlastnosti** v části **Upřesnit** nastavte akci sestavení pro soubor pomocí rozevíracího seznamu vedle **příkazu Vytvořit akci.**

![Vytváření akcí pro soubor v sadě Visual Studio](media/build-actions.png)

## <a name="build-action-values"></a>Vytváření hodnot akcí

Některé z nejběžnějších akcí sestavení pro soubory projektu jazyka C# a Visual Basic jsou:

|Vytvořit akci | Typy projektů | Popis |
|-|-|
| **Další soubory** | C#, Visual Basic | Nezdrojový textový soubor, který je předán kompilátoru jazyka C# nebo Visual Basic jako vstup. Tato akce sestavení se používá hlavně k poskytování vstupů [pro analyzátory,](../code-quality/roslyn-analyzers-overview.md) které jsou odkazovány projektem k ověření kvality kódu. Další informace naleznete v tématu [Použití dalších souborů](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Using%20Additional%20Files.md).|
| **Definice aplikace** | WPF | Soubor, který definuje vaši aplikaci. Při prvním vytvoření projektu je to *App.xaml*. |
| **CodeAnalysisDictionary** | .NET | Vlastní slovník slov, který analýza kódu používá pro kontrolu pravopisu. Viz [Postup: Přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)|
| **Kompilaci** | jakékoli | Soubor je předán kompilátoru jako zdrojový soubor.|
| **Obsah** | .NET | Soubor označený jako **obsah** lze načíst jako <xref:System.Windows.Application.GetContentStream%2A?displayProperty=nameWithType>datový proud voláním . U ASP.NET projektů jsou tyto soubory zahrnuty jako součást webu při jeho nasazení.|
| **DesignData** | WPF | Používá se pro soubory XAML ViewModel, aby bylo možné zobrazit uživatelské ovládací prvky v době návrhu s fiktivními typy a ukázkovými daty. |
| **NávrhDataWithDesignTimeVytvořitelný** | WPF | Stejně jako **DesignData**, ale se skutečnými typy.  |
| **Vložený prostředek** | .NET | Soubor je předán kompilátoru jako prostředek, který má být vložen do sestavení. Můžete volat <xref:System.Reflection.Assembly.GetManifestResourceStream%2A?displayProperty=fullName> číst soubor ze sestavení.|
| **EntityDeployDeploy** | .NET | Pro entity Framework (EF) .edmx soubory, které určují nasazení artefaktů EF. |
| **Padělky** | .NET | Používá se pro rozhraní testování Microsoft Fakes. Viz [Izolovat testovaný kód pomocí Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) |
| **Žádné** | jakékoli | Soubor není součástí sestavení v žádném případě. Tuto hodnotu lze použít například pro soubory dokumentace, jako jsou soubory "ReadMe".|
| **Stránka** | WPF | Kompilace souboru XAML do binárního souboru BAML pro rychlejší načítání za běhu. |
| **Prostředek** | WPF | Určuje vložení souboru do souboru prostředků manifestu sestavení s příponou *.g.resources*. |
| **Stín** | .NET | Používá se pro soubor .accessor, který obsahuje seznam sestavených názvů souborů sestavení, jeden na řádek. Pro každé sestavení v seznamu vygenerujte veřejné třídy s názvy, `ClassName_Accessor` které jsou stejné jako originály, ale s veřejnými metodami namísto soukromých metod. Používá se pro testování částí. |
| **Úvodní obrazovka** | WPF | Určuje soubor obrázku, který se má zobrazit za běhu při spuštění aplikace. |
| **XamlAppDef** | Windows Workflow Foundation | Dává sestavení pokyn k vytvoření souboru XAML pracovního postupu do sestavení s vloženým pracovním postupem. |

> [!NOTE]
> Další akce sestavení mohou být definovány pro konkrétní typy projektů, takže seznam akcí sestavení závisí na typu projektu a hodnoty, které nejsou v tomto seznamu.

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](/dotnet/csharp/language-reference/compiler-options/listed-alphabetically)
- [Možnosti kompilátoru jazyka Visual Basic](/dotnet/visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically)
- [Akce sestavení (Visual Studio pro Mac)](/visualstudio/mac/build-actions)
