---
title: 'Postupy: cílení na vícejazyčné uživatelské rozhraní Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5217f2d6cf67eced00c0c84b9bacda94573c5a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537498"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Postupy: cílení na vícejazyčné uživatelské rozhraní Office
  Rozhraní MUI (Multilingual User Interface) je funkce systém Microsoft Office, která koncovému uživateli umožňuje změnit jazyk uživatelského rozhraní. Například koncový uživatel, který pracuje s anglickou uživatelským ROZHRANÍm, může změnit jazyk uživatelského rozhraní na španělštinu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Pokud budou vaše aplikace používat lidé, kteří používají mnoho jazyků Office, můžete přidat kód, který automaticky změní jazyk řetězců uživatelského rozhraní tak, aby odpovídal jazyku používanému systémem Office v počítači uživatele (Pokud má uživatel nainstalované správné prostředky).

## <a name="to-check-the-current-office-ui-setting"></a>Chcete-li zjistit aktuální nastavení uživatelského rozhraní systému Office

1. Použijte <xref:System.Threading.Thread.CurrentUICulture%2A> vlastnost aktuálního vlákna. Nastavte jazyk řetězců uživatelského rozhraní tak, aby odpovídal jazyku používané verzi Office, která je aktuálně spuštěna v počítači uživatele.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Viz také
- [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Pozdní vazba v řešeních pro systém Office](../vsto/late-binding-in-office-solutions.md)
