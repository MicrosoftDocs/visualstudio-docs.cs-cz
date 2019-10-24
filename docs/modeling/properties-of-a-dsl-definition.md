---
title: Vlastnosti definice DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ae26dc54c8f57348ed00196d86629e3515a1835
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748341"
---
# <a name="properties-of-a-dsl-definition"></a>Vlastnosti definice DSL
Vlastnosti DslDefinition definují vlastnosti definice *jazyka specifického pro doménu* , jako je například číslování verzí. Vlastnosti DslDefinition se zobrazí v okně **vlastnosti** , když kliknete na otevřenou oblast diagramu v *Návrháři jazyka specifického pro doménu*.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition má vlastnosti v následující tabulce:

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Modifikátor přístupu|Určuje, jestli je modifikátor přístupu pro doménovou třídu veřejný nebo interní.|public|
|Vlastní atributy|Vlastní definované atributy pro doménovou třídu.<br /><br /> **Poznámka:** K přidání atributu použijte tlačítko Procházet.|\<none >|
|Název společnosti|Název aktuálního názvu společnosti v registru systému.|Název aktuální společnosti|
|Name|Název této doménové třídy|Aktuální název|
|Obor názvů|Obor názvů přidružený k této doménové třídě|Aktuální obor názvů|
|Identifikátor GUID balíčku|Identifikátor GUID balíčku sady Visual Studio vygenerovaného pro tento DSL|\<none >|
|Obor názvů balíčku|Obor názvů pro balíček sady Visual Studio vygenerovaný pro tento DSL|\<none >|
|Název produktu|Název produktu, který se zaregistruje pro balíček sady Visual Studio vygenerovaný pro tento DSL|\<none >|
|Poznámky|Poznámky přidružené k této doménové třídě|\<none >|
|Popis|Popis této doménové třídy|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři pro tuto doménovou třídu.|\<none >|
|Klíčové slovo Help|Klíčové slovo Help přidružené k této doménové třídě|\<none >|
|Sestavení|Číslo přírůstkového sestavení pro tuto definici jazyka specifického pro doménu.|0,8|
|Hlavní verze|Přírůstkové hlavní číslo buildu pro tuto definici jazyka specifického pro doménu.|první|
|Dílčí verze|Přírůstkové číslo sestavení pro tuto definici jazyka specifického pro doménu.|0,8|
|Revize|Číslo buildu přírůstkové revize pro tuto definici jazyka specifického pro doménu.|0,8|

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)