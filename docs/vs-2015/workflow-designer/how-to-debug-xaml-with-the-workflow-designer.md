---
title: 'Postupy: ladění XAML pomocí návrháře postupu provádění | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7ac99d5bcacb937db27867a1b02b2076fdce66c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176042"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Postupy: ladění XAML pomocí návrháře postupu provádění
Pracovní postupy jsou definována v XAML. Uživatelské rozhraní reprezentace pracovního postupu je nástavbou stromu XAML definování pracovního postupu. Je podobné ladění pracovních postupů v prostředí ladění [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Například při ladění XAML, místní hodnoty, kukátko a vlákna windows fungovat stejným způsobem jako stejně jako [!INCLUDE[wfd2](../includes/wfd2-md.md)] ladění. Kromě toho zobrazení zásobníku volání během ladění XAML je založené na řádku hierarchické zobrazení toku provádění pracovního postupu.  
  
> [!NOTE]
>  Pokud XAML pro pracovní postup je umístěn ve stejném sestavení, aktivity, část sestavení pro názvy tříd nejsou zahrnuty. Bez této části názvy tříd (aktivita) nelze načíst XAML za běhu. Nedoporučuje se definovat aktivity v stejný obor názvů jako hlavní projektu. v opačném případě XAML bude potřeba ručně upravit po upravována v návrháři.  
  
### <a name="to-debug-workflow-xaml"></a>Chcete-li ladit pracovní postup XAML  
  
1.  Otevřete projekt pracovního postupu nebo aktivity v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
2.  Nastavit zarážku na aktivitu nebo aktivity, který chcete ladit, jak je popsáno v [postupy: nastavení zarážek v pracovních postupech](../workflow-designer/how-to-set-breakpoints-in-workflows.md).  
  
3.  Klikněte pravým tlačítkem na soubor .xaml, který obsahuje definici pracovního postupu a vyberte **zobrazit kód**. Zobrazí se zarážku na stejném řádku jako deklarace prvku XAML, které jste nastavili zarážku na v návrhovém zobrazení aktivity.  
  
4.  Vyvolání ladicího programu, jak je popsáno v [postupy: vyvolání ladicího programu pracovních postupů](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Při provádění kódu dosáhnou některé z vašich zarážek, budou zvýrazněny elementu XAML přidružené k této zarážky. Chcete-li přejít k další zarážce, použijte **F10** nebo **F11** klíč.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: nastavení zarážek v pracovních postupech](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [Postupy: Spuštění ladicího programu pracovních postupů](../workflow-designer/how-to-invoke-the-workflow-debugger.md)