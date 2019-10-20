---
title: 'Postupy: použití vyhledávání v Návrhář postupu provádění'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 12bda4af085b8ab41d3e11841f24cd5dfd389738
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650301"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Postupy: použití vyhledávání v Návrhář postupu provádění

Abyste usnadnili vytváření větších a složitějších pracovních postupů, můžete hledat v rámci Návrhář postupu provádění pro hledání položek podle klíčového slova. Všimněte si, že Návrhář nepodporuje nahrazení.

## <a name="quick-find"></a>Rychlé hledání

Rychlé hledání najde v Návrháři následující:

- Vlastnosti objektů <xref:System.Activities.Activity>, <xref:System.Activities.Statements.FlowNode> objektů, <xref:System.Activities.Statements.State> objektů, přechodů a dalších vlastních položek řízení toku.

- Proměnné

- Arguments

- Výrazy

### <a name="use-quick-find"></a>Použít rychlé hledání

1. V okně návrháře pracovních postupů otevřete, stiskněte **CTRL + F**nebo vyberte **Upravit**  > **Najít a nahradit**  > **Rychlé hledání**.

2. Do textového pole **Najít** zadejte hledaný termín a klikněte na **Najít další**.

3. Hledaný termín se nachází v aktuálním pracovním postupu. Následující obrázek ukazuje zobrazovaný název aktivity umístěný v Návrháři:

   ![Výsledky hledání v Návrhář postupu provádění](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Najít v souborech

Hledání v souborech vyhledává řetězce v souborech pracovního postupu, včetně souborů XAML.

### <a name="use-find-in-files"></a>Použít hledání v souborech

1. V aplikaci Visual Studio stiskněte **Ctrl** +**SHIFT** +**F**nebo vyberte **Upravit**  > **Najít a nahradit**  > **najít v souborech**.

2. Do textového pole **Najít** zadejte hledaný text a klikněte na **Najít vše**.

3. Výsledek hledání je zobrazen v zobrazení **výsledků hledání** . Dvojím kliknutím na výslednou položku přejdete na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.