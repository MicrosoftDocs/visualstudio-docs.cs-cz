---
title: Pozdní vazba v řešeních pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5616ce958747f90c8015df858f657299ba52852b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572547"
---
# <a name="late-binding-in-office-solutions"></a>Pozdní vazba v řešeních pro systém Office
  Některé typy v objektové modely aplikací Office poskytují funkce, které jsou k dispozici prostřednictvím funkce pozdní vazba. Například některé metody a vlastnosti, může vracet různé typy objektů v závislosti na kontextu aplikace Office a některé typy můžou zpřístupnit různé metody nebo vlastnosti v různých kontextech.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Visual Basic, projekty, kde **možnost striktní** je vypnuto a Visual C# projektů cílených [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] může spolupracovat přímo s typy, které využívají tyto funkce pozdní vazba.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Implicitní a explicitní přetypování objektu návratové hodnoty  
 Mnoho metod a vlastností v aplikaci Microsoft Office, vrátí primární spolupracující sestavení (PIA) <xref:System.Object> hodnoty, protože se může vracet různé typy objektů. Například <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> vlastnost vrátí <xref:System.Object> vzhledem k tomu může být hodnoty <xref:Microsoft.Office.Interop.Excel.Worksheet> nebo <xref:Microsoft.Office.Interop.Excel.Chart> objekt, v závislosti na tom, co je aktivním listem.  
  
 Při vrácení metody nebo vlastnosti <xref:System.Object>, je nutné explicitně převést (v jazyce Visual Basic) objekt správný typ v projekty Visual Basic kde **možnost striktní** zapnutý. Není nutné explicitně přetypovat <xref:System.Object> návratové hodnoty v projektech Visual Basic kde **možnost striktní** je vypnutý.  
  
 Ve většině případů referenční dokumentaci k nástroji uvádí možné typy návratovou hodnotu pro člena, který vrátí <xref:System.Object>. Převádění nebo přetypování objekt umožňuje technologii IntelliSense pro objekt v editoru kódu.  
  
 Informace o převodu v jazyce Visual Basic najdete v tématu [implicitní a explicitní převody &#40;jazyka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) a [CType – funkce &#40;jazyka Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje, jak převést objekt na určitý typ v projektu jazyka Visual Basic kde **možnost striktní** zapnutý. V tomto typu projektu musíte explicitně přetypovat <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> vlastnosti <xref:Microsoft.Office.Interop.Excel.Range>. Tento příklad vyžaduje projekt aplikace Excel na úrovni dokumentu a s listu třídy s názvem `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Následující příklad kódu ukazuje, jak implicitně převést na určitý typ objektu v projektu jazyka Visual Basic kde **možnost striktní** je vypnutý nebo v projektu jazyka Visual C#, jehož cílem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. V těchto typech projektů <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> vlastnost je implicitně převést na <xref:Microsoft.Office.Interop.Excel.Range>. Tento příklad vyžaduje projekt aplikace Excel na úrovni dokumentu a s listu třídy s názvem `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Přístupu členů, které jsou dostupné pouze prostřednictvím pozdní vazba  
 Některé vlastnosti a metody v PIA Office jsou k dispozici pouze prostřednictvím pozdní vazba. V jazyce Visual Basic projekty kde **možnost striktní** je v projektech Visual C# nebo vypnout cílených [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] nebo [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], pozdní vazba funkce v těchto jazycích můžete použít pro přístup ke členům pozdní vazbu. V jazyce Visual Basic projekty kde **možnost striktní** zapnutý, reflexe musí používat pro přístup tito členové.  
  
### <a name="examples"></a>Příklady  
 Následující příklad kódu ukazuje, jak přístup ke členům pozdní vazba v projektu jazyka Visual Basic kde **možnost striktní** je vypnutý nebo v projektu jazyka Visual C#, jehož cílem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tento příklad používá pozdní vazbu **název** vlastnost **otevřít soubor** dialogové okno v aplikaci Word. Pokud chcete použít v tomto příkladu, spusťte z `ThisDocument` nebo `ThisAddIn` – třída v projektu aplikace Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Následující příklad kódu ukazuje, jak provést stejný úkol v projektu jazyka Visual Basic pomocí reflexe kde **možnost striktní** zapnutý.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Viz také:  
 [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Použití typu dynamic &#40;C&#35; Průvodce programováním&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict – příkaz](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexe (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexe (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)  
  
  