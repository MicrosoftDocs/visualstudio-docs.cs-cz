---
title: Vytváření vlastních procesorů pro direktivy textových šablon T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 836e2c24d9f236c7b87dfff60b934221b7645f1b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654072"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Vytváření vlastních procesorů pro direktivy textových šablon T4

*Proces transformace textové šablony* převede soubor *textové šablony* jako vstup a vytvoří textový soubor jako výstup. *Modul transformace textových šablon* řídí proces a modul komunikuje s hostitelem transformace textové šablony a jedním nebo více *procesory direktiv* textových šablon pro dokončení procesu. Další informace naleznete v tématu [proces transformace textové šablony](../modeling/the-text-template-transformation-process.md).

Chcete-li vytvořit vlastní procesor direktiv, vytvoříte třídu, která dědí z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Rozdíl mezi těmito dvěma je, že <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementuje minimální rozhraní, které je nezbytné pro získání parametrů od uživatele a pro vygenerování kódu, který vytváří výstupní soubor šablony. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje vzor návrhu vyžaduje/poskytuje. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> zpracovává dva speciální parametry `requires` a `provides`.  Vlastní procesor direktiv může například přijmout název souboru od uživatele, otevřít soubor a načíst ho a pak text souboru Uložit do proměnné s názvem `fileText`. Podtřída <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> třídy může mít název souboru od uživatele jako hodnota parametru `requires` a název proměnné, do které se má text uložit, jako hodnota parametru `provides`. Tento procesor by otevřel a četl soubor a pak v zadané proměnné uložil text souboru.

Před voláním vlastního procesoru direktiv z textové šablony v aplikaci Visual Studio je nutné jej zaregistrovat.

Další informace o tom, jak přidat klíč registru, najdete v tématu [nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Vlastní direktivy

Vlastní direktiva vypadá takto:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Pokud chcete získat přístup k externím datům nebo prostředkům z textové šablony, můžete použít vlastní procesor direktiv.

Různé textové šablony mohou sdílet funkce, které poskytuje jeden procesor direktiv, takže procesory direktiv poskytují způsob, jak použít kód pro opakované použití. Integrovaná direktiva `include` je podobná, protože ji můžete použít k vyzkoušení kódu a jejich sdílení mezi různými textovými šablonami. Rozdílem je, že všechny funkce, které direktiva `include` poskytuje, jsou pevně dané a nepřijímají parametry. Chcete-li pro textovou šablonu poskytnout společné funkce a umožnit šabloně předat parametry, je nutné vytvořit vlastní procesor direktiv.

Některé příklady vlastních procesorů direktiv mohou být:

- Procesor direktiv pro vrácení dat z databáze, která přijímá uživatelské jméno a heslo jako parametry.

- Procesor direktiv pro otevření a čtení souboru, který přijímá název souboru jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Hlavní části vlastního procesoru direktiv

Chcete-li vyvinout procesor direktiv, je nutné vytvořit třídu, která dědí z buď <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>, nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Nejdůležitější `DirectiveProcessor` metody, které je nutné implementovat, jsou následující.

- `bool IsDirectiveSupported(string directiveName)` – vrátí `true`, pokud se váš procesor direktiv může zabývat s pojmenovanou direktivou.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` – modul šablon volá tuto metodu pro každý výskyt direktivy v šabloně. Váš procesor by měl výsledky uložit.

Po všech voláních ProcessDirective () modul šablonování vyvolá tyto metody:

- `string[] GetReferencesForProcessingRun()` – vrátí názvy sestavení, které kód šablony vyžaduje.

- `string[] GetImportsForProcessingRun()` – vrátí obory názvů, které lze použít v kódu šablony.

- `string GetClassCodeForProcessingRun()` – vrátí kód metod, vlastností a dalších deklarací, které může kód šablony použít. Nejjednodušší způsob, jak to provést, je sestavení řetězce obsahujícího kód C# nebo Visual Basic. Aby byl procesor direktiv schopný volat ze šablony, která používá jakýkoliv jazyk CLR, můžete vytvořit příkazy jako strom CodeDom a pak vrátit výsledek serializace stromu v jazyce používaném šablonou.

- Další informace najdete v tématu [Návod: Vytvoření vlastního procesoru direktiv](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Viz také:

- [Nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md) vysvětluje, jak zaregistrovat vlastní procesor direktiv.
- [Návod: Vytvoření vlastního procesoru direktiv](../modeling/walkthrough-creating-a-custom-directive-processor.md) popisuje, jak vytvořit vlastní procesor direktiv, jak registrovat a testovat procesor direktiv a jak zformátovat výstupní soubor jako HTML.