---
title: Vlastnosti obrazců portů
description: Přečtěte si o tvarech portů a o tom, jak můžete pomocí tvarů portů reprezentovat třídy domén ve vygenerované návrháři.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.port
helpviewer_keywords:
- Domain-Specific Language, port shape
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b5994d2629a49757980695ca99a6d12ae21160a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386524"
---
# <a name="properties-of-port-shapes"></a>Vlastnosti obrazců portů
Tvary portů můžete použít k reprezentaci tříd domény ve vygenerované návrháři.

 Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Tvary portů mají vlastnosti uvedené v následující tabulce.

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Barva výplně|Barva výplně tohoto tvaru|White|
|Režim přechodu výplně|Režim přechodu výplně tohoto tvaru.|Vodorovně|
|Geometrie|Geometrie tohoto tvaru (obdélník, zaoblený obdélník, tři tečky nebo kruh).|Obdélník|
|Má výchozí body připojení|Pokud použije tvar horní, dolní, levý a pravý spojovací `True` bod ve vygenerované návrháři.|Ne|
|Barva obrysu|Barva obrysu tohoto tvaru.|Black|
|Styl pomlčky obrysu|Styl pomlčky obrysu tohoto tvaru (Solid, Dash, Dot, DashDot, DashDotDot nebo Custom).|Plná|
|Tloušťka obrysu|Tloušťka obrysu tohoto tvaru|0.03125|
|Barva textu|Barva, která se používá pro dekorátory textu, které jsou přidruženy k tomuto tvaru.|Black|
|Modifikátor přístupu|Úroveň přístupu třídy ( `public` nebo `internal` ).|Veřejná|
|Vlastní atributy|Slouží k přidání atributů do třídy zdrojového kódu, která je generována z tohoto tvaru.|\<none>|
|Vygeneruje dvojitě odvozený|Pokud `True` , bude vygenerována základní i částečná třída (pro podporu přizpůsobení prostřednictvím přepsání). Další informace najdete v tématu [Přepsání a rozšíření generovaných tříd.](../modeling/overriding-and-extending-the-generated-classes.md)|Ne|
|Má vlastní konstruktor|Pokud , bude ve zdrojovém `True` kódu k dispozici vlastní konstruktor. Další informace najdete v tématu [Přepsání a rozšíření vygenerované třídy](../modeling/overriding-and-extending-the-generated-classes.md).|Ne|
|Modifikátor dědičnosti|Popisuje druh dědičnosti třídy zdrojového kódu, která je generována z portu ( `none` `abstract` nebo `sealed` ).|žádné|
|Základní port|Základní třída tohoto tvaru.|(žádná)|
|Name|Název tohoto tvaru.|Aktuální název|
|Obor názvů|Obor názvů, který je přidružen k tomuto tvaru.|Aktuální obor názvů|
|Typ popisku|Jak je popis definován (pevný, proměnný nebo žádný). Pokud je tato hodnota opravená, použije se hodnota vlastnosti jako popisek. Pokud je proměnná proměnná, popis je definovaný ve `Fixed Tooltip Text` vlastním kódu.|žádné|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto tvaru.|\<none>|
|Počáteční výška|Počáteční výška tohoto tvaru v palcích|1|
|Počáteční šířka|Počáteční šířka tohoto tvaru v palcích|1.5|
|Vystavená barva výplně jako vlastnost<br /><br /> Vystavený přechodový režim výplně<br /><br /> Vystavená barva obrysu jako vlastnost<br /><br /> Vystavená vlastnost pomlčky obrysu jako<br /><br /> Vystavená tloušťka obrysu jako vlastnost<br /><br /> Zpřístupňuje barvu textu|V `True` případě může uživatel nastavit uvedenou vlastnost obrazce. Tuto možnost nastavíte tak, že kliknete pravým tlačítkem na definici obrazce a kliknete na **Add Exposed (Přidat vystavený).**|Ne|
|Description|Slouží k zdokumentování generovaného návrháře.|\<none>|
|Zobrazovaný název|Název, který se zobrazí ve vygenerované návrháři pro tento tvar.|\<none>|
|Oprava textu popisku|Text, který se používá pro pevný popis.|\<none>|
|Klíčové slovo nápovědy|Klíčové slovo , které se používá k indexování nápovědy F1 pro tento tvar.|\<none>|

## <a name="see-also"></a>Viz také

- [Nástroje DSL glosář](/previous-versions/bb126564(v=vs.100))