---
title: Vlastnosti drah
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5180581b0a0934c049d9c4ea199fa3396a1d1237
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658124"
---
# <a name="properties-of-swimlanes"></a>Vlastnosti drah
Do diagramu můžete přidat plavecké dráhy. Plavecké dráhy rozdělí diagram na svislé nebo vodorovné oblasti. Můžete definovat další obrazce, které se mají zobrazit v rámci plaveckých drah. Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Plavecké dráhy mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně textu|Barva výplně těla plavecké dráhy.|White|
|Barva výplně záhlaví|Barva výplně záhlaví plavecké dráhy|DarkGray|
|Barva oddělovače|Barva oddělovací čáry|LightGray|
|Styl čáry oddělovače|Styl oddělovací čáry (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot` nebo `Custom`).|`Dash`|
|Tloušťka oddělovače|Tloušťka oddělovací čáry v palcích|0,03125|
|Barva textu|Barva, která se používá pro text dekoratéry, která je spojená s touto plaveckou dráhou.|zůstane|
|Modifikátor přístupu|Úroveň přístupu třídy (`public` nebo `internal`).|Public|
|Vlastní atributy|Slouží k přidání atributů do třídy kódu, která je vygenerována z této plavecké dráhy.|\<none >|
|Generuje dvojitou odvozenou|Pokud `True`, bude vygenerována jak základní třída, tak i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Má vlastní konstruktor|Pokud `True`, bude ve zdrojovém kódu k dispozici vlastní konstruktor. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z plavecké dráhy (`none`, `abstract` nebo `sealed`).|žádná|
|Základní plavecká dráha|Základní třída této plavecké dráhy.|nTato|
|Name|Název této plavecké dráhy.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k této plavecké dráze.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka (`fixed`, `variable` nebo `none`). Je-li `fixed`, je použita hodnota vlastnosti `Fixed Tooltip Text`; Pokud `variable`, je popis tlačítka definován ve vlastním kódu.|\<none >|
|Poznámky|Neformální poznámky, které jsou spojeny s touto plaveckou dráhou.|\<none >|
|Zarovnání|Vodorovné nebo svislé zarovnání|Svislé|
|Počáteční výška|Počáteční výška této plavecké dráhy v palcích Platí pouze pro horizontální plavecké dráhy.|0,8|
|Počáteční Šířka|Počáteční šířka této plavecké dráhy v palcích Platí pouze pro vertikální plavecké dráhy.|0,8|
|Zpřístupňuje barvu textu|Pokud `True`, může uživatel nastavit barvu plavecké dráhy ve vygenerovaném návrháři. Pokud to chcete nastavit, klikněte pravým tlačítkem myši na obrazec plavecká dráha a klikněte na **Přidat vystavené**.|False|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none >|
|Zobrazované jméno|Název, který se zobrazí ve vygenerovaném návrháři, aby odkazoval na tuto třídu plavecké dráhy.|\<none >|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none >|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tuto plaveckou dráhu.|\<none >|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)