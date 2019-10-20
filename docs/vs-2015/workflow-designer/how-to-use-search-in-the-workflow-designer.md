---
title: 'Postupy: použití vyhledávání v Návrhář postupu provádění | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 84f74b4718a7f976b386197a79692256ab49caa4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659126"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Postupy: použití vyhledávání v Návrhář postupu provádění
Aby bylo možné vytvořit větší a složitější pracovní postupy, můžete použít vyhledávání v Návrhář postupu provádění k hledání položek podle klíčového slova. Všimněte si, že Návrhář nepodporuje nahrazení. Hledání bude v Návrháři najít následující:

## <a name="quick-find"></a>Rychlé hledání
 Rychlé hledání bude v Návrháři najít následující:

- Vlastnosti objektů <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode> objektů, <xref:System.Activities.Statements.State> objektů, přechodů a dalších vlastních položek řízení toku.

- Proměnné

- Arguments

- Výrazy

#### <a name="using-quick-find"></a>Použití rychlého hledání

1. V okně návrháře pracovních postupů otevřete, stiskněte **CTRL + F**nebo vyberte **Upravit**, **Najít a nahradit**, **Rychlé hledání**.

2. Do textového pole **Najít** zadejte hledaný termín a klikněte na **Najít další**.

3. Hledaný termín se bude nacházet v aktuálním pracovním postupu. Následující snímek obrazovky ukazuje zobrazovaný název aktivity umístěný v návrháři.

     ![Výsledky hledání v Návrhář postupu provádění](../workflow-designer/media/designersearch.png "DesignerSearch")

## <a name="find-in-files"></a>Najít v souborech
 Použití Find v souborech vyhledá řetězce v souborech pracovního postupu, včetně souborů XAML.

#### <a name="using-find-in-files"></a>Použití Find v souborech

1. V aplikaci Visual Studio stiskněte **kombinaci kláves CTRL + SHIFT + F**nebo vyberte možnost **Upravit**, **Najít a nahradit**, **najít v souborech** .

2. Do textového pole **Najít** zadejte hledaný text a klikněte na **Najít vše** .

3. Výsledek hledání se zobrazí v zobrazení**výsledků hledání** [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Dvojím kliknutím na výslednou položku přejdete na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.