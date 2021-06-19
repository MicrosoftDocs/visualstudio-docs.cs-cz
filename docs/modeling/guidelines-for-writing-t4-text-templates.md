---
title: Pokyny pro tvorbu textových šablon T4
description: Přečtěte si obecné pokyny, které jsou užitečné, pokud generujete programový kód nebo jiné prostředky aplikace v Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f043e95ef477558028e634bf6b48aded2960ec2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386654"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Pokyny pro tvorbu textových šablon T4

Tyto obecné pokyny můžou být užitečné, pokud generujete programový kód nebo jiné prostředky aplikace v Visual Studio. Nejsou to pevná pravidla.

## <a name="guidelines-for-design-time-t4-templates"></a>Pokyny pro Design-Time T4

Šablony T4 v době návrhu jsou šablony, které generují kód v Visual Studio projektu v době návrhu. Další informace najdete v tématu [Generování kódu při návrhu pomocí textových šablon T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Vygenerování proměnných aspektů aplikace

Generování kódu je nejužitečnější pro ty aspekty aplikace, které se můžou během projektu změnit nebo se budou měnit mezi různými verzemi aplikace. Oddělte tyto aspekty proměnných od invariantnějších aspektů, abyste mohli snadněji určit, co se má vygenerovat. Pokud například vaše aplikace poskytuje web, oddělte standardní funkce obsluhující stránky od logiky, která definuje navigační cesty z jedné stránky na druhou.

Kódujte aspekty proměnných v jednom nebo více zdrojových modelech.

Model je soubor nebo databáze, které každá šablona čte, aby získala konkrétní hodnoty pro proměnlivé části kódu, které se mají vygenerovat. Modely mohou být databáze, soubory XML vašeho vlastního návrhu, diagramy nebo jazyky specifické pro doménu. Jeden model se obvykle používá k vygenerování mnoha souborů v Visual Studio projektu. Každý soubor se generuje ze samostatné šablony.

V projektu můžete použít více než jeden model. Můžete například definovat model pro navigaci mezi webovými stránkami a samostatný model pro rozložení stránek.

Zaměřte model na potřeby a slovní zásoby uživatelů, ne na vaši implementaci.

Například v aplikaci webu byste očekávali, že model bude odkazovat na webové stránky a hypertextové odkazy.

V ideálním případě zvolte takovou formu prezentace, která vyhovuje druhu informací, které model představuje. Příkladem modelu navigačních cest přes web může být diagram polí a šipek.

Otestujte vygenerovaný kód.

Pomocí ručních nebo automatizovaných testů ověřte, že výsledný kód funguje tak, jak to uživatelé vyžadují. Vyhněte se generování testů ze stejného modelu, ze kterého je kód generován.

V některých případech lze obecné testy provést přímo na modelu. Můžete například napsat test, který zajistí, že každá stránka na webu bude přístupná z jakékoli jiné stránky.

Povolit pro vlastní kód: vygeneruje částečné třídy.

Kromě generovaného kódu povolte i kód, který napíšete ručně. Je neobvyklé, že schéma generování kódu dokáže zohlednit všechny možné variace, které mohou nastat. Proto byste měli očekávat, že přidáte nebo přepíšete některý z vygenerovaný kód. Pokud je vygenerovaný materiál v jazyce .NET, jako je C# nebo Visual Basic, jsou obzvláště užitečné dvě strategie:

- Vygenerované třídy by měly být částečné. To vám umožní přidat obsah do generovaného kódu.

- Třídy by měly být generovány v párech, jedna dědí od druhé. Základní třída by měla obsahovat všechny vygenerované metody a vlastnosti a odvozená třída by měla obsahovat pouze konstruktory. To umožňuje ručně psaný kód přepsat libovolnou z vygenerované metody.

V jiných generovaných jazycích, jako je NAPŘÍKLAD XML, použijte direktivu k vytvoření jednoduchých kombinací ručně psaný a `<#@include#>` vygenerovaný obsah. Ve složitějších případech možná budete muset napsat krok po zpracování, který kombinuje vygenerovaný soubor s ručně napsanými soubory.

Přesuňte běžné materiály do souborů zahrnutí nebo šablon za běhu.

Chcete-li se vyhnout opakování podobných bloků textu a kódu ve více šablonách, použijte `<#@ include #>` direktivu . Další informace najdete v tématu [T4 Include – direktiva](../modeling/t4-include-directive.md).

Textové šablony za běhu můžete také sestavit v samostatném projektu a pak je volat ze šablony pro návrh. Chcete-li to provést, `<#@ assembly #>` použijte direktivu pro přístup k samostatnému projektu.

Zvažte přesunutí velkých bloků kódu do samostatného sestavení.

Pokud máte velké bloky kódu a bloky funkcí třídy, může být užitečné přesunout část tohoto kódu do metod, které zkompilujte v samostatném projektu. Direktivu můžete `<#@ assembly #>` použít pro přístup ke kódu v šabloně. Další informace najdete v tématu [Direktiva sestavení T4](../modeling/t4-assembly-directive.md).

Metody můžete umístit do abstraktní třídy, kterou šablona může dědit. Abstraktní třída musí dědit z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> třídy . Další informace najdete v tématu [Direktiva šablony T4](../modeling/t4-template-directive.md).

Vygenerování kódu, ne konfiguračních souborů

Jednou z metod zápisu proměnné aplikace je napsat obecný programový kód, který přijímá konfigurační soubor. Aplikace napsaná tímto způsobem je velmi flexibilní a lze ji překonfigurovat při změně obchodních požadavků bez opětovného sestavení aplikace. Nevýhodou tohoto přístupu ale je, že aplikace bude výkonnější než konkrétnější aplikace. Také kód programu bude obtížnější číst a udržovat, částečně proto, že se vždy musí zabývat nejoobecnámi typy.

Naproti tomu aplikace, jejíž části proměnných se generují před kompilací, může být silného typu. Díky tomu je mnohem jednodušší a spolehlivější psát ručně psaný kód a integrovat ho s generovanými částmi softwaru.

Pokud chcete získat plnou výhodu generování kódu, zkuste místo konfiguračních souborů vygenerovat programový kód.

Použijte složku Vygenerovaný kód.

Umístěte šablony a vygenerované soubory do složky projektu s názvem **Vygenerovaný** kód, aby bylo jasné, že se jedná o soubory, které by se měly přímo upravit. Pokud vytvoříte vlastní kód pro přepsání nebo přidání do generovaných tříd, umístěte tyto třídy do složky s názvem **Vlastní kód**. Struktura typického projektu vypadá takhle:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Pokyny pro Run-Time (předzpracované) šablony T4

Přesuňte běžné materiály do zděděných šablon.

Dědičnost můžete použít ke sdílení metod a textových bloků mezi textovou šablonou T4. Další informace najdete v tématu [Direktiva šablony T4](../modeling/t4-template-directive.md).

Můžete také použít zahrnuté soubory, které mají šablony za běhu.

Přesuňte velká těla kódu do částečné třídy.

Každá šablona za běhu generuje částečnou definici třídy, která má stejný název jako šablona. Můžete napsat soubor kódu, který obsahuje další částečnou definici stejné třídy. Tímto způsobem můžete do třídy přidat metody, pole a konstruktory. Tyto členy lze volat z bloků kódu v šabloně.

Výhodou toho je, že kód se snadněji píše, protože technologie IntelliSense je k dispozici. Můžete také dosáhnout lepšího rozdělení mezi prezentací a základní logikou.

Například v **MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

V **souboru MyReportText-Methods.cs:**

`private string ComputeTotal() { ... }`

Povolit pro vlastní kód: uveďte ná přípony.

Zvažte generování virtuálních metod v \<#+ class feature blocks #> . To umožňuje použití jedné šablony v mnoha kontextech beze změn. Místo úpravy šablony můžete vytvořit odvozenou třídu, která poskytuje minimální dodatečnou logiku. Odvozenou třídou může být buď běžný kód, nebo šablona za běhu.

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

Oddělte shromažďování dat od generování textu.

Snažte se vyhnout kombinaci výpočetních bloků a textových bloků. V každé textové šabloně použijte první k nastavení proměnných a \<# code block #> provádění složitých výpočtů. Od prvního textového bloku až po konec šablony nebo prvního se vyhněte dlouhým výrazům a vyhněte se smyčkám a podmíněným výrazům, pokud neobsahují \<#+ class feature block #> textové bloky. Tento postup usnadňuje čtení a údržbu šablony.

Nepoužívejte pro `.tt` zahrnuté soubory.

Použijte jinou příponu názvu souboru, například `.ttinclude` pro zahrnuté soubory. Použijte pouze pro soubory, které chcete zpracovat jako textové šablony za běhu nebo `.tt` návrhu. V některých případech Visual Studio soubory a `.tt` automaticky nastaví jejich vlastnosti pro zpracování.

Každou šablonu spusťte jako pevný prototyp.

Napište příklad kódu nebo textu, který chcete vygenerovat, a ujistěte se, že je správný. Potom změňte jeho příponu na .tt a přírůstkově vložte kód, který upraví obsah čtením modelu.

Zvažte použití typových modelů.

I když můžete vytvořit XML nebo schéma databáze pro vaše modely, může být užitečné vytvořit jazyk domény specifické (DSL). DSL má výhodu, že generuje třídu pro reprezentaci každého uzlu ve schématu a vlastnosti reprezentující atributy. To znamená, že můžete programovat z hlediska obchodního modelu. Příklad:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

Zvažte použití diagramů pro vaše modely.

Mnoho modelů je nejuceněji prezentovaných a spravovaných jednoduše jako textové tabulky, zejména pokud jsou velmi velké.

U některých druhů obchodních požadavků je však důležité objasnit složité sady relací a pracovních toků a diagramy jsou nejlépe vhodné médium. Výhodou diagramu je, že se snadno diskutuje s uživateli a dalšími zúčastněnými stranami. Generováním kódu z modelu na úrovni obchodních požadavků můžete kód flexibilnější, když se požadavky změní.

Můžete také navrhnout vlastní typ diagramu jako jazyk specifický pro doménu (DSL). Kód lze generovat z UML i DSL. Další informace najdete v tématu [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Viz také

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generování textu za běhu pomocí textových šablon T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
