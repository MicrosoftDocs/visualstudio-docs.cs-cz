---
title: Potlačení porušení analýzy kódu
ms.date: 08/27/2020
description: Přečtěte si, jak potlačit porušení analýzy kódu v aplikaci Visual Studio. Pochopte, jak použít atribut SuppressMessageAttribute pro potlačení v rámci zdroje.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: b7a0820404047d123350a27950c5aee254af306f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348694"
---
# <a name="suppress-code-analysis-violations"></a>Potlačení porušení analýzy kódu

Je často vhodné označit, že upozornění není k dispozici. To znamená, že členové týmu byli zkontrolováni kód a že je možné upozornění potlačit. In-source potlačení (ISS) používá <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atribut k potlačení upozornění. Atribut může být umístěn blízko segmentu kódu, který vygeneroval upozornění. Atribut můžete přidat <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> do zdrojového souboru jeho zadáním do, nebo můžete použít místní nabídku na upozornění v **Seznam chyb** k jeho automatickému přidání.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Atribut je podmíněný atribut, který je obsažen v metadatech Il sestavení spravovaného kódu, pouze pokud je symbol kompilace CODE_ANALYSIS definován v době kompilace.

V jazyce C++/CLI použijte \_ \_ \_ \_ k přidání atributu v hlavičkovém souboru globální SUPPRESS_MESSAGE certifikační autority maker.

> [!NOTE]
> V sestavách vydaných verzí byste neměli používat potlačení ve zdrojovém kódu, abyste zabránili nechtěnému přesouvání metadat potlačení ve zdroji. Z důvodu nákladů na zpracování potlačení v rámci zdroje je navíc možné snížit výkon vaší aplikace.

::: moniker range="vs-2017"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2017, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit tak, že vyberete **analyzovat**  >  **Spustit analýzu kódu a potlačit aktivní problémy**.
>
> ![Spustit analýzu kódu a potlačit problémy v aplikaci Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2019, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit výběrem možnosti **analyzovat**  >  **sestavení a potlačit aktivní problémy**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage – atribut

Když vyberete možnost **potlačit** z kontextu nebo v místní nabídce upozornění analýzy kódu v **Seznam chyb** , přidá se do <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kódu nebo do globálního souboru potlačení projektu atribut.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Atribut má následující formát:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Mezi vlastnosti atributu patří:

- **Category** (kategorie) – kategorie, ve které je definováno pravidlo. Další informace o kategoriích pravidla analýzy kódu najdete v tématu [Upozornění spravovaného kódu](/dotnet/fundamentals/code-analysis/quality-rules/index).

- **CheckId** – identifikátor pravidla. Podpora zahrnuje krátký i dlouhý název identifikátoru pravidla. Krátký název je CAXXXX; dlouhé jméno je CAXXXX: FriendlyTypeName.

- **Odůvodnění** – text, který se používá k dokumentaci důvodu pro potlačení zprávy.

- **MessageID** – jedinečný identifikátor problému pro každou zprávu.

- **Rozsah** – cíl, na kterém je upozornění potlačeno. Pokud není cíl zadán, je nastaven na cíl atributu. Mezi podporované [obory](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) patří následující:

  - [`module`](#module-suppression-scope) – Tento rozsah potlačuje upozornění proti sestavení. Jedná se o globální potlačení, které platí pro celý projekt.

  - `resource` – (jenom[starší verze FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) ) Tento obor potlačí upozornění v diagnostických informacích zapsaných do souborů prostředků, které jsou součástí modulu (Assembly). Tento rozsah není v kompilátorech C#/VB pro diagnostiku Roslyn Analyzer, který analyzuje jenom zdrojové soubory, nedodržuje/nedodržuje žádné informace.

  - `type` – Tento rozsah potlačuje upozornění proti typu.

  - `member` – Tento rozsah potlačuje upozornění proti členu.

  - `namespace` – Tento rozsah potlačuje upozornění proti samotnému oboru názvů. Potlačí upozornění na typy v rámci oboru názvů.

  - `namespaceanddescendants` – (Vyžaduje kompilátor verze 3. x nebo vyšší a Visual Studio 2019) Tento rozsah potlačuje upozornění v oboru názvů a všechny jeho odvozené symboly. `namespaceanddescendants`Hodnota se ignoruje v rámci analýzy starší verze.

- **Target** – identifikátor, který se používá k určení cíle, na kterém je upozornění potlačeno. Musí obsahovat plně kvalifikovaný název položky.

Když se v aplikaci Visual Studio zobrazí upozornění, můžete zobrazit příklady přidáním `SuppressMessage` [potlačení do globálního souboru potlačení](../code-quality/use-roslyn-analyzers.md#suppress-violations). Atribut potlačení a požadované vlastnosti se zobrazí v okně náhledu.

## <a name="suppressmessage-usage"></a>Využití SuppressMessage

Upozornění analýzy kódu jsou potlačena na úrovni, na kterou <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> je atribut použit. Atribut lze například použít na úrovni sestavení, modulu, typu, člena nebo parametru. Účelem tohoto je pevně spojit informace o potlačení s kódem, kde dojde k porušení.

Obecná podoba potlačení zahrnuje kategorii pravidla a identifikátor pravidla, který obsahuje nepovinné uživatelsky čitelné reprezentace názvu pravidla. Příklad:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Pokud existují přísné důvody pro výkon pro minimalizaci v metadatech potlačení zdroje, je možné název pravidla vynechat. Kategorie pravidla a ID pravidla společně tvoří dostatečně jedinečný identifikátor pravidla. Příklad:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

V případě důvodů zachování nedoporučujeme název pravidla vynechat.

## <a name="suppress-selective-violations-within-a-method-body"></a>Potlačit selektivní porušení v těle metody

Atributy potlačení lze použít pro metodu, ale nelze je vložit do těla metody. To znamená, že všechna porušení určitého pravidla jsou potlačena při přidání <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributu do metody.

V některých případech můžete chtít potlačit určitou instanci porušení, například tak, aby budoucí kód nebyl automaticky vyloučen z pravidla analýzy kódu. Určitá pravidla analýzy kódu vám umožňují použít `MessageId` vlastnost <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributu. Obecně platí, že starší pravidla pro porušení určitého symbolu (místní proměnná nebo parametr) respektují `MessageId` vlastnost. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) je příkladem takového pravidla. Starší pravidla pro porušení u spustitelného kódu (bez symbolu) ale nerespektují `MessageId` vlastnost. Kromě toho .NET Compiler Platform ("Roslyn") analyzátory nerespektují `MessageId` vlastnost.

Chcete-li potlačit určité porušení symbolu pravidla, zadejte název symbolu pro `MessageId` vlastnost <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributu. Následující příklad ukazuje kód se dvěma porušeními [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) &mdash; jeden pro `name` proměnnou a jednu pro `age` proměnnou. Pouze porušení pro `age` symbol je potlačeno.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="global-level-suppressions"></a>Potlačení na globální úrovni

Nástroj Analýza spravovaného kódu prověřuje `SuppressMessage` atributy, které jsou aplikovány na úrovni sestavení, modulu, typu, člena nebo parametru. Také se aktivují narušení proti prostředkům a oborům názvů. Tato porušení musí být použita na globální úrovni a mají rozsah a cíl. Například následující zpráva potlačuje porušení oboru názvů:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Potlačíte-li upozornění s `namespace` rozsahem, potlačí upozornění na samotný obor názvů. Potlačí upozornění na typy v rámci oboru názvů.

Jakékoli potlačení lze vyjádřit zadáním explicitního oboru. Tato potlačení musí být živá na globální úrovni. Nemůžete zadat potlačení na úrovni člena upravení typem.

Potlačení globální úrovně jsou jediným způsobem, jak potlačit zprávy, které odkazují na kód generovaný kompilátorem, který není namapován na explicitně zadaný zdroj uživatele. Například následující kód potlačí porušení proti konstruktoru generovanému kompilátorem:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` vždy obsahuje plně kvalifikovaný název položky.

### <a name="global-suppression-file"></a>Globální soubor potlačení

Globální soubor potlačení uchovává potlačení, která jsou buď potlačená, nebo potlačení, která neurčují cíl. Například potlačení pro porušení na úrovni sestavení se ukládají do tohoto souboru. Kromě toho jsou v tomto souboru uložena některá potlačení ASP.NET, protože nastavení na úrovni projektu nejsou k dispozici pro kód za formulářem. Globální soubor potlačení je vytvořen a přidán do projektu při prvním výběru možnosti **v souboru potlačení projektu** v příkazu **potlačit** v okně **Seznam chyb** .

### <a name="module-suppression-scope"></a>Rozsah potlačení modulu

Můžete potlačit porušení kvality kódu pro celé sestavení pomocí oboru **modulu** .

Například následující atribut v souboru projektu _GlobalSuppressions_ potlačí porušení ConfigureAwait pro projekt ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="generated-code"></a>Generovaný kód

Kompilátory spravovaného kódu a některé nástroje třetích stran generují kód pro usnadnění rychlého vývoje kódu. Kód generovaný kompilátorem, který se zobrazí ve zdrojových souborech, je obvykle označen `GeneratedCodeAttribute` atributem.

V případě analýzy zdrojového kódu můžete potlačit zprávy v generovaném kódu v `.editorconfig` souboru. Další informace naleznete v tématu [Exclude Generated Code](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code).

Pro analýzu starší verze kódu můžete zvolit, zda chcete potlačit upozornění analýzy kódu a chyby pro vygenerovaný kód. Informace o tom, jak potlačit taková upozornění a chyby, naleznete v tématu [How to: potlačit upozornění pro generovaný kód](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analýza kódu se ignoruje `GeneratedCodeAttribute` , když se použije na celé sestavení nebo na jeden parametr.

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Použití analyzátorů kódu](../code-quality/use-roslyn-analyzers.md)
