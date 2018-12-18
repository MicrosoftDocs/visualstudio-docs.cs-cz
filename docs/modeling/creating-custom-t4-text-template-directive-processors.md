---
title: Vytváření vlastních procesorů pro direktivy textových šablon T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0216fab44ddc52c2d01c27365449377fb899e1a6
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859650"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Vytváření vlastních procesorů pro direktivy textových šablon T4

*Proces transformace textových šablon* přijímá *textové šablony* soubor jako vstup a vytvoří textový soubor jako výstup. *Modul transformace textové šablony* procesu a modul komunikuje se službou hostitele transformace textových šablon a textové šablony pro jeden nebo více ovládacích prvků *procesorů pro direktivy* dokončit proces. Další informace najdete v tématu [proces transformace textových šablon](../modeling/the-text-template-transformation-process.md).

Vytvoření vlastního procesoru direktiv vytvoříte třídu, která dědí buď z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Rozdíl mezi těmito dvěma je, že <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementuje rozhraní minimální potřebné parametry od uživatele a generovat kód, který vytvoří výstupní soubor šablony. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje vyžaduje/poskytuje vzoru návrhu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> zpracovává dva speciální parametry `requires` a `provides`.  Například může vlastního procesoru direktiv přijmout názvu souboru od uživatele, otevřete a čtení tohoto souboru a poté uložit text souboru v proměnné s názvem `fileText`. Podtřída <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> třída může trvat názvu souboru od uživatele jako hodnotu `requires` parametr a název proměnné, do kterého chcete uložit text jako hodnotu `provides` parametru. Tento procesor by otevřít a přečíst soubor a poté uložit text souboru v zadané proměnné.

Před voláním vlastního procesoru direktiv z textové šablony v sadě Visual Studio, je nutné ho zaregistrovat.

Další informace o tom, jak přidat klíč registru najdete v tématu [nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Vlastní direktivy

Vlastní direktivy vypadá takto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Pokud chcete získat přístup k externí data nebo prostředky z textové šablony, můžete použít vlastní procesor direktiv.

Různé textové šablony můžete sdílet funkci, která poskytuje jeden procesor direktiv, takže procesorů pro direktivy poskytují způsob, jak kód koeficient pro opakované použití. Předdefinované `include` direktiva je podobné, protože slouží k zohlednit si kód a sdílení mezi různé textové šablony. Rozdíl je, že všechny funkce, která `include` poskytuje – direktiva je pevná a nepřijímá žádné parametry. Pokud chcete povolit šablona pro předání parametrů a poskytují společné funkce, které textové šablony, musíte vytvořit vlastní procesor direktiv.

Může být několik příkladů vlastní procesory direktiv:

-   Procesor direktiv vrátit data z databáze, která přijímá jako parametry uživatelské jméno a heslo.

-   Procesoru direktiv pro otevírání a čtení souboru, který přijímá jako parametr názvu souboru.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Hlavní část vlastního procesoru direktiv

K vývoji procesor direktiv, musíte vytvořit třídu, která dědí buď z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Nejdůležitější `DirectiveProcessor` metody, které je nutné implementovat jsou následující.

-   `bool IsDirectiveSupported(string directiveName)` -Návratový `true` pokud procesor direktiv můžete řešit s názvem direktivy.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` – Modul šablony volá tuto metodu pro každý výskyt – direktiva v šabloně. Procesor měli uložit výsledky.

Po všech volání metoda ProcessDirective() modul šablon bude volat tyto metody:

-   `string[] GetReferencesForProcessingRun()` -Vrátí názvy sestavení, která se vyžaduje kód šablony.

-   `string[] GetImportsForProcessingRun()` -Vrátí obory názvů, které lze použít v kódu šablony.

-   `string GetClassCodeForProcessingRun()` -Návratový kód metody, vlastnosti a jiné deklarace, které kód šablony mohl používat. Nejjednodušší způsob, jak to provést je vytvořit řetězec obsahující C# nebo kódu jazyka Visual Basic. Aby procesor direktiv dokáže volaná ze šablony, která používá libovolný jazyk CLR, můžete vytvořit příkazy jako strom CodeDom a potom vrátí výsledek serializaci stromu v jazyce, který používá šablonu.

-   Další informace najdete v tématu [návod: vytvoření vlastního procesoru direktiv](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Viz také:

- [Nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md) vysvětluje postup při registraci vlastního procesoru direktiv.
- [Návod: Vytvoření vlastního procesoru direktiv](../modeling/walkthrough-creating-a-custom-directive-processor.md) popisuje postup vytvoření vlastního procesoru direktiv, jak zaregistrovat a testování procesoru direktiv a jak formátovat výstup souboru ve formátu HTML.