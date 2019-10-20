---
title: Vlastnosti dekorátorů
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, decorators
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e34268b1c360c686a61da631100cb671acd59d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658246"
---
# <a name="properties-of-decorators"></a>Vlastnosti dekorátorů
Dekoratéry jsou ikony, text nebo rozbalit/sbalit šipky, které se mohou objevit na tvarech nebo spojnicích v diagramu. V následujících tabulkách jsou uvedeny vlastnosti pro tři druhy dekoratér. Některé vlastnosti se zobrazí pouze u obrazce dekoratéry nebo pouze na dekoratéry konektoru.

 Další informace najdete v tématu [Definování jazyka specifického pro doménu](../modeling/how-to-define-a-domain-specific-language.md). Další informace o tom, jak tyto vlastnosti používat, najdete v tématu [přizpůsobení a rozšíření jazyka specifického pro doménu](../modeling/customizing-and-extending-a-domain-specific-language.md).

## <a name="expandcollapse-decorator"></a>Rozbalit/sbalit dekoratér

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DisplayName|Název dekoratér, který se zobrazí ve vygenerovaném návrháři.|Rozbalit sbalení dekoratér|
|Name|Název dekoratér.|ExpandCollapseDecorator|
|Poznámky|Neformální poznámky, které jsou spojeny s tímto dekoratér.|\<none >|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|Pozice|Výchozí pozice dekoratéru|SourceTop|

## <a name="icon-decorator"></a>Dekoratér ikony

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DefaultIcon|Cesta k souboru ikony nebo obrázku, který se má zobrazit|\<none >|
|DisplayName|Název dekoratér, který se má zobrazit ve vygenerovaném návrháři.|Dekoratér ikony|
|Name|Název dekoratér.|IconDecorator|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekoratér.|\<none >|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|Pozice|Výchozí pozice dekoratéru|SourceTop|

## <a name="textdecorator"></a>TextDecorator

|Vlastnost|Popis|Výchozí|
|-|-|-|
|DefaultText|Výchozí text, který se má zobrazit|Popisek|
|DisplayName|Název dekoratér, který se má zobrazit ve vygenerovaném návrháři.|Popisek|
|FontSize|Velikost písma textu zobrazeného v dekoratéru|8|
|FontStyle|Styl písma textu, který se zobrazí v dekoratér.|Platné|
|Name|Název dekoratér.|Popisek|
|Poznámky|Neformální poznámky, které jsou přidruženy k dekoratér.|\<none >|
|HorizontalOffset|Vodorovný posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|VerticalOffset|Svislý posun vzhledem k výchozí pozici dekoratéru v palcích. (Pouze v obrazcích.)|0,8|
|OffsetFromLine|Posun dekoratéru od řádku vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|OffsetFromShape|Posun dekoratér od tvaru vzhledem k jeho výchozí pozici v palcích (Pouze v konektorech.)|0,8|
|Pozice|Výchozí pozice dekoratéru|TargetBottom|

## <a name="see-also"></a>Viz také

- [Glosář Nástroje DSL](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)