---
title: Modul Common Language Runtime a vyhodnocování výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85cf4d2029dc25dc993fcc32b89fdc60bd91171d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779343"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Modul CLR a vyhodnocování výrazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  V sadě Visual Studio 2015 je zastaralý tímto způsobem implementace vyhodnocovače výrazů. Informace o implementace vyhodnocovače výrazů modulu CLR najdete v tématu [vyhodnocovače výrazů modulu CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) a [spravované ukázka Chyba při vyhodnocování výrazu](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Kompilátory, jako například Visual Basic a C# (vyslovováno C sharp), který cílí Common Language Runtime (CLR), vytvořit Microsoft Intermediate Language (MSIL), která se později zkompilované do nativního kódu. CLR poskytuje ladicího stroje (DE) Chcete-li ladit výsledný kód. Pokud chcete integrovat proprietární programovacího jazyka do rozhraní IDE sady Visual Studio, můžete vybrat kompilace do jazyka MSIL a proto nebudete muset psát vlastní DE. Ale budete muset zápis vyhodnocovače výrazů (EE), který je schopen vyhodnocování výrazů v rámci kontextu svůj oblíbený programovací jazyk.  
  
## <a name="discussion"></a>Diskuse  
 Výrazy jazyka počítače jsou obecně analyzovat vytvoří sadu datových objektů a sadu operátorů používá k manipulaci s nimi. Například výraz, který "A + B" může být analyzován použít operátor sčítání (+) a data objektů "A" a "B" může být výsledkem jiného datového objektu. Úplnou sadu datových objektů, operátory a jejich přidružení jsou nejčastěji vyjádřené v programu stromové struktury s operátory na uzly stromu a datové objekty na větve. Výraz, který má rozdělené do stromu formuláře se často nazývá analyzovaný strom.  
  
 Jakmile má být výraz, poskytovatel symbolů (SP) je volána k vyhodnocení každý datový objekt. Například, pokud "A" je definován ve více než jednu metodu a poté na otázku "Které A?" musí být zodpovězeny před hodnotou A lze zjistit. Odpověď vrácená této uložené Procedury je něco jako "Třetí položka v pátém zásobníku" nebo "A 50 bajtů nad rámec počáteční statické paměti přidělených této metody."  
  
 Kromě vytváření jazyka MSIL pro program samotné, kompilátory CLR může také vytvořit velmi popisné informace o ladění, která jsou zapsána do souboru databáze programu (PDB). Za předpokladu, kompilátor jazyka nechráněný vytvoří ladicí informace ve stejném formátu jako kompilátory CLR, je schopen identifikovat, že jazyk názvy datových objektů SP modulu CLR. Po zjistila pojmenované datový objekt EE používá objekt vazače pro přidružení (nebo vytvoření vazby) datového objektu do oblasti paměti, která obsahuje hodnotu tohoto objektu. DE můžete pak získat nebo nastavit novou hodnotu pro datový objekt.  
  
 Proprietární kompilátor může poskytnout informace o ladění pomocí volání CLR `ISymbolWriter` rozhraní (která je definovaná v rozhraní .NET Framework v oboru názvů `System.Diagnostics.SymbolStore`). Kompilace do jazyka MSIL a zápisu ladicích informací prostřednictvím těchto rozhraní, můžete použít speciální kompilátoru CLR DE a SP. To výrazně zjednodušuje integraci proprietární jazyk do IDE sady Visual Studio.  
  
 Když CLR DE volá proprietární EE vyhodnocení výrazu, DE poskytuje EE s rozhraními pro SP a objekt vazače. Díky tomu se zápis prostředků modulu CLR ladění je potřeba pouze implementovat rozhraní Chyba při vyhodnocování výrazu odpovídající; vazby a symbol zpracování za vás postará o modulu CLR.  
  
## <a name="see-also"></a>Viz také  
 [Zápis pro vyhodnocovač výrazů modulu CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

