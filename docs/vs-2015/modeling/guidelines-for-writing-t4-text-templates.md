---
title: Pokyny pro psaní textových šablon T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d1e15a8c00a0614d020defd2df7b06665289a8b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666054"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Pokyny pro tvorbu textových šablon T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tyto obecné pokyny mohou být užitečné, pokud generujete kód programu nebo jiné prostředky aplikace v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nejedná se o pevná pravidla.

## <a name="guidelines-for-design-time-t4-templates"></a>Pokyny pro šablony T4 v době návrhu
 Šablony T4 v době návrhu jsou šablony, které generují kód v projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v době návrhu. Další informace najdete v tématu [generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Vygenerujte aspekty proměnných aplikace.
Generování kódu je nejužitečnější pro tyto aspekty aplikace, které se mohou změnit během projektu, nebo se změní mezi různými verzemi aplikace. Jednotlivé aspekty proměnných oddělte z dalších nevariantních aspektů, abyste mohli snadněji určit, co má být vygenerováno. Například pokud vaše aplikace poskytuje web, oddělte standardní stránku obsluhující funkce z logiky, která definuje navigační cesty z jedné stránky na druhou.

 Zakódovat aspekty proměnných v jednom nebo více zdrojových modelech.
Model je soubor nebo databáze, které Každá šablona načítá pro získání konkrétních hodnot proměnných kódu, který má být vygenerován. Modely můžou být databáze, soubory XML vlastního návrhu, diagramů nebo jazyků specifických pro doménu. Typicky jeden model se používá ke generování mnoha souborů v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Jednotlivé soubory jsou vygenerovány ze samostatné šablony.

 V projektu můžete použít více než jeden model. Můžete například definovat model navigace mezi webovými stránkami a samostatný model pro rozložení stránek.

 Zaměřte se na potřeby uživatelů a slovník, ne na implementaci.
Například v aplikaci webu byste očekávali, že model bude odkazovat na webové stránky a hypertextové odkazy.

 V ideálním případě vyberte formu prezentace, která bude vyhovovat druhu informací, které model představuje. Například model navigačních cest prostřednictvím webu může být diagramem polí a šipek.

 Otestujte generovaný kód.
Pomocí ručních nebo automatizovaných testů ověřte, zda výsledný kód funguje tak, jak uživatelé vyžadují. Vyhněte se generování testů ze stejného modelu, ze kterého je generován kód.

 V některých případech lze obecné testy provádět přímo v modelu. Můžete například napsat test, který zajistí, že na každou stránku na webu lze dosáhnout navigace z jiné.

 Povolení pro vlastní kód: generování částečných tříd.
Umožněte, aby kód, který píšete rukou, byl kromě vygenerovaného kódu. Není neobvyklé, že pro schéma generování kódu bude možné přihlédnout ke všem možným variantám, které by mohly nastat. Proto byste měli očekávat, že chcete přidat nebo přepsat některý z generovaný kód. Pokud je vygenerovaný materiál v jazyce .NET, jako je například [!INCLUDE[csprcs](../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], jsou obzvláště užitečné dvě strategie:

- Generované třídy by měly být částečné. To umožňuje přidat obsah do vygenerovaného kódu.

- Třídy by měly být vygenerovány ve dvojicích, jedna dědí z druhé. Základní třída by měla obsahovat všechny vygenerované metody a vlastnosti a odvozená třída by měla obsahovat pouze konstruktory. To umožňuje vašemu ručnímu kódu přepsat kteroukoli z vygenerovaných metod.

  V jiných generovaných jazycích, jako je XML, použijte direktivu `<#@include#>` k provádění jednoduchých kombinací ručně napsaných a generovaných obsahu. Ve složitějších případech možná budete muset napsat krok následného zpracování, který kombinuje vygenerovaný soubor se všemi ručně zapsanými soubory.

  Přesuňte společný materiál do zahrnutých souborů nebo šablon run-time, aby nedocházelo k opakujícím se podobným blokům textu a kódu ve více šablonách, použijte direktivu `<#@ include #>`. Další informace najdete v tématu [direktiva T4 include](../modeling/t4-include-directive.md).

  V samostatném projektu můžete také vytvořit textové šablony Run-Time a pak je volat pomocí šablony pro dobu návrhu. K tomu použijte direktivu `<#@ assembly #>` pro přístup k samostatnému projektu.

  Zvažte přesunutí velkých bloků kódu do samostatného sestavení.
  Pokud máte velké bloky kódu a bloky funkcí třídy, může být užitečné přesunout část tohoto kódu do metod, které kompilujete v samostatném projektu. Pro přístup k kódu v šabloně můžete použít direktivu `<#@ assembly #>`. Další informace naleznete v tématu [direktiva T4 pro sestavení](../modeling/t4-assembly-directive.md).

  Metody lze umístit do abstraktní třídy, kterou může šablona dědit. Abstraktní třída musí dědit z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Další informace najdete v tématu [direktiva šablony T4](../modeling/t4-template-directive.md).

  Generování kódu, nikoli konfiguračních souborů jedna metoda zápisu proměnné aplikace je napsat obecný kód programu, který přijímá konfigurační soubor. Aplikace napsaná tímto způsobem je velmi flexibilní a je možné ji překonfigurovat, když se změní obchodní požadavky, aniž by bylo nutné aplikaci znovu sestavit. Nevýhodou tohoto přístupu je však, že aplikace bude provádět méně dobře než konkrétní aplikace. I jeho programový kód bude obtížnější číst a udržovat, částečně z toho důvodu, že se vždy zabývat nejobecnější typy.

  Naproti tomu aplikace, jejíž proměnné jsou generovány před kompilací, může být silného typu. To je mnohem jednodušší a spolehlivější pro zápis rukou psaného kódu a jeho integraci s generovanými částmi softwaru.

  Chcete-li získat úplný přínos pro generování kódu, pokuste se vygenerovat kód programu místo konfiguračních souborů.

  Pomocí vygenerované složky kódu umístěte šablony a generované soubory do složky projektu s názvem **generovaný kód**, aby bylo jasné, že se nejedná o soubory, které by se měly upravovat přímo. Pokud vytvoříte vlastní kód pro přepsání nebo přidání do generovaných tříd, umístěte tyto třídy do složky, která má název **vlastní kód**. Struktura typického projektu vypadá takto:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Pokyny pro šablony s podporou procesu run-time (předzpracované) T4
 Přesunout společný materiál do děděných šablon: dědičnost můžete použít ke sdílení metod a textových bloků mezi textovými šablonami T4. Další informace najdete v tématu [direktiva šablony T4](../modeling/t4-template-directive.md).

 Můžete také použít vložené soubory, které mají šablony Run-Time.

 Přesuňte velké části kódu do částečné třídy.
Každá šablona za běhu generuje definici částečné třídy, která má stejný název jako šablona. Můžete napsat soubor kódu, který obsahuje další částečnou definici stejné třídy. Tímto způsobem můžete přidat metody, pole a konstruktory do třídy. Tyto členy mohou být volány z bloků kódu v šabloně.

 Výhodou je, že kód je snazší psát, protože je k dispozici IntelliSense. Můžete také dosáhnout lepšího oddělení prezentace a základní logiky.

 Například v **MyReportText.TT**:

 `The total is: <#= ComputeTotal() #>`

 V **MyReportText-Methods.cs**:

 `private string ComputeTotal() { ... }`

 Povolení pro vlastní kód: poskytnutí rozšiřujících bodů zvažte generování virtuálních metod v \< # + třídy funkcí Blocks # >. Tato možnost umožňuje použít jedinou šablonu v mnoha kontextech bez úprav. Místo změny šablony můžete vytvořit odvozenou třídu, která poskytuje minimální další logiku. Odvozená třída může být buď pravidelný kód, nebo může být šablonou run-time.

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
 Oddělení shromažďování dat od generování textu se snažte vyhnout kombinování výpočetních a textových bloků. V každé textové šabloně použijte první \< # Code Block # > k nastavení proměnných a provádění složitých výpočtů. Od prvního bloku textu až po konec šablony nebo první \< # + třídy bloku funkce # >, vyhněte se dlouhým výrazům a vyhněte se cyklům a podmíněným výjimkám, pokud neobsahují textové bloky. Tento postup usnadňuje čtení a údržbu šablony.

 Nepoužívejte `.tt` pro vložené soubory použijte jinou příponu názvu souboru, například `.ttinclude` pro zahrnuté soubory. Použijte `.tt` jenom pro soubory, které chcete zpracovat buď jako textové šablony Run-Time nebo v době návrhu. V některých případech [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpozná `.tt` soubory a automaticky nastaví jejich vlastnosti ke zpracování.

 Spusťte každou šablonu jako pevný prototyp.
Napište příklad kódu nebo textu, který chcete vygenerovat, a ujistěte se, že je správný. Pak změňte jeho příponu na. TT a přírůstkově vložte kód, který upraví obsah, a to tak, že načtou model.

 Zvažte použití typových modelů.
I když můžete vytvořit schéma XML nebo databáze pro vaše modely, může být užitečné vytvořit jazyk specifický pro doménu (DSL). DSL má výhodu, že generuje třídu, která představuje každý uzel ve schématu a vlastnosti pro reprezentaci atributů. To znamená, že můžete programovat na základě obchodního modelu. Příklad:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Zvažte použití diagramů pro vaše modely.
Mnoho modelů je efektivně prezentováno a spravováno jednoduše jako textové tabulky, zejména v případě, že jsou velmi velké.

 U některých druhů obchodních požadavků ale je důležité objasnit složitou sadu vztahů a pracovních toků a diagramy představují nejvhodnější médium. Výhodou diagramu je, že je snadné diskutovat s uživateli a dalšími zúčastněnými stranami. Vygenerováním kódu z modelu na úrovni obchodních požadavků zajistíte flexibilitu kódu při změně požadavků.

 Diagramy tříd a aktivit UML je často možné přizpůsobit pro tyto účely. Můžete také navrhnout vlastní typ diagramu jako jazyk specifický pro doménu (DSL). Kód lze vygenerovat z UML i z DSL. Další informace najdete v tématu [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md) a [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Viz také
 [Generování kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) při [generování textu za běhu s textovými šablonami T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
