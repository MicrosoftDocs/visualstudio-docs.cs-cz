---
title: Vlastnosti drah
description: Přečtěte si, jak plavecké dráhy rozdělí diagram do vertikálních nebo horizontálních oblastí a jak můžete definovat další obrazce, které se mají zobrazit v rámci plaveckých drah.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fef3b2115be499197030a4ce7fd49b1dd849de12
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363065"
---
# <a name="properties-of-swimlanes"></a>Vlastnosti drah
Do diagramu můžete přidat plavecké dráhy. Plavecké dráhy rozdělí diagram na svislé nebo vodorovné oblasti. Můžete definovat další obrazce, které se mají zobrazit v rámci plaveckých drah. Další informace najdete v tématu [definování Domain-Specificho jazyka](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti použít, najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Plavecké dráhy mají vlastnosti, které jsou uvedeny v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně textu|Barva výplně těla plavecké dráhy.|White|
|Barva výplně záhlaví|Barva výplně záhlaví plavecké dráhy|DarkGray|
|Barva oddělovače|Barva oddělovací čáry|LightGray|
|Styl čáry oddělovače|Styl oddělovací čáry ( `Solid` , `Dash` ,, `Dot` `DashDot` , `DashDotDot` nebo `Custom` ).|`Dash`|
|Tloušťka oddělovače|Tloušťka oddělovací čáry v palcích|0,03125|
|Barva textu|Barva, která se používá pro text dekoratéry, která je spojená s touto plaveckou dráhou.|Black|
|Modifikátor přístupu|Úroveň přístupu třídy ( `public` nebo `internal` ).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy kódu, která je vygenerována z této plavecké dráhy.|\<none>|
|Generuje dvojitou odvozenou|Pokud `True` bude vygenerována jak základní třída, tak částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud se `True` vlastní konstruktor poskytne ve zdrojovém kódu. Další informace naleznete v tématu [přepsání a rozšíření vygenerovaných tříd](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědění třídy zdrojového kódu, který je generován z plavecké dráhy ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní plavecká dráha|Základní třída této plavecké dráhy.|(žádná)|
|Název|Název této plavecké dráhy.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k této plavecké dráze.|Aktuální obor názvů|
|Typ popisu|Jak je definován popis tlačítka ( `fixed` , `variable` , nebo `none` ). `fixed`Je-li použita hodnota vlastnosti, je `Fixed Tooltip Text` `variable` -li, pak je popis definovaný ve vlastním kódu.|\<none>|
|Poznámky|Neformální poznámky, které jsou spojeny s touto plaveckou dráhou.|\<none>|
|Zarovnání|Vodorovné nebo svislé zarovnání|Svisle|
|Počáteční výška|Počáteční výška této plavecké dráhy v palcích Platí pouze pro horizontální plavecké dráhy.|0|
|Počáteční Šířka|Počáteční šířka této plavecké dráhy v palcích Platí pouze pro vertikální plavecké dráhy.|0|
|Zpřístupňuje barvu textu|Pokud `True` uživatel může nastavit barvu plavecké dráhy ve vygenerovaném návrháři. Pokud to chcete nastavit, klikněte pravým tlačítkem myši na obrazec plavecká dráha a klikněte na **Přidat vystavené**.|Ne|
|Popis|Slouží k dokumentování vygenerovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerovaném návrháři, aby odkazoval na tuto třídu plavecké dráhy.|\<none>|
|Pevný text popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo Help|Klíčové slovo, které se používá k indexování Nápověda F1 pro tuto plaveckou dráhu.|\<none>|

## <a name="see-also"></a>Viz také:

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))