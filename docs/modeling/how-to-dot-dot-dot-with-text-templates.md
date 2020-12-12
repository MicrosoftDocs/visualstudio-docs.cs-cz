---
title: Postupy pro textové šablony
description: Přečtěte si o odpovědích na časté otázky, které se vyskytly při použití textových šablon k vygenerování textu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50844ce8c6943fcf6b2a0b91c7fd2cfcb6184094
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363182"
---
# <a name="how-to--with-text-templates"></a>Postupy pro textové šablony
Textové šablony v aplikaci Visual Studio poskytují užitečný způsob, jak vygenerovat text libovolného druhu. Můžete použít textové šablony k vygenerování textu v době běhu jako součást vaší aplikace a v době návrhu k vygenerování kódu projektu. Toto téma shrnuje nejčastější dotaz "Návody...?" otázky.

 V tomto tématu jsou více odpovědí předcházících odrážkami alternativní návrhy.

 Obecné seznámení s textovými šablonami najdete v článku [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="how-to-"></a>Jak...

### <a name="generate-part-of-my-application-code"></a>Vygenerovat část kódu mé aplikace
 V souboru nebo v databázi mám konfigurační nebo *model* . Jedna nebo více částí vlastního kódu závisí na tomto modelu.

- Generování některých souborů kódu z textových šablon. Další informace najdete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) a [Jaký je nejlepší způsob, jak začít psát šablonu?](#starting).

### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generovat soubory za běhu a předávání dat do šablony
 V době běhu moje aplikace generuje textové soubory, jako jsou sestavy, které obsahují kombinaci standardního textu a dat. Chci se vyhnout psaní stovek `write` příkazů.

- Přidejte do projektu textovou šablonu modulu runtime. Tato šablona vytvoří třídu ve vašem kódu, kterou lze vytvořit a použít k vygenerování textu. Do této třídy můžete předat data v parametrech konstruktoru. Další informace najdete v tématu [generování textu v době běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

- Pokud chcete generovat ze šablon, které jsou k dispozici pouze v době běhu, můžete použít standardní textové šablony. Pokud píšete rozšíření sady Visual Studio, můžete vyvolat službu šablonování textu. Další informace najdete v tématu [vyvolání transformace textu v rozšíření vs](../modeling/invoking-text-transformation-in-a-vs-extension.md). V jiných kontextech můžete použít modul text šablonování. Další informace naleznete v tématu <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.

     \<#@parameter#>K předání parametrů těmto šablonám Použijte direktivu. Další informace naleznete v tématu [direktiva parametru T4](../modeling/t4-parameter-directive.md).

### <a name="read-another-project-file-from-a-template"></a>Načíst jiný soubor projektu ze šablony
 Chcete-li číst soubor ze stejného projektu sady Visual Studio jako šablonu:

- Vložte `hostSpecific="true"` do `<#@template#>` direktivy.

     V kódu použijte `this.Host.ResolvePath(filename)` k získání úplné cesty k souboru.

### <a name="invoke-methods-from-a-template"></a>Vyvolání metod ze šablony

Pokud metody již existují, například v třídách .NET:

- Použijte \<#@assembly#> direktivu pro načtení sestavení a použijte \<#@import#> k nastavení kontextu oboru názvů. Další informace najdete v tématu [direktiva T4 pro import](../modeling/t4-import-directive.md).

   Pokud často používáte stejnou sadu direktiv sestavení a importu, zvažte vytvoření procesoru direktiv. V každé šabloně můžete vyvolat procesor direktiv, který může načíst sestavení a soubory modelu a nastavit kontext oboru názvů. Další informace najdete v tématu [vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

Pokud píšete metody sami:

- Pokud píšete šablonu textu za běhu, napište definici částečné třídy, která má stejný název jako textová šablona za běhu. Do této třídy přidejte další metody.

- Zapište řídicí blok funkcí třídy, `<#+ ... #>` ve kterém lze deklarovat metody, vlastnosti a soukromé třídy. Je-li šablona textu kompilována, je transformována na třídu. Standardní řídicí bloky `<#...#>` a text jsou transformovány na jedinou metodu a bloky funkcí třídy jsou vloženy jako samostatné členy. Další informace naleznete v tématu [ovládací bloky textové šablony](../modeling/text-template-control-blocks.md).

   Metody definované jako funkce třídy mohou také obsahovat vložené textové bloky.

   Zvažte umístění funkcí třídy do samostatného souboru, který lze použít `<#@include#>` do jednoho nebo více souborů šablon.

- Zapište metody v samostatném sestavení (knihovny tříd) a zavolejte je ze šablony. Pomocí `<#@assembly#>` direktivy načtěte sestavení a `<#@import#>` nastavte kontext oboru názvů. Všimněte si, že pokud chcete sestavení znovu sestavit během ladění, může být nutné zastavit a restartovat aplikaci Visual Studio. Další informace naleznete v tématu [direktivy textové šablony T4](../modeling/t4-text-template-directives.md).

### <a name="generate-many-files-from-one-model-schema"></a>Generování mnoha souborů z jednoho schématu modelu
 Pokud často generujete soubory z modelů, které mají stejné schéma XML nebo databáze:

- Zvažte vytvoření procesoru direktiv. To umožňuje nahradit více příkazů sestavení a příkazy import v každé šabloně s jednou vlastní direktivou. Procesor direktiv může také načíst a analyzovat soubor modelu. Další informace najdete v tématu [vytváření vlastních procesorů pro direktivy textových šablon T4](../modeling/creating-custom-t4-text-template-directive-processors.md).

### <a name="generate-files-from-a-complex-model"></a>Generování souborů ze komplexního modelu

- Zvažte vytvoření jazyka specifického pro doménu (DSL), který bude představovat model. To usnadňuje psaní šablon, protože používáte typy a vlastnosti, které odpovídají názvům elementů v modelu. Nemusíte analyzovat soubor nebo procházet uzly XML. Příklad:

     `foreach (Book book in this.Library) { ... }`

     Další informace najdete v tématu [Začínáme s Domain-Specific jazyky](../modeling/getting-started-with-domain-specific-languages.md) a [generování kódu z Domain-Specificho jazyka](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="get-data-from-visual-studio"></a>Získat data ze sady Visual Studio
 Chcete-li použít služby poskytované v aplikaci Visual Studio, nastavte `hostSpecific` atribut a načtěte `EnvDTE` sestavení. Příklad:

```csharp
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ assembly name="EnvDTE" #>
<#
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));
#>

Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>
```

### <a name="execute-text-templates-in-the-build-process"></a>Spouštění textových šablon v procesu sestavení

- Další informace naleznete v tématu [generování kódu v procesu sestavení](../modeling/code-generation-in-a-build-process.md).

## <a name="more-general-questions"></a>Obecnější otázky

### <a name="what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a> Jaký je nejlepší způsob, jak začít psát textovou šablonu?

1. Zapište konkrétní příklad vygenerovaného souboru.

2. Převeďte ji na textovou šablonu vložením `<#@template #>` direktivy a direktiv a kódu, které jsou požadovány pro načtení vstupního souboru nebo modelu.

3. Postupně nahradí části souboru pomocí výrazů a bloků kódu.

### <a name="what-is-a-model"></a>Co je "model"?

- Vstup přečte vaše šablona. Může to být v souboru nebo v databázi. Může to být XML nebo vykreslování Visia nebo jazyk DSL (Domain-Specific Language) nebo model UML, nebo může být prostý text. Může být rozložená mezi několik souborů. Obvykle více než jedna šablona čte jeden model.

     Namnožení pojmu "model" znamená, že představuje nějaký aspekt vaší společnosti přímo než generovaný kód programu nebo jiné soubory. Například může představovat plán komunikační sítě, na kterou se vygenerovaný software bude dohlížet.

### <a name="what-is-the-benefit-of-using-text-templates"></a>Jaká je výhoda použití textových šablon?
 Obvykle generujete více kódů nebo jiných souborů z jednoho modelu. Model představuje více požadavků přímo než generovaný kód. Vynechává detailní implementaci a je zapsána z požadavků, nikoli kódu. Když se požadavky mění – stejně jako obvykle – můžete model aktualizovat snadněji a spolehlivější než jednotlivé části kódu programu.

 Generování kódu je proto cenným nástrojem z perspektivy agilních metod vývoje.

### <a name="what-best-practices-are-there-for-text-templates"></a>Jaké "osvědčené postupy" jsou pro textové šablony?

- Další informace najdete v tématu [pokyny pro psaní textových šablon T4](../modeling/guidelines-for-writing-t4-text-templates.md).

### <a name="what-is-t4"></a>Co je T4?

- Další název možností textových šablon sady Visual Studio, které jsou popsány zde. Předchozí verze, která nebyla publikována, byla zkratka pro "transformace textové šablony".
