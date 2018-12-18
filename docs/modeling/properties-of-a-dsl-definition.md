---
title: Vlastnosti definice DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1fd001f5371e346a07f82c9c48a3acb699cefd52
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966762"
---
# <a name="properties-of-a-dsl-definition"></a>Vlastnosti definice DSL
Definovat vlastnosti DslDefinition *jazyka specifického pro doménu* definice vlastnosti, jako je například verze číslování. Vlastnosti DslDefinition se zobrazí v **vlastnosti** okně po kliknutí na otevřené oblasti diagramu v *návrháře jazyka specifického pro doménu*.

 Další informace najdete v tématu [jak se definuje jazyk specifický pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak pomocí těchto vlastností najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition má vlastnosti v následující tabulce:

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Určuje, jestli je modifikátor přístupu pro doménovou třídu veřejný nebo interní.|public|
|Vlastní atributy|Uživatelem definované atributy pro doménovou třídu.<br /><br /> **Poznámka:** přidat atribut, pomocí tlačítka Procházet.|\<žádné >|
|Název společnosti|Název aktuální název společnosti v systémovém registru.|Aktuální název společnosti|
|Název|Název třídy této domény.|Aktuální název|
|Obor názvů|Názvový prostor připojený k této doménové třídě.|Aktuální obor názvů|
|Identifikátor Guid balíčku|Identifikátor guid balíčku sady Visual Studio vygenerovaný pro tento DSL.|\<žádné >|
|Balíček Namespace|Obor názvů pro balíček sady Visual Studio vygenerovaný pro tento DSL.|\<žádné >|
|Název produktu|Název produktu, který se zaregistruje pro balíček sady Visual Studio vygenerovaný pro tento DSL.|\<žádné >|
|Poznámky|Poznámky přidružené k této doménové třídě.|\<žádné >|
|Popis|Popis pro tuto doménovou třídu.|\<žádné >|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři u této doménové třídě.|\<žádné >|
|Klíčové slovo nápovědy|Klíčové slovo nápovědy přidružené k této doménové třídě.|\<žádné >|
|Sestavení|Číslo přírůstkové sestavení této definice jazyka specifického pro doménu.|0|
|Hlavní verze|Číslo hlavní přírůstkového sestavení této definice jazyka specifického pro doménu.|1|
|Podverze|Přírůstkové sestavení vedlejší číslo pro tato definice jazyka specifického pro doménu.|0|
|Revize|Přírůstkové revize číslo pro tuto definici jazyka specifického pro doménu sestavení.|0|

## <a name="see-also"></a>Viz také

- [Glosář nástrojů jazyka specifického pro doménu](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)