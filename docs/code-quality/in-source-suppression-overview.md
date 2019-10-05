---
title: Potlačit upozornění analýzy kódu
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 670150053053a2e556e0f111312247f243c2a8c0
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975042"
---
# <a name="suppress-code-analysis-warnings"></a>Potlačit upozornění analýzy kódu

Je často vhodné označit, že upozornění není k dispozici. To znamená, že členové týmu byli zkontrolováni kód a že je možné upozornění potlačit. In-source potlačení (ISS) používá pro potlačení upozornění atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Atribut může být umístěn blízko segmentu kódu, který vygeneroval upozornění. Můžete přidat atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> do zdrojového souboru jeho zadáním do nebo můžete použít místní nabídku s upozorněním v **Seznam chyb** k jeho automatickému přidání.

Atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> je podmíněný atribut, který je obsažen v metadatech IL sestavení spravovaného kódu, pouze pokud je symbol kompilace CODE_ANALYSIS definován v době kompilace.

V C++/CLI použijte k přidání atributu certifikační autorita maker @ NO__T-1SUPPRESS @ NO__T-2MESSAGE nebo CA @ NO__T-3GLOBAL @ NO__T-4SUPPRESS_MESSAGE v hlavičkovém souboru.

> [!NOTE]
> V sestavách vydaných verzí byste neměli používat potlačení ve zdrojovém kódu, abyste zabránili nechtěnému přesouvání metadat potlačení ve zdroji. Z důvodu nákladů na zpracování potlačení v rámci zdroje je navíc možné snížit výkon vaší aplikace.

::: moniker range="vs-2017"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2017, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit výběrem možnosti **analyzovat** > **Spustit analýzu kódu a potlačit aktivní problémy**.
>
> ![Spustit analýzu kódu a potlačit problémy v aplikaci Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2019, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit výběrem možnosti **analyzovat** > **sestavení a potlačit aktivní problémy**.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage – atribut

Pokud zvolíte možnost **potlačit** v kontextu nebo v místní nabídce upozornění analýzy kódu v **Seznam chyb**, atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> se přidá buď do kódu, nebo do globálního souboru potlačení projektu.

Atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> má následující formát:

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

- **Category** (kategorie) – kategorie, ve které je definováno pravidlo. Další informace o kategoriích pravidla analýzy kódu najdete v tématu [Upozornění spravovaného kódu](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** – identifikátor pravidla. Podpora zahrnuje krátký i dlouhý název identifikátoru pravidla. Krátký název je CAXXXX; dlouhé jméno je CAXXXX: FriendlyTypeName.

- **Odůvodnění** – text, který se používá k dokumentaci důvodu pro potlačení zprávy.

- **MessageID** – jedinečný identifikátor problému pro každou zprávu.

- **Rozsah** – cíl, na kterém je upozornění potlačeno. Pokud není cíl zadán, je nastaven na cíl atributu. Mezi podporované [obory](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) patří následující:

  - `module`

  - `resource`

  - `type`

  - `member`

  - `namespace` – Tento rozsah potlačuje upozornění proti samotnému oboru názvů. Potlačí upozornění na typy v rámci oboru názvů.

  - `namespaceanddescendants` – (novinka pro Visual Studio 2019) Tento rozsah potlačuje upozornění v oboru názvů a všechny jeho odvozené symboly. Hodnota `namespaceanddescendants` je starší než analýza ignoruje.

- **Target** – identifikátor, který se používá k určení cíle, na kterém je upozornění potlačeno. Musí obsahovat plně kvalifikovaný název položky.

## <a name="suppressmessage-usage"></a>Využití SuppressMessage

Upozornění analýzy kódu jsou potlačena na úrovni, na kterou je použit atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Atribut lze například použít na úrovni sestavení, modulu, typu, člena nebo parametru. Účelem tohoto je pevně spojit informace o potlačení s kódem, kde dojde k porušení.

Obecná podoba potlačení zahrnuje kategorii pravidla a identifikátor pravidla, který obsahuje nepovinné uživatelsky čitelné reprezentace názvu pravidla. Příklad:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Pokud existují přísné důvody pro výkon pro minimalizaci v metadatech potlačení zdroje, je možné název pravidla vynechat. Kategorie pravidla a ID pravidla společně tvoří dostatečně jedinečný identifikátor pravidla. Příklad:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

V případě důvodů zachování nedoporučujeme název pravidla vynechat.

## <a name="suppress-selective-violations-within-a-method-body"></a>Potlačit selektivní porušení v těle metody

Atributy potlačení lze použít pro metodu, ale nelze je vložit do těla metody. To znamená, že všechna porušení určitého pravidla jsou potlačena, pokud přidáte atribut <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> do metody.

V některých případech můžete chtít potlačit určitou instanci porušení, například tak, aby budoucí kód nebyl automaticky vyloučen z pravidla analýzy kódu. Určitá pravidla analýzy kódu vám umožňují použít vlastnost `MessageId` atributu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Obecně platí, že starší pravidla pro porušení určitého symbolu (místní proměnná nebo parametr) respektují vlastnost `MessageId`. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) je příkladem takového pravidla. Starší pravidla pro porušení u spustitelného kódu (bez symbolu) ale nerespektují vlastnost `MessageId`. Kromě toho .NET Compiler Platform ("Roslyn") analyzátory nerespektují vlastnost `MessageId`.

Chcete-li potlačit určité porušení symbolu pravidla, zadejte název symbolu pro vlastnost `MessageId` atributu <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>. Následující příklad ukazuje kód se dvěma porušováními [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;one pro proměnnou `name` a druhou pro proměnnou `age`. Pouze porušení pro symbol `age` je potlačeno.

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

## <a name="generated-code"></a>Generovaný kód

Kompilátory spravovaného kódu a některé nástroje třetích stran generují kód pro usnadnění rychlého vývoje kódu. Kód generovaný kompilátorem, který se zobrazí ve zdrojových souborech, je obvykle označen atributem `GeneratedCodeAttribute`.

Můžete zvolit, zda chcete potlačit upozornění a chyby analýzy kódu pro vygenerovaný kód. Informace o tom, jak potlačit taková upozornění a chyby, najdete v tématu [How: Potlačit upozornění pro generovaný kód @ no__t-0

> [!NOTE]
> Analýza kódu ignoruje `GeneratedCodeAttribute` při použití na celé sestavení nebo na jeden parametr.

## <a name="global-level-suppressions"></a>Potlačení na globální úrovni

Nástroj Analýza spravovaného kódu prověřuje atributy `SuppressMessage`, které jsou aplikovány na úrovni sestavení, modulu, typu, člena nebo parametru. Také se aktivují narušení proti prostředkům a oborům názvů. Tato porušení musí být použita na globální úrovni a mají rozsah a cíl. Například následující zpráva potlačuje porušení oboru názvů:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Potlačíte-li upozornění s rozsahem `namespace`, potlačí se upozornění proti samotnému oboru názvů. Potlačí upozornění na typy v rámci oboru názvů.

Jakékoli potlačení lze vyjádřit zadáním explicitního oboru. Tato potlačení musí být živá na globální úrovni. Nemůžete zadat potlačení na úrovni člena upravení typem.

Potlačení globální úrovně jsou jediným způsobem, jak potlačit zprávy, které odkazují na kód generovaný kompilátorem, který není namapován na explicitně zadaný zdroj uživatele. Například následující kód potlačí porušení proti konstruktoru generovanému kompilátorem:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` vždy obsahuje plně kvalifikovaný název položky.

## <a name="global-suppression-file"></a>Globální soubor potlačení

Globální soubor potlačení uchovává potlačení, která jsou buď potlačená, nebo potlačení, která neurčují cíl. Například potlačení pro porušení na úrovni sestavení se ukládají do tohoto souboru. Kromě toho jsou v tomto souboru uložena některá potlačení ASP.NET, protože nastavení na úrovni projektu nejsou k dispozici pro kód za formulářem. Globální soubor potlačení je vytvořen a přidán do projektu při prvním výběru možnosti **v souboru potlačení projektu** v příkazu **potlačit** v okně **Seznam chyb** .

## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Použití analyzátorů kódu](../code-quality/use-roslyn-analyzers.md)
