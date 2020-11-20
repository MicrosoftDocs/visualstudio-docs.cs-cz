---
title: Typové a netypové datové sady
description: Pochopte rozdíl mezi zadanými a netypovými datovými sadami. Kontrastní přístup k datům v zadaných a netypových datových sadách.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b2dc8d78f42d210741c904e3e475be33f2443e74
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998054"
---
# <a name="typed-vs-untyped-datasets"></a>Typové a netypové datové sady
Typová datová sada je datová sada, která je nejprve odvozena od základní <xref:System.Data.DataSet> třídy a poté používá informace z **Návrhář datových sad**, která je uložena v souboru. XSD pro vygenerování nové, silně typované datové třídy. Informace ze schématu (tabulky, sloupce a tak dále) jsou vygenerovány a zkompilovány do této nové datové třídy jako sada objektů a vlastností první třídy. Vzhledem k tomu, že zadaná datová sada dědí ze základní <xref:System.Data.DataSet> třídy, třída typu předpokládá všechny funkce <xref:System.Data.DataSet> třídy a lze ji použít s metodami, které jako parametr přebírají instanci <xref:System.Data.DataSet> třídy.

Netypové datové sady naopak nemá žádné odpovídající předdefinované schéma. Jako u typované datové sady obsahuje netypové datové sady tabulky, sloupce a tak dále, ale ty jsou zpřístupněny pouze jako kolekce. (Nicméně po ručním vytvoření tabulek a dalších datových prvků v netypové datové sadě můžete strukturu datové sady exportovat jako schéma pomocí metody datové sady <xref:System.Data.DataSet.WriteXmlSchema%2A> .)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Kontrast přístupu k datům v zadaných a netypových datových sadách
Třída pro typovou datovou sadu má objektový model, ve kterém vlastnosti přebírají skutečné názvy tabulek a sloupců. Například pokud pracujete s typovou datovou sadou, můžete odkazovat na sloupec pomocí kódu, jako je následující:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Na rozdíl od toho, pokud pracujete s netypovým datovou sadou, je ekvivalentní kód:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

Typ přístupu typu není snazší číst, ale také plně podporovaný technologií IntelliSense v **editoru kódu** sady Visual Studio. Kromě toho, že syntaxe pro typovou datovou sadu usnadňuje práci s, syntaxe pro typované datové sady poskytuje kontrolu typu v době kompilace, což významně snižuje riziko chyb při přiřazování hodnot členům datové sady. Pokud změníte název sloupce ve <xref:System.Data.DataSet> třídě a potom zkompilujete aplikaci, obdržíte chybu sestavení. Dvojitým kliknutím na chybu sestavení v **seznam úkolů** můžete přejít přímo na řádek nebo řádky kódu, které odkazují na starý název sloupce. Přístup k tabulkám a sloupcům ve typované datové sadě je v době běhu také mírně rychlejší, protože přístup je určen v době kompilace, nikoli prostřednictvím kolekcí za běhu.

I když typové datové sady mají mnoho výhod, netypové datové sady je užitečné v různých případech. Nejvýraznějším scénářem je, že pro datovou sadu není k dispozici žádné schéma. K tomu může dojít například v případě, že vaše aplikace pracuje s komponentou, která vrací datovou sadu, ale nevíte, co je jeho struktura. Podobně existují situace, kdy pracujete s daty, která nemají statickou, předvídatelná strukturu. V takovém případě je nepraktické použít typovou datovou sadu, protože by bylo nutné znovu vygenerovat typovou třídu DataSet s každou změnou v datové struktuře.

Obecně platí, že existuje mnoho času, kdy můžete datovou sadu vytvořit dynamicky, aniž by bylo nutné mít k dispozici schéma. V takovém případě je datová sada jednoduše vhodnou strukturou, ve které můžete uchovávat informace, pokud je možné data znázornit relačním způsobem. Současně můžete využít výhody funkcí datové sady, jako je možnost serializace informací, které mají být předávány jinému procesu, nebo pro zápis souboru XML.

## <a name="see-also"></a>Viz také

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)
