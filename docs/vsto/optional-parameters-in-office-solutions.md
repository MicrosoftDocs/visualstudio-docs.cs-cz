---
title: Volitelné parametry v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4a9737ae9e256cdc9862c0d7725e9bffda5b633
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882571"
---
# <a name="optional-parameters-in-office-solutions"></a>Volitelné parametry v řešeních pro systém Office
  Mnoho metod v objektové modely aplikací sady Microsoft Office přijmout volitelné parametry. Pokud používáte Visual Basic pro vývoj řešení pro Office v sadě Visual Studio, nemáte předat hodnotu pro volitelné parametry, protože jsou automaticky použity výchozí hodnoty pro každý parametr chybí. Ve většině případů můžete vynechat volitelné parametry v projektech Visual C#. Ale nejde vynechat volitelné **ref** parametry `ThisDocument` tříd v projektech aplikace Word úrovni dokumentu.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Další informace o práci s volitelnými parametry v projektech Visual C# a Visual Basic najdete v tématu [pojmenované a nepovinné argumenty &#40;C&#35; programováním&#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) a [volitelné parametry &#40;Jazyka Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).  
  
> [!NOTE]  
>  V dřívějších verzích sady Visual Studio musíte předat hodnotu pro každý volitelný parametr v projektech Visual C#. Pro usnadnění práce těchto projektů zahrnout globální proměnnou s názvem `missing` , můžete předat volitelný parametr Pokud chcete použít výchozí hodnotu parametru. Projekty Visual C# pro Office v sadě Visual Studio stále zahrnuje `missing` proměnnou, ale obvykle není nutné ho používat při vývoji řešení pro systém Office v [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], s výjimkou při volání metody s volitelným **ref** v parametrech `ThisDocument` tříd v projektech na úrovni dokumentu pro aplikaci Word.  
  
## <a name="example-in-excel"></a>Příklad v aplikaci Excel  
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> Metoda má mnoho nepovinných parametrů. Můžete zadat hodnoty pro některé parametry a přijměte výchozí hodnotu ostatních, jak je znázorněno v následujícím příkladu kódu. Tento příklad vyžaduje úrovni dokumentu projekt s třídou list s názvem `Sheet1`.  
  
 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]  
  
## <a name="example-in-word"></a>Příklad v aplikaci Word  
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Metoda má mnoho nepovinných parametrů. Můžete zadat hodnoty pro některé parametry a přijměte výchozí hodnotu ostatních, jak je znázorněno v následujícím příkladu kódu.  
  
 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]  
  
## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Použití volitelných parametrů metod ve třídě ThisDocument v jazyce Visual C# projekty na úrovni dokumentu pro Word  
 Objektový model aplikace Word obsahuje mnoho metod s volitelným **ref** parametry, které přijímají <xref:System.Object> hodnoty. Ale nejde vynechat volitelné **ref** parametry metody generované `ThisDocument` třídy v úrovni dokumentu projekty Visual C# pro aplikaci Word. Visual C# můžete vynechat, nechte volitelné **ref** parametry pouze pro metody rozhraní, nikoli tříd. Například následující příklad kódu nelze kompilovat, protože nemůžete vynechat volitelné **ref** parametry <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodu `ThisDocument` třídy.  
  
 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]  
  
 Při volání metody `ThisDocument` třídy, postupujte podle následujících pokynů:  
  
- Přijměte výchozí hodnotu volitelně **ref** parametr, předejte `missing` proměnnou na parametr. `missing` Proměnná je automaticky definovaný v projektech Visual C# Office a bude mu přiřazena hodnota <xref:System.Type.Missing> v kódu generovaném projektu.  
  
- Zadat vlastní hodnotu pro volitelný **ref** deklarovat objekt, který je přiřazen k hodnotě, kterou chcete zadat parametr a objekt předat parametr.  
  
  Následující příklad kódu ukazuje, jak volat <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metodu tak, že zadáte hodnotu *ignoreUppercase* parametr a přijímat výchozí hodnota pro ostatní parametry.  
  
  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]  
  
  Pokud chcete napsat kód, který se vynechá volitelné **ref** parametry metody v `ThisDocument` třídy, můžete také volat stejnou metodu na <xref:Microsoft.Office.Interop.Word.Document> vrácený <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> vlastnost a vynechat možnost parametry z metody. Můžete to provést, protože <xref:Microsoft.Office.Interop.Word.Document> rozhraní, nikoli třída.  
  
  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]  
  
  Další informace o parametrech typu hodnoty a odkazu, naleznete v tématu [předávání argumentů podle hodnoty a podle reference &#40;jazyka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (pro jazyk Visual Basic) a [předávat parametry &#40;C&#35; Průvodce programováním pro&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## <a name="see-also"></a>Viz také:  
 [Vývoj řešení pro systém Office](../vsto/developing-office-solutions.md)   
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
  