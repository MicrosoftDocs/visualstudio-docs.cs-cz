---
title: Potlačení porušení analýzy kódu
ms.date: 05/10/2021
description: Přečtěte si, jak potlačit porušení analýzy kódu v aplikaci Visual Studio. Pochopte, jak použít atribut SuppressMessageAttribute pro potlačení v rámci zdroje.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973333"
---
# <a name="suppress-code-analysis-violations"></a>Potlačení porušení analýzy kódu

Je často vhodné označit, že upozornění není k dispozici. To znamená, že členové týmu byli zkontrolováni kód a že je možné upozornění potlačit. Tento článek popisuje různé způsoby, jak potlačit porušení analýzy kódu pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>Potlačit porušení pomocí souboru EditorConfig

V **souboru EditorConfig** nastavte závažnost na `none` , například `dotnet_diagnostic.CA1822.severity = none` . Chcete-li přidat soubor EditorConfig, přečtěte si téma [Přidání souboru EditorConfig do projektu](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files).

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>Potlačit porušení ve zdrojovém kódu

Můžete potlačit porušení v kódu pomocí direktivy preprocesoru, direktivy [#pragma upozornění (C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) nebo [disabled (Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) pro potlačení upozornění pouze pro konkrétní řádek kódu. Nebo můžete použít [atribut SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- Z **editoru kódu**

  Umístěte kurzor na řádek kódu s porušením a stisknutím klávesy **CTRL** + **(.)** otevřete nabídku **rychlé akce** . Vyberte **potlačit CAXXXX** a pak zvolte buď **ve zdroji** , nebo **ve zdroji (atribut)**.

  Pokud zvolíte možnost **zdroj**, uvidíte náhled direktivy preprocesoru, který bude přidán do kódu.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="Potlačit diagnostiku z nabídky rychlé akce":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="Potlačit diagnostiku z nabídky rychlé akce":::

  Pokud se rozhodnete **v části zdroj (atribut)**, zobrazí se náhled [atributu SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute) , který se přidá do kódu.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="Potlačit diagnostiku z nabídky rychlé akce pomocí atributu":::
  ::: moniker-end

- Z **Seznam chyb**

  Vyberte pravidla, která chcete potlačit, a potom klikněte pravým tlačítkem myši a vyberte **potlačit**  >  **ve zdroji**.

  - Pokud potlačíte **ve zdroji**, otevře se dialogové okno **Náhled změn** , ve kterém se zobrazí náhled [#pragma upozornění](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) a direktiva Visual Basic [#Disable upozornění](/dotnet/visual-basic/language-reference/directives/directives) , která je přidána do zdrojového kódu.

    ![Náhled Přidání upozornění #pragma v souboru kódu](media/pragma-warning-preview.png)

  V dialogovém okně **Náhled změn** vyberte **použít**.

  > [!NOTE]
  > Pokud nevidíte možnost nabídky **potlačit** v **Průzkumník řešení**, porušení pravděpodobně přijde z buildu a ne za živou analýzu. **Seznam chyb** zobrazuje narušení diagnostiky nebo pravidla, a to od živých analýz kódu i sestavení. Vzhledem k tomu, že diagnostika sestavení může být zastaralá, například pokud jste upravili kód pro opravu porušení, ale ještě nebyla znovu sestavena, nemůžete tuto diagnostiku z **Seznam chyb** potlačit. Diagnostika z živých analýz nebo IntelliSense je vždy aktuální s aktuálními zdroji a lze ji potlačit z **Seznam chyb**. Pokud chcete z výběru vyloučit diagnostiku *sestavení* , přepněte filtr zdroje **Seznam chyb** z **Build + IntelliSense** na **pouze IntelliSense**. Pak vyberte diagnostiku, kterou chcete potlačit, a pokračujte podle postupu popsaného výše.
  >
  > ![Zdrojový filtr Seznam chyb v aplikaci Visual Studio](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>Potlačit porušení pomocí globálního souboru potlačení

[Globální soubor potlačení](#global-level-suppressions) používá [atribut SuppressMessage](#in-source-suppression-and-the-suppressmessage-attribute).

- Z **Seznam chyb** vyberte pravidla, která chcete potlačit, a potom klikněte pravým tlačítkem myši a vyberte **potlačit**  >  **v souboru potlačení**. Otevře se dialogové okno **Náhled změn** a zobrazí náhled <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atributu, který je přidán do globálního souboru potlačení.

  ![Náhled přidání atributu SuppressMessage do souboru potlačení](media/preview-changes-in-suppression-file.png)

- V editoru **kódu** umístěte kurzor na řádek kódu s porušením a stisknutím rychlých akcí a **refaktoringů** (nebo stisknutím ctrl + **tečky (.)**) otevřete nabídku **Rychlé** akce. Vyberte **Potlačit CAXXXX** a potom v **části Soubor potlačení zvolte**. Zobrazí se náhled souboru [globálního potlačení,](#global-level-suppressions) který se vytvoří nebo upraví.

::: moniker range=">=vs-2019"

- V nabídce **Analyzovat** vyberte analyzovat sestavení a potlačit aktivní problémy na řádku nabídek, aby se  >   potlačovala všechna aktuální porušení. To se někdy označuje jako "základní" (baselining).

::: moniker-end
::: moniker range="vs-2017"

- V nabídce **Analyzovat** vyberte Analyzovat spuštění Code Analysis  >  **a Potlačit aktivní** problémy, aby se potlačovala všechna aktuální porušení. To se někdy označuje jako "základní" (baselining).
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>Potlačení porušení pomocí nastavení projektu

V **Průzkumník řešení** otevřete vlastnosti projektu (klikněte pravým tlačítkem na projekt a zvolte **Vlastnosti** (nebo stiskněte Alt **+ Enter)** a pomocí karty **Code Analysis** nakonfigurujte možnosti. Můžete například zakázat analýzu živého kódu nebo zakázat analyzátory .NET.

## <a name="suppress-violations-using-a-rule-set"></a>Potlačení porušení pomocí sady pravidel

V editoru **sady pravidel zrušte** zaškrtnutí políčka vedle názvu nebo nastavte **Action** na **None (Žádná).**

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>Potlačení ve zdroji a atribut SuppressMessage

Potlačení ve zdroji (ISS) používá <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atribut k potlačení upozornění. Atribut může být umístěn blízko segmentu kódu, který vygeneroval upozornění. Atribut můžete do zdrojového souboru přidat tak, že ho zadáte do , nebo ho můžete automaticky přidat pomocí místní nabídky u upozornění <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> **v Seznam chyb** souboru.

Atribut je podmíněný atribut, který je součástí metadat IL sestavení spravovaného kódu, pouze pokud je symbol kompilace CODE_ANALYSIS definován v době <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kompilace.

V jazyce C++/CLI přidejte atribut pomocí maker CA SUPPRESS MESSAGE nebo CA GLOBAL SUPPRESS_MESSAGE v souboru \_ \_ \_ \_ hlaviček.

> [!NOTE]
> V sestavách vydaných verzí byste neměli používat potlačení ve zdrojovém kódu, abyste zabránili nechtěnému přesouvání metadat potlačení ve zdroji. Z důvodu nákladů na zpracování potlačení v rámci zdroje je navíc možné snížit výkon vaší aplikace.

::: moniker range="vs-2017"

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2017, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit tak, že vyberete **analyzovat**  >  **Spustit analýzu kódu a potlačit aktivní problémy**.
>
> ![Spustit analýzu kódu a potlačit problémy v aplikaci Visual Studio](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

> [!NOTE]
> Pokud migrujete projekt do sady Visual Studio 2019, může dojít k náhlému vynechání velkého počtu upozornění analýzy kódu. Pokud nejste připraveni opravit upozornění, můžete je potlačit výběrem možnosti **analyzovat**  >  **sestavení a potlačit aktivní problémy**.

::: moniker-end

### <a name=&quot;suppressmessage-attribute&quot;></a>SuppressMessage – atribut

Když vyberete možnost **potlačit** z kontextu nebo v místní nabídce upozornění analýzy kódu v **Seznam chyb**, přidá se do <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> kódu nebo do globálního souboru potlačení projektu atribut.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>Atribut má následující formát:

```vb
<Scope:SuppressMessage(&quot;Rule Category&quot;, &quot;Rule Id&quot;, Justification = &quot;Justification&quot;, MessageId = &quot;MessageId&quot;, Scope = &quot;Scope&quot;, Target = &quot;Target")>
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

  - [`module`](#module-suppression-scope) – Tento obor potlačí upozornění na sestavení. Jedná se o globální potlačení, které platí pro celý projekt.

  - `resource` –[(jenom starší verze FxCop)](../code-quality/static-code-analysis-for-managed-code-overview.md) Tento obor potlačí upozornění v diagnostických informacích zapisných do souborů prostředků, které jsou součástí modulu (sestavení). Tento obor není čten nebo respektován v kompilátorech C#/VB pro diagnostiku analyzátoru Roslyn, který analyzuje pouze zdrojové soubory.

  - `type` – Tento obor potlačí upozornění na typ.

  - `member` – Tento obor potlačí upozornění na člena.

  - `namespace` – Tento obor potlačí upozornění na samotný obor názvů. Nepotlačuje upozornění na typy v rámci oboru názvů.

  - `namespaceanddescendants` – (Vyžaduje kompilátor verze 3.x nebo vyšší a Visual Studio 2019) Tento obor potlačí upozornění v oboru názvů a všech jeho následných symbolech. Starší `namespaceanddescendants` verze analýzy tuto hodnotu ignoruje.

- **Target** – identifikátor, který se používá k určení cíle, na kterém se upozornění potlačuje. Musí obsahovat plně kvalifikovaný název položky.

Když se zobrazí upozornění v Visual Studio, můžete zobrazit příklady tak, že přidáte potlačení do souboru `SuppressMessage` [globálního potlačení](../code-quality/use-roslyn-analyzers.md#suppress-violations). Atribut potlačení a jeho požadované vlastnosti se zobrazí v okně náhledu.

### <a name="suppressmessage-usage"></a>SuppressMessage usage

Code Analysis jsou potlačena na úrovni, na kterou je <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> atribut použit. Například atribut lze použít na úrovni sestavení, modulu, typu, člena nebo parametru. Účelem tohoto chování je těsně zmástět informace o potlačení s kódem, ve kterém k porušení dojde.

Obecná forma potlačení zahrnuje kategorii pravidla a identifikátor pravidla, který obsahuje volitelnou čitelnou reprezentaci názvu pravidla. Například:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

Pokud existují striktní důvody výkonu pro minimalizaci metadat potlačení ve zdroji, můžete název pravidla vynechat. Kategorie pravidla a ID pravidla společně tvoří dostatečně jedinečný identifikátor pravidla. Například:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

V případě důvodů zachování nedoporučujeme název pravidla vynechat.

### <a name="suppress-selective-violations-within-a-method-body"></a>Potlačit selektivní porušení v těle metody

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

### <a name="global-level-suppressions"></a>Potlačení na globální úrovni

Nástroj Analýza spravovaného kódu prověřuje `SuppressMessage` atributy, které jsou aplikovány na úrovni sestavení, modulu, typu, člena nebo parametru. Také se aktivují narušení proti prostředkům a oborům názvů. Tato porušení musí být použita na globální úrovni a mají rozsah a cíl. Například následující zpráva potlačuje porušení oboru názvů:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Potlačíte-li upozornění s `namespace` rozsahem, potlačí upozornění na samotný obor názvů. Nepotlačuje upozornění na typy v rámci oboru názvů.

Jakékoli potlačení lze vyjádřit zadáním explicitního oboru. Tato potlačení musí být na globální úrovni. Potlačení na úrovni členu nelze určit tím, že přerušujeme typ.

Potlačení na globální úrovni jsou jediným způsobem, jak potlačit zprávy odkazující na kód generovaný kompilátorem, který není namapovaný na explicitně poskytnutý zdroj uživatele. Například následující kód potlačí porušení proti konstruktoru generovanému kompilátorem:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` vždy obsahuje plně kvalifikovaný název položky.

#### <a name="global-suppression-file"></a>Soubor globálního potlačení

Soubor globálního potlačení udržuje potlačení, která jsou potlačeními na globální úrovni nebo potlačeními, která nezadat cíl. V tomto souboru jsou například uložena potlačení porušení na úrovni sestavení. Kromě toho jsou v ASP.NET uložená některá potlačení, protože nastavení na úrovni projektu není k dispozici pro kód za formulářem. Soubor globálního potlačení se vytvoří a přidá do projektu  při prvním výběru možnosti  V souboru potlačení projektu příkazu Potlačit v okně **Seznam chyb** souboru.

#### <a name="module-suppression-scope"></a>Rozsah potlačení modulu

Porušení kvality kódu pro celé sestavení můžete potlačit pomocí **oboru** modulu.

Například následující atribut v souboru projektu _GlobalSuppressions_ potlačí porušení zásady ConfigureAwait pro ASP.NET Core:

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>Vygenerovaný kód

Kompilátory spravovaného kódu a některé nástroje třetích stran generují kód pro usnadnění rychlého vývoje kódu. Kód generovaný kompilátorem, který se zobrazí ve zdrojových souborech, je obvykle označen `GeneratedCodeAttribute` atributem .

Pro analýzu zdrojového kódu můžete potlačit zprávy ve vygenerovaných kódech v `.editorconfig` souboru. Další informace najdete v tématu [Vyloučení generovaného kódu.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

Pro analýzu starší verze kódu můžete zvolit, zda chcete potlačit upozornění analýzy kódu a chyby pro vygenerovaný kód. Informace o tom, jak potlačit taková upozornění a chyby, naleznete v tématu [How to: potlačit upozornění pro generovaný kód](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Analýza kódu se ignoruje `GeneratedCodeAttribute` , když se použije na celé sestavení nebo na jeden parametr.

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Použití analyzátorů kódu](../code-quality/use-roslyn-analyzers.md)
