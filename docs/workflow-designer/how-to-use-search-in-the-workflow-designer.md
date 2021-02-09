---
title: 'Postupy: Hledání v návrháři postupu provádění'
description: Naučte se hledat v Návrhář postupu provádění, abyste našli položky podle klíčového slova, abyste mohli snadněji vytvářet větší a složitější pracovní postupy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f42d3115-2ed2-4941-8f1e-92dac41c30fa
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6fb30d4846c24638f87989d2a7a716df06b0523b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894111"
---
# <a name="how-to-use-search-in-the-workflow-designer"></a>Postupy: Hledání v návrháři postupu provádění

Abyste usnadnili vytváření větších a složitějších pracovních postupů, můžete hledat v rámci Návrhář postupu provádění pro hledání položek podle klíčového slova. Všimněte si, že Návrhář nepodporuje nahrazení.

## <a name="quick-find"></a>Rychlé hledání

Rychlé hledání najde v Návrháři následující:

- Vlastnosti <xref:System.Activities.Activity> objektů, <xref:System.Activities.Statements.FlowNode> objektů, <xref:System.Activities.Statements.State> objektů, přechodů a dalších vlastních položek řízení toku.

- Proměnné

- Argumenty

- Výrazy

### <a name="use-quick-find"></a>Použít rychlé hledání

1. Pomocí návrháře pracovních postupů otevřete, stiskněte **CTRL + F** nebo vyberte **Upravit**  >  **Najít a nahradit**  >  **Rychlé hledání**.

2. Do textového pole **Najít** zadejte hledaný termín a klikněte na **Najít další**.

3. Hledaný termín se nachází v aktuálním pracovním postupu. Následující obrázek ukazuje zobrazovaný název aktivity umístěný v Návrháři:

   ![Výsledky hledání v Návrhář postupu provádění](../workflow-designer/media/designersearch.png)

## <a name="find-in-files"></a>Najít v souborech

Hledání v souborech vyhledává řetězce v souborech pracovního postupu, včetně souborů XAML.

### <a name="use-find-in-files"></a>Použít hledání v souborech

1. V aplikaci Visual Studio stiskněte klávesy **CTRL** + **SHIFT** + **F** nebo vyberte možnost **Upravit**  >  **Najít a nahradit**  >  **najít v souborech**.

2. Do textového pole **Najít** zadejte hledaný text a klikněte na **Najít vše**.

3. Výsledek hledání je zobrazen v zobrazení **výsledků hledání** . Dvojím kliknutím na výslednou položku přejdete na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.