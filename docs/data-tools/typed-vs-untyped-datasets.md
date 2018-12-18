---
title: Typové a netypové datové sady
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d817938a7611d7390e400cfbf69c6836b9256f3b
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117222"
---
# <a name="typed-vs-untyped-datasets"></a>Typové a netypové datové sady
Typové datové sady je datovou sadu, která je první odvozený od základní <xref:System.Data.DataSet> třídy a pak používá informace z **návrháře Dataset**, která je uložena v souboru XSD vygenerovat nový, dataset – třída silného typu. Informace ze schématu (tabulek, sloupců atd.) je generována a zkompilovat do tato nová třída datovou sadu jako sada první třídy objektů a vlastností. Protože typové datové sady dědí od základní <xref:System.Data.DataSet> třída, typovaná třída předpokládá všechny funkce <xref:System.Data.DataSet> třídy a lze použít s metod, které berou instanci <xref:System.Data.DataSet> třída jako parametr.

 Netypové datové sady, na rozdíl od nemá žádné odpovídající integrované schéma. Jako typové datové sady, netypové datové sady obsahuje tabulky, sloupce a tak dále – ale těch, které jsou zveřejněné pouze jako kolekce. (Však po vytvoření ručně tabulky a další prvky dat v datové sadě služby bez typu, můžete exportovat datovou sadu struktura jako schéma pomocí datovou sadu <xref:System.Data.DataSet.WriteXmlSchema%2A> metoda.)

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Přístup k datům kontrast v typu a netypové datové sady
 Třída pro typové datové sady obsahuje model objektu, ve kterém jeho vlastnosti trvat na skutečné názvy tabulek a sloupců. Například pokud pracujete s typové datové sady, můžete odkazovat na sloupec pomocí kódu, například následující:

 [!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
 [!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

 Naproti tomu při práci s netypové datové sady, je ekvivalentní kódu:

 [!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
 [!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

 Typové přístup není pouze snadněji číst, ale také plně podporované technologii IntelliSense v sadě Visual Studio **Editor kódu**. Kromě toho snazší s ním pracovat, poskytuje syntaxe typové datové sady typ kontroly při kompilaci, výrazně snižuje možnost chyb v přiřazení hodnoty k datové sadě členů. Pokud změníte název sloupce v vaší <xref:System.Data.DataSet> třídy a pak kompilace aplikace, obdržíte chybu sestavení. Chyby sestavení v dvojitým kliknutím **seznam úkolů**, můžete přejít přímo na řádky kódu, které odkazují na původní název sloupce. Přístup k tabulek a sloupců v typové datové sady je také rychlejší mírně za běhu vzhledem k tomu, že přístup je určený při kompilaci, ne prostřednictvím kolekce za běhu.

 I když typové datové sady mít celou řadu výhod, je užitečné v z různých důvodů netypové datové sady. Nejobvyklejší scénář je-li k dispozici pro datovou sadu žádné schéma. Této chybě může dojít, například aplikace komunikuje s komponenty, která vrátí datovou sadu, ale neznáte předem co je jeho strukturu. Podobně platí jsou časy při práci s daty, která nemá strukturou statické, předvídatelný. V takovém případě je nepraktické používat typové datové sady, protože jste k opětovnému vytvoření třídy typové datové sady s každé změně ve struktuře data.

 Obecně platí kolikrát bude při se můžete vytvořit datové sady dynamicky bez nutnosti schéma k dispozici. V takovém případě datová sada je jednoduše vhodnou strukturu, ve kterém můžete zachovat informace, tak dlouho, dokud dat může být reprezentován relační způsobem. Ve stejnou dobu můžete využít výhod funkce datovou sadu, například možnost k serializaci informace předat jiným procesem nebo zapsat soubor XML.

## <a name="see-also"></a>Viz také:

- [Nástroje datové sady](../data-tools/dataset-tools-in-visual-studio.md)