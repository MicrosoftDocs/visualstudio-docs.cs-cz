---
title: Stránka události sestavení, Návrhář projektu (C#) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a73978bf78c26914e7ee6b21c27f1eb2e7682ea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223075"
---
# <a name="build-events-page-project-designer-c"></a>Stránka Události sestavení, návrhář projektu (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Použití **události sestavení** stránku **Návrháře projektu** k určení pokyny ke konfiguraci sestavení. Můžete také zadat podmínky, za kterých jsou spuštěny žádné události po sestavení. Další informace najdete v tématu [jak: Specify Build Events (C#)](../../ide/how-to-specify-build-events-csharp.md)a [jak: Specify Build Events (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Konfigurace**  
 Tento ovládací prvek není na této stránce upravovat. Popis tohoto ovládacího prvku, naleznete v tématu [stránku sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Platforma**  
 Tento ovládací prvek není na této stránce upravovat. Popis tohoto ovládacího prvku, naleznete v tématu [stránku sestavení, Návrhář projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Příkazový řádek události před sestavením**  
 Určuje všechny příkazy se mají provést před začátkem sestavení. Zadejte dlouhé příkazy, klikněte na tlačítko **upravit před sestavením** zobrazíte [pre-build Event/po sestavení příkazového řádku dialogové okno události](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Události před sestavením nebudou spuštěny, pokud je aktuální projekt a není aktivováno žádné sestavení.  
  
 **Příkazový řádek události po sestavení**  
 Určuje všechny příkazy k provedení po skončení sestavování. Zadejte dlouhé příkazy, klikněte na tlačítko **upravit POST-Build** zobrazíte **pre-build Event/po sestavení příkazového řádku dialogové okno události**.  
  
> [!NOTE]
>  Přidat `call` než vše post-build příkazy, které spouštějí soubory .bat. Například `call C:\MyFile.bat` nebo `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Spustit událost po sestavení**  
 Následující podmínky pro událost po sestavení ke spuštění, určuje, jak je znázorněno v následující tabulce.  
  
|Možnost|Výsledek|  
|------------|------------|  
|**Vždy**|Událost po sestavení se spustí bez ohledu na to, zda byl sestaven úspěšně.|  
|**Při úspěšném sestavení**|Událost po sestavení spustí-li sestavení úspěšné. Díky tomu se událost se spustí i pro projekt, který je aktuální, tak dlouho, dokud sestavení úspěšné.|  
|**Když sestavení aktualizuje výstup projektu**|Událost po sestavení poběží pouze po kompilátoru výstupního souboru (.exe nebo .dll) se liší od předchozí výstupní soubor kompilátoru. Událost po sestavení se díky tomu se nespustil, když je aktuální projekt.|  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení událostí sestavení (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Postupy: určení událostí sestavení (C#)](../../ide/how-to-specify-build-events-csharp.md)   
 [Referenční dokumentace k vlastnostem projektu](../../ide/reference/project-properties-reference.md)   
 [Kompilace a sestavení](../../ide/compiling-and-building-in-visual-studio.md)



