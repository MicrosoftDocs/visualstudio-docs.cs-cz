---
title: Vytváření vlastních procesorů pro direktivy textových šablon T4
description: Přečtěte si o procesu transformace textových šablon a o tom, jak vytvořit vlastní procesor direktiv textových šablon T4.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389498"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Vytváření vlastních procesorů pro direktivy textových šablon T4

Proces *transformace textové šablony přebírá* jako *vstup* textový soubor šablony a jako výstup vytvoří textový soubor. Modul *transformace textových šablon* řídí proces a modul komunikuje s hostitelem transformace  textových šablon a jedním nebo více procesory direktiv textových šablon k dokončení procesu. Další informace najdete v tématu [Proces transformace textových šablon.](../modeling/the-text-template-transformation-process.md)

Pokud chcete vytvořit vlastní procesor direktiv, vytvoříte třídu, která dědí z nebo <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Rozdíl mezi těmito dvěma rozhraními spočívá v implementaci minimálního rozhraní, které je nezbytné k získání parametrů od uživatele a k vygenerování kódu, který vytváří <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> výstupní soubor šablony. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje vzor návrhu requires/provides. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> zpracovává dva speciální parametry, `requires` a `provides` .  Například procesor vlastních direktiv může přijmout název souboru od uživatele, otevřít a přečíst soubor a pak uložit text souboru do proměnné s názvem `fileText` . Podtřída třídy může převzít název souboru od uživatele jako hodnotu parametru a název proměnné, do které se má text uložit jako hodnota <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> `requires` `provides` parametru. Tento procesor by otevřel a načetl soubor a pak text souboru ukládal do zadané proměnné.

Před voláním vlastního procesoru direktiv z textové šablony v Visual Studio, musíte ho zaregistrovat.

Další informace o tom, jak přidat klíč registru, najdete v tématu [Nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Vlastní direktivy

Vlastní direktiva vypadá takhle:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Pokud chcete získat přístup k externím datům nebo prostředkům z textové šablony, můžete použít vlastní procesor direktiv.

Různé textové šablony mohou sdílet funkce, které poskytuje procesor s jednou direktivou, takže procesory direktiv poskytují způsob, jak kód použít k opakovanému použití. Integrovaná direktiva je podobná, protože ji můžete použít k ověření kódu a jeho sdílení `include` mezi různými textovou šablonou. Rozdíl je v tom, že všechny funkce, které direktiva poskytuje, jsou pevné a `include` nepřijímá parametry. Pokud chcete textové šabloně poskytnout běžné funkce a umožnit šabloně předat parametry, musíte vytvořit vlastní procesor direktiv.

Mezi příklady vlastních procesorů direktiv patří:

- Procesor direktiv pro vrácení dat z databáze, která jako parametry přijímá uživatelské jméno a heslo.

- Procesor direktiv pro otevření a čtení souboru, který přijímá název souboru jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Hlavní části vlastního procesoru direktiv

Chcete-li vyvinout procesor direktiv, je nutné vytvořit třídu, která dědí z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> nebo <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Nejdůležitější `DirectiveProcessor` metody, které je nutné implementovat, jsou následující.

- `bool IsDirectiveSupported(string directiveName)` – Vrátí `true` hodnotu , pokud procesor direktiv dokáže pojmenovanou direktivu použít.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` – Modul šablon volá tuto metodu pro každý výskyt direktivy v šabloně. Váš procesor by měl výsledky uložit.

Po všech voláních metody ProcessDirective() bude modul šablon volat tyto metody:

- `string[] GetReferencesForProcessingRun()` – Vrátí názvy sestavení, která vyžaduje kód šablony.

- `string[] GetImportsForProcessingRun()` – Vrátí obory názvů, které lze použít v kódu šablony.

- `string GetClassCodeForProcessingRun()` – Vrátí kód metod, vlastností a dalších deklarací, které může kód šablony použít. Nejjednodušším způsobem, jak to provést, je sestavit řetězec obsahující kód jazyka C# nebo Visual Basic kódu. Chcete-li zajistit, aby byl procesor direktiv schopný být volán ze šablony, která používá libovolný jazyk CLR, můžete příkazy sestavit jako strom CodeDom a poté vrátit výsledek serializace stromu v jazyce používaném šablonou.

- Další informace najdete v [návodu: Vytvoření vlastního procesoru direktiv](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Viz také

- [Článek Nasazení vlastního procesoru direktiv](../modeling/deploying-a-custom-directive-processor.md) vysvětluje, jak zaregistrovat vlastní procesor direktiv.
- [Návod: Vytvoření vlastního](../modeling/walkthrough-creating-a-custom-directive-processor.md) procesoru direktiv popisuje, jak vytvořit vlastní procesor direktiv, jak zaregistrovat a otestovat procesor direktiv a jak formátovat výstupní soubor jako HTML.
