---
title: Vlastnosti drah
description: Zjistěte, jak plavecký dráhy rozdělují diagram do svislých nebo vodorovných oblastí a jak můžete definovat další obrazce, které se mají zobrazit uvnitř drah.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c171bda2670b698297dd876a8a4403a91cd4af7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386485"
---
# <a name="properties-of-swimlanes"></a>Vlastnosti drah
Do diagramu můžete přidat dráhy. Dráhy rozdělují diagram do svislých nebo vodorovných oblastí. Můžete definovat další obrazce, které se budou zobrazovat uvnitř drah. Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Dráhy mají vlastnosti uvedené v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně těla|Barva výplně těla dráhy|White|
|Barva výplně záhlaví|Barva výplně pro záhlaví dráhy|DarkGray|
|Barva oddělovače|Barva čáry oddělovače|LightGray|
|Styl čáry oddělovače|Styl čáry oddělovače ( `Solid` , , , , , nebo `Dash` `Dot` `DashDot` `DashDotDot` `Custom` ).|`Dash`|
|Tloušťka oddělovače|Tloušťka čáry oddělovače v palcích|0.03125|
|Barva textu|Barva, která se používá pro dekorátory textu, které jsou přidruženy k této dráhy.|Black|
|Modifikátor přístupu|Úroveň přístupu třídy ( `public` nebo `internal` ).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy kódu, která je generována z této dráhy.|\<none>|
|Vygeneruje dvojitě odvozený|Pokud `True` , bude vygenerována základní i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Má vlastní konstruktor|Pokud , bude ve zdrojovém `True` kódu k dispozici vlastní konstruktor. Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z dráhy ( `none` , `abstract` nebo `sealed` ).|žádné|
|Základní plavecký drah|Základní třída této dráhy|(žádná)|
|Name|Název této dráhy|Aktuální název|
|Obor názvů|Obor názvů přidružený k této dráhě.|Aktuální obor názvů|
|Typ popisu|Jak je popis definovaný ( `fixed` `variable` , nebo `none` ). Pokud se použije hodnota vlastnosti , pak se popis definuje ve vlastním `fixed` `Fixed Tooltip Text` `variable` kódu.|\<none>|
|Poznámky|Neformální poznámky, které jsou přidruženy k této dráhě.|\<none>|
|Zarovnání|Vodorovné nebo svislé zarovnání.|Svisle|
|Počáteční výška|Počáteční výška této dráhy v palcích Vztahuje se pouze na vodorovné dráhy.|0|
|Počáteční šířka|Počáteční šířka této dráhy (v palcích). Platí jenom pro svislé dráhy.|0|
|Zpřístupňuje barvu textu|Pokud `True` , uživatel může nastavit barvu dráhy ve vygenerované návrháři. Tuto možnost nastavíte tak, že kliknete pravým tlačítkem na tvar dráhy a kliknete na **Přidat vystavený.**|Ne|
|Description|Slouží k zdokumentování generovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro odkazování na tuto třídu drah.|\<none>|
|Oprava textu popisu|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo nápovědy|Klíčové slovo , které se používá k indexování nápovědy F1 pro tuto dráhu.|\<none>|

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))