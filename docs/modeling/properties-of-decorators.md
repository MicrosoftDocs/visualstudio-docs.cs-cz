---
title: Vlastnosti dekorátorů
description: Zjistěte, že dekorátory jsou ikony, text nebo rozbalení/sbalení chevrons, které se dají zobrazit na tvarech nebo konektorech v diagramu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2f3436bb800142e7c85594f4b05cef6fb45c4489
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390799"
---
# <a name="properties-of-decorators"></a>Vlastnosti dekorátorů
Dekorátory jsou ikony, text nebo rozbalení/sbalení chevrons, které se dají zobrazit u obrazců nebo konektorů v diagramu. Následující tabulky zobrazují vlastnosti pro tři druhy dekoratéra. Některé vlastnosti se zobrazují pouze u dekorátorů obrazce nebo pouze u dekorátorů konektorů.

 Další informace najdete v [tématu Definování jazyka Domain-Specific .](../modeling/how-to-define-a-domain-specific-language.md) Další informace o použití těchto vlastností naleznete v tématu [Customizing and Extending a Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozbalení/sbalení dekorátoru

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DisplayName|Název dekoratéru, který se zobrazí ve vygenerované návrháři.|Rozbalení dekorátoru sbalení|
|Name|Název dekorátoru.|ExpandCollapseDecorator|
|Poznámky|Neformální poznámky, které jsou přidruženy k tomuto dekorátoru.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|Verticaloffset|Svislý posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|PosunFromLine|Posun dekorátoru od čáry vzhledem k jeho výchozí pozici v palcích. (Jenom u konektorů.)|0|
|PosunFromShape|Posun dekorátoru od obrazce vzhledem k jeho výchozí pozici v palcích. (Jenom u konektorů.)|0|
|Pozice|Výchozí pozice dekorátoru.|SourceTop|

## <a name="icon-decorator"></a>Dekorátor ikon

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DefaultIcon (Výchozí Icon)|Cesta k ikoně nebo souboru obrázku, který se má zobrazit.|\<none>|
|DisplayName|Název dekorátoru, který se má zobrazit ve vygenerované návrháři.|Dekorátor ikon|
|Name|Název dekorátoru.|IkonaDecorator|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekorátoru.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|Verticaloffset|Svislý posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|PosunFromLine|Posun dekorátoru od čáry vzhledem k jeho výchozí pozici v palcích. (Jenom u konektorů.)|0|
|PosunFromShape|Posun dekorátoru od obrazce vzhledem k jeho výchozí pozici v palcích. (Jenom u konektorů.)|0|
|Pozice|Výchozí pozice dekorátoru.|SourceTop|

## <a name="textdecorator"></a>TextDecorator (Textový decorator)

|Vlastnost|Popis|Výchozí|
|-|-|-|
|Výchozítext|Výchozí text, který se má zobrazit.|Popisek|
|DisplayName|Název dekorátoru, který se má zobrazit ve vygenerované návrháři.|Popisek|
|Fontsize|Velikost písma pro text, který je zobrazen v dekorátoru.|8|
|Fontstyle|Styl písma pro text, který je zobrazen v dekorátoru.|Pravidelný|
|Name|Název dekorátoru.|Popisek|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekorátoru.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|Verticaloffset|Svislý posun vzhledem k výchozí pozici dekorátoru v palcích. (Pouze u obrazců.)|0|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|Pozice|Výchozí pozice dekoratéru|TargetBottom|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))