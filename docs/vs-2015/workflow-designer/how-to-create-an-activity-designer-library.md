---
title: 'Postupy: vytvoření knihovny návrhářů aktivit | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 6802f92f349d15d48935f4e7c3db85abf7c12535
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258268"
---
# <a name="how-to-create-an-activity-designer-library"></a>Postupy: vytvoření knihovny návrhářů aktivit
Vlastní návrháři aktivit umožňují vytvářet uživatelské rozhraní pro standardní nebo vlastní aktivity. Řízení složitosti uživatelského rozhraní, aby bylo možné vytvořit více než jeden návrháře aktivit pro aktivitu. Tento scénář umožňuje vytvořit designery, které jsou přizpůsobené pro více cílových skupin.  
  
### <a name="to-create-an-activity-designer-library"></a>Chcete-li vytvořit knihovny návrháře aktivit  
  
1.  Spustit [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu...** Chcete-li otevřít **nový projekt** dialogové okno.  
  
3.  V **typy projektů** vyberte **pracovního postupu** buď z **Visual C#** nebo **jazyka Visual Basic** seskupení podle svých představ jazyk.  
  
4.  V **šablony** vyberte **knihovny návrháře aktivit**.  
  
5.  V **název** zadejte popisný název pro váš projekt, aby byl snadno identifikovat.  
  
6.  V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.  
  
7.  V **řešení** pole, zadejte popisný název pro vaše řešení a pak klikněte na tlačítko **OK**.  
  
    > [!NOTE]
    >  Pokud chcete přidat Konzolová aplikace pracovního postupu do existujícího řešení, otevřete toto řešení [!INCLUDE[vs2010](../includes/vs2010-md.md)], klikněte pravým tlačítkem na řešení v **Průzkumníka řešení**a vyberte **přidat**, pak **Nový projekt...** Chcete-li otevřít **nový projekt** dialogové okno. Pokračujte, jak je popsáno výše v tomto postupu.  
  
8.  Šablona projektu vytvoří definici návrháře aktivit v XAML a soubor implementace použití modelu code-behind ve zdrojovém kódu. [!INCLUDE[wfd1](../includes/wfd1-md.md)] Otevře a zobrazí na plátně návrháře aktivit.  
  
9. Přetáhněte [!INCLUDE[avalon1](../includes/avalon1-md.md)] ovládacích prvků z **nástrojů** na návrhovou plochu pro použití v Návrháři vaše vlastní aktivity.  Příklad implementace vlastního návrháře aktivit najdete v tématu [postupy: vytvoření vlastního návrháře aktivit](http://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).  
  
    > [!WARNING]
    >  Vlastní návrháři aktivit lze použít pro vlastní aktivit, stejně jako u výchozí [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]aktivity.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření projektu pracovního postupu](../workflow-designer/creating-a-workflow-project.md)