---
title: Pokyny pro tvorbu textových šablon T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 09ed896c85807da5a65084360fa62e24c3cca141
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896208"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Pokyny pro tvorbu textových šablon T4
Tyto obecné pokyny mohou být užitečné, pokud jsou generování programového kódu nebo jiných prostředků aplikace v sadě Visual Studio. Nejsou k nápravě pravidla.

## <a name="guidelines-for-design-time-t4-templates"></a>Pokyny pro šablony T4 návrhu
 Šablony T4 návrhu jsou šablony, které generují kód v projektu sady Visual Studio v době návrhu. Další informace najdete v tématu [vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Generovat proměnnou aspektech vaší aplikace.
Generování kódu je zvláště užitečná pro tyto aspekty aplikace, která může změnit během projektu, nebo se změní mezi různými verzemi aplikace. Tyto proměnné aspekty oddělte od více invariantní aspekty, tak, aby můžete snadněji určit, co se má vygenerovat. Například pokud vaše aplikace poskytuje web, samostatné standardní stránky obsluhující funkce od logiky, která definuje navigační cesty z jedné stránky na jiný.

 Kódování proměnné aspekty v jedné nebo více zdrojových modelů.
Model je soubor nebo databáze, která přečte každou šablonu k získání konkrétní hodnoty pro proměnné části kódu, který se má vygenerovat. Modelů může být databáze a soubory XML návrh, diagramů nebo jazyky specifickými pro doménu. Obvykle jeden model se používá ke generování mnoha soubory v projektu sady Visual Studio. Každý soubor je vygenerován ze samostatné šablony.

 V projektu můžete použít více než jeden model. Můžete definovat model pro navigaci mezi stránkami web a samostatný model pro rozložení stránky.

 Model zaměřte se na uživatelské požadavky a slovník, ne na implementaci.
Například v aplikaci Web, které očekáváte modelu, který má odkazovat na webové stránky a hypertextových odkazů.

 V ideálním případě zvolte způsob prezentace, která vyhovuje druh informací, které představuje model. Model navigačních cesty, které prostřednictvím webu může být například diagram polí a šipky.

 Otestujte generovaného kódu.
Použijte ruční nebo automatické testy k ověření, že výsledný kód pracuje uživatelé potřebují. Zabránění generování testů ze stejného modelu, ve kterém je kód vygenerován.

 V některých případech obecné testy můžete provést na modelu přímo. Můžete například napsat test, který zajistí, že každé stránky na webu může být dosažitelný podle navigace z jiného.

 Povolit pro vlastní kód: generovat částečné třídy.
Povolit pro kód, který píšete ručně kromě pro vygenerovaný kód. Neobvyklé, že schéma generování kódu budete moci účet pro všechny možné změny, které mohou nastat. Proto by se měl přidat nebo přepsat vygenerovaný kód. Kde generované materiál je v jazyce .NET, jako [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] nebo [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], jsou zvláště užitečné dvou strategií:

- Generované třídy by měl být neúplná. Umožňuje přidávat obsah do generovaného kódu.

- Třídy by měly být generovány v párech, jeden z nich dědí. Základní třída by měla obsahovat všechny generované metody a vlastnosti a odvozená třída může obsahovat pouze konstruktory. To umožňuje ručně psanou k přepsání metod generovaného kódu.

  V jiných generované jazycích, jako jsou XML, použijte `<#@include#>` směrnice jednoduché kombinacích ručně psanou a vygenerovaný obsah. Ve složitějších případech bude pravděpodobně pro zápis, který kombinuje vygenerovaný soubor se všechny soubory ručně psanou krok následného zpracování.

  Přesunout běžné materiálu zahrnutých souborech nebo šablony běhu, aby se zabránilo zopakujete podobné bloky textu a kódu ve více šablonách, použijte `<#@ include #>` směrnice. Další informace najdete v tématu [T4 – direktiva zahrnují](../modeling/t4-include-directive.md).

  Můžete také vytvářet šablony textu za běhu v samostatném projektu a pak je volejte z šablony návrhu. Chcete-li to provést, použijte `<#@ assembly #>` směrnice pro přístup k samostatného projektu. Příklady najdete v tématu ["Dědičnosti v textových šablon" v blogu Garetha Jonese](http://go.microsoft.com/fwlink/?LinkId=208373).

  Zvažte přesunutí velkých bloků kódu do samostatného sestavení.
  Pokud máte velké kód bloky a bloky s funkcí třídy, může být užitečné k přesunutí některé tento kód do metody, které se kompilují do samostatného projektu. Můžete použít `<#@ assembly #>` směrnice získat přístup ke kódu v šabloně. Další informace najdete v tématu [T4 – Direktiva Assembly](../modeling/t4-assembly-directive.md).

  Metody můžete umístit v abstraktní třída může dědit vlastnosti šablony. Abstraktní třída musí dědit z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Další informace najdete v tématu [T4 – direktiva Template](../modeling/t4-template-directive.md).

  Generovat kód, není konfigurace soubory jedním ze způsobů vytváření proměnných aplikace je zapsat obecný programový kód, který přijímá konfigurační soubor. Aplikace napsané tímto způsobem je velmi flexibilní a můžete překonfigurovat při změně obchodních požadavků, bez nutnosti opětovného sestavení aplikace. Nevýhod tohoto přístupu je, že aplikace budou provádět méně dobře než konkrétnější aplikace. Také jeho kód programu bude obtížné číst a spravovat, částečně, protože má vždy řešit nejvíce obecných typů.

  Oproti tomu může být silného typu aplikace, jejichž proměnné části jsou generovány před kompilací. Díky tomu je mnohem jednodušší a spolehlivější a napsat ručně psanou kód ji integrovat s generované částí softwaru.

  Pokud chcete získat úplné výhodou generování kódu, pokusu o generování programového kódu namísto konfigurační soubory.

  Použijte kód generovaný složky umístěte šablony a generované soubory ve složce projektu s názvem **kód generovaný**, aby byl vymazat, že se nejedná soubory, které by měl být upravován přímo. Pokud vytvoříte vlastní kód pro přepsání nebo přidat do generované třídy, umístěte do složky s názvem tyto třídy **vlastního kódu**. Struktura obvyklou pro projekty vypadá takto:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Pokyny pro šablony T4 za běhu (Předzpracovaných)
 Přesunout běžné materiál do zděděné šablon můžete dědičnost sdílet metody a bloky textu mezi textových šablon T4. Další informace najdete v tématu [T4 – direktiva Template](../modeling/t4-template-directive.md).

 Můžete také zahrnout soubory, které mají šablony běhu.

 Přesuňte velké části kódu do částečné třídy.
Každá šablona běhu generuje definice částečné třídy, která má stejný název jako šablona. Můžete napsat kód soubor, který obsahuje jiné částečné deklaraci stejné třídy. Do třídy tímto způsobem můžete přidat metody, pole a konstruktory. Tyto členy můžete volat z bloků kódu v šabloně.

 Výhodou to je, že kód je snazší psát, protože technologie IntelliSense není k dispozici. Kromě toho můžete dosáhnout lepší oddělení mezi prezentaci a logiku.

 Například v **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 V **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Povolit pro vlastní kód: poskytují Rozšiřovací body zvažte generování virtuální metody v \<#+ třídy funkce blokuje #>. To umožňuje jediné šabloně pro použití v mnoha kontextech beze změn. Místo úpravy šablony, můžete vytvořit odvozené třídy, která zajišťuje minimální další logiku. Odvozená třída může být buď regulárních kódu nebo může být šablona běhu.

 Například v MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

 V kódu aplikace:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Pokyny pro všechny šablony T4
 Samostatné shromažďování dat z generování textu, zkuste se vyhnout kombinování výpočetní výkon a textové bloky. V každé textové šablony, použijte první \<kód # block #> k nastavení proměnných a provádění složitých výpočtů. Z první blok textu na konec šablony nebo první \<funkci třídy #+ blokovat #>, vyhněte se dlouho výrazy a vyhnout se tak smyček a podmíněné výrazy pokud neobsahují textové bloky. Tento postup vytvoří šablonu čitelnější a udržovat.

 Nepoužívejte `.tt` pro zahrnout soubory používají jinou příponu, jako `.ttinclude` vložených souborů. Použití `.tt` pouze pro soubory, které mají být zpracovány jako za běhu nebo návrhových textových šablon. V některých případech může sada Visual Studio rozpozná `.tt` soubory a automaticky nastaví jeho vlastnosti pro zpracování.

 Spuštění každou šablonu jako dlouhodobý prototyp.
Zápis příklad kódu nebo textu, který chcete vygenerovat a ujistěte se, zda je správný. Potom změňte jeho příponu na .tt a postupně vkládat kód, který upraví obsah tak čtení modelu.

 Zvažte použití typu modelů.
I když můžete vytvořit schéma XML nebo databáze pro modely, může být užitečné k vytvoření jazyka specifického pro doménu (DSL). DSL má výhodu v tom, že se vygeneruje třídu pro každý uzel ve schématu a vlastnosti představují atributy. To znamená, že můžete naprogramovat z hlediska obchodní model. Příklad:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Zvažte použití diagramů pro své modely.
Mnoho modelů prezentovány a co nejefektivněji spravovat jednoduše jako text tabulek, zejména v případě, že jsou velmi velké.

 Však pro některé druhy obchodní požadavky, je důležité, abyste zjednodušili komplexní sadu vztahů a pracovním postupům a diagramy se nejlíp hodí střední. Výhodou diagramu je, že je snadno můžete projednávat s uživateli a další zainteresované uživatele. Generování kódu z modelu na úrovni obchodní požadavky, se být váš kód zvýšení flexibility při změně požadavků.

 Vlastní typ diagramu můžete také navrhnout jako jazyka specifického pro doménu (DSL). Kód lze vygenerovat z UML a DSL. Další informace najdete v tématu [analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Viz také

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
