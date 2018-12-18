---
title: Typové a netypové datové sady | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 71761826611c490a3fb43413acaa29eb6520138f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283787"
---
# <a name="typed-vs-untyped-datasets"></a>Typové a netypové datové sady
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Typové datové sady je datová sada, která je nejprve odvozené od základní třídy <xref:System.Data.DataSet> třídy a potom pomocí informací z **Návrhář Dataset**, které je uložený v souboru XSD pro generování nového silně typované třídy datové sady. Informace ze schématu (tabulky, sloupce a tak dále) je generována a zkompilovány do této třídy novou datovou sadu jako sada první třídy objektů a vlastností. Protože typové datové sady se dědí ze základní <xref:System.Data.DataSet> třídy, typovaná třída předpokládá, všechny funkce <xref:System.Data.DataSet> třídy a je možné pomocí metod, které berou instance <xref:System.Data.DataSet> jako parametr předávat třídu.  
  
 Netypové datové sady, naproti tomu nemá žádné odpovídající vestavěné schéma. Stejně jako v typové datové sady, netypové datové sady obsahuje tabulky, sloupce a tak dále, ale ty jsou dostupné jenom jako kolekce. (Však po ručně vytvářet tabulky a další datové prvky v netypovou datovou sadu můžete exportovat strukturu datové sady jako schéma datové sady pomocí <xref:System.Data.DataSet.WriteXmlSchema%2A> metoda.)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Kontrastní přístup k datům v typové a netypové datové sady  
 Třída typované datové sady má objektový model trvat jeho vlastnosti na skutečné názvy tabulek a sloupců. Například pokud pracujete s typové datové sady, můžete odkazovat na sloupec s použitím kódu, jako jsou následující:  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 Naproti tomu při práci s netypovou datovou sadu, je ekvivalentní kód:  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 Zadaný přístup je nejen snadněji čtou, ale také plně podporován technologií IntelliSense v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Editor kódu**. Nejen snadněji pracovat, ale poskytuje syntaxe pro typové datové sady v době kompilace, kontrolu typu výrazně snižuje možnost chyb při přiřazování hodnot k členům datové sady. Pokud změníte název sloupce ve vaší <xref:System.Data.DataSet> třídy a poté zkompilovat aplikaci, obdržíte chybu sestavení. Dvojitým kliknutím při sestavení **seznamu úkolů**, můžete přejít přímo na řádek nebo řádky kódu, které odkazují na původní název sloupce. Přístup do tabulek a sloupců v typovaného datová sada je mírně rychlejší za běhu také vzhledem k tomu, že přístup je určen v době kompilace, ne prostřednictvím kolekce za běhu.  
  
 I když typové datové sady mají celou řadu výhod, je užitečné v mnoha případech netypovou datovou sadu. Nejobvyklejšími scénář je, pokud není k dispozici pro datovou sadu bez schématu. Tato situace může nastat, například pokud vaše aplikace pracuje s komponenty, která vrací třídu dataset, ale neznáte předem co je jeho strukturu. Podobně jsou časy při práci s daty, která nemá žádné statické a předvídatelná struktura. V takovém případě je nepraktické používat typové datové sady, protože je potřeba znovu generovat třídy typové datové sady s každou změnou datové struktury.  
  
 Obecně platí mnohokrát se vám při můžete vytvořit datové sady dynamicky bez nutnosti schéma k dispozici. V takovém případě datová sada je jednoduše vhodnou strukturu ve kterém můžete zachovat informace, jako data může být reprezentována způsobem, relační. Ve stejnou dobu můžete využít výhod funkcí datové sady, například možnost serializace informací o předat jiným procesem nebo vypsat soubor XML.

