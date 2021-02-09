---
title: Vlastnosti dekorátorů
description: Přečtěte si, že dekoratéry jsou ikony, text nebo rozbalit nebo sbalit šipky, které se mohou objevit na tvarech nebo spojnicích v diagramu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e29dcda43fdbb7b60567ff0aa0627b41ca3ca299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873785"
---
# <a name="properties-of-decorators"></a>Vlastnosti dekorátorů
Dekoratéry jsou ikony, text nebo rozbalit/sbalit šipky, které se mohou objevit na tvarech nebo spojnicích v diagramu. V následujících tabulkách jsou uvedeny vlastnosti pro tři druhy dekoratér. Některé vlastnosti se zobrazí pouze u obrazce dekoratéry nebo pouze na dekoratéry konektoru.

 Další informace najdete v tématu [definování Domain-Specificho jazyka](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti použít, najdete v tématu [přizpůsobení a rozšíření Domain-Specificho jazyka](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozbalit/sbalit dekoratér

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DisplayName|Název dekoratér, který se zobrazí ve vygenerovaném návrháři.|Rozbalit sbalení dekoratér|
|Název|Název dekoratér.|ExpandCollapseDecorator|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto dekoratér.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|Pozice|Výchozí pozice dekoratéru|SourceTop|

## <a name="icon-decorator"></a>Dekoratér ikony

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DefaultIcon|Cesta k souboru ikony nebo obrázku, který se má zobrazit|\<none>|
|DisplayName|Název dekoratér, který se má zobrazit ve vygenerovaném návrháři.|Dekoratér ikony|
|Název|Název dekoratér.|IconDecorator|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekoratér.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|Pozice|Výchozí pozice dekoratéru|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DefaultText|Výchozí text, který se má zobrazit|Popisek|
|DisplayName|Název dekoratér, který se má zobrazit ve vygenerovaném návrháři.|Popisek|
|FontSize|Velikost písma textu zobrazeného v dekoratéru|8|
|FontStyle|Styl písma textu, který se zobrazí v dekoratér.|Pravidelný|
|Název|Název dekoratér.|Popisek|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekoratér.|\<none>|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0|
|Pozice|Výchozí pozice dekoratéru|TargetBottom|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](/previous-versions/bb126564(v=vs.100))