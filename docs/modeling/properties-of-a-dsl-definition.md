---
title: Vlastnosti definice DSL
description: Zjistěte, že vlastnosti DslDefinition definují vlastnosti definice jazyka specifické pro doménu, jako je číslování verzí.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6212dfcb9e93110a97e7143e5b1c946efebee89f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390838"
---
# <a name="properties-of-a-dsl-definition"></a>Vlastnosti definice DSL
Vlastnosti DslDefinition definují *vlastnosti definice jazyka specifické* pro doménu, jako je číslování verzí. Vlastnosti DslDefinition se zobrazí v **okně Vlastnosti** po kliknutí na otevřenou oblast diagramu v *Návrháři jazyka specifickém pro doménu*.

 Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition má vlastnosti v následující tabulce:

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Určuje, jestli je modifikátor přístupu pro třídu domény veřejný nebo interní.|public|
|Vlastní atributy|Vlastní definované atributy pro třídu domény.<br /><br /> **Poznámka:** Pomocí tlačítka Procházet přidejte atribut.|\<none>|
|Název společnosti|Název aktuálního názvu společnosti v systémovém registru.|Aktuální název společnosti|
|Name|Název této třídy domény.|Aktuální název|
|Obor názvů|Obor názvů přidružený k této třídě domény.|Aktuální obor názvů|
|Guid balíčku|Identifikátor GUID pro Visual Studio vygenerovaný pro tento DSL.|\<none>|
|Package – obor názvů|Obor názvů pro Visual Studio pro tento DSL.|\<none>|
|Název produktu|Název produktu, který bude zaregistrován pro balíček Visual Studio pro tento DSL.|\<none>|
|Poznámky|Poznámky přidružené k této třídě domény.|\<none>|
|Description|Popis pro tuto třídu domény|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro tuto třídu domény.|\<none>|
|Klíčové slovo nápovědy|Klíčové slovo nápovědy přidružené k této třídě domény.|\<none>|
|Sestavení|Číslo přírůstkového sestavení pro tuto definici jazyka specifické pro doménu.|0|
|Hlavní verze|Číslo přírůstkového velkého sestavení pro tuto definici jazyka specifické pro doménu.|1|
|Podverze|Přírůstkové dílčí číslo sestavení pro tuto definici jazyka specifické pro doménu.|0|
|Revize|Číslo sestavení přírůstkové revize pro tuto definici jazyka specifickou pro doménu.|0|

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))