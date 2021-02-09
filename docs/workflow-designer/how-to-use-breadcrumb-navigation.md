---
title: 'Návrhář postupu provádění-postupy: použití navigace s popisem cesty'
description: Přečtěte si, jak pomocí navigace s popisem cesty získat přístup k podřízené aktivitě, jak přejít na aktivitu předchůdce, nebo můžete rozbalit nebo sbalit aktivity na místě.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e33ea580f46f09ab3bd4d75ba58a35518c3583c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894137"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Postupy: Používání navigace s popisem cesty

Existují tři hlavní způsoby, jak změnit sadu aktivit, které jsou zobrazeny v Návrhář postupu provádění:

1. Dvojím kliknutím přejdete na podřízenou aktivitu.

2. Kliknutím na tlačítko na panelu s popisem cesty přejdete k aktivitě předchůdce.

3. Rozbalte nebo sbalte aktivity na místě.

## <a name="using-breadcrumb-navigation"></a>Pomocí navigace s popisem cesty

1. Dvojím kliknutím na aktivitu Návrhář postupu provádění změníte kořenovou aktivitu na aktivitu kliknutí. Kliknutí na aktivitu se pak plně rozbalí v kořenu a její předchůdce se zobrazí na panelu s popisem cesty. To se někdy označuje jako přechod do aktivity nebo z ní.

2. Chcete-li přejít k předchůdci aktuální kořenové aktivity, klikněte na aktivitu v panelu s popisem cesty.

## <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozbalení nebo sbalení aktivity na místě

1. Kliknutím na dvojitou šipku u aktivity dojde k rozšíření nebo sbalení aktivity na místě.

2. Když se stav rozšíření změní kliknutím na tlačítko, nový stav rozšíření je uložen v jazyce XAML.

    > [!WARNING]
    > Ne všechny aktivity lze rozbalit na místě. Existují dva případy, kdy aktivitu nelze rozšířit na místo: Nadřazená aktivita nepovoluje, aby byly podřízené položky rozbaleny, (například aktivity ve vývojovém diagramu nelze rozšířit na místo), nebo Návrhář aktivity nedovoluje, aby byl rozšířen na místo. I když žádný z návrhářů aktivity zahrnutý v Návrhář postupu provádění nemá druhé chování, některé vlastní aktivity mohou toto chování vykazovat.

## <a name="expanding-all-or-collapsing-all-activities"></a>Rozbalení všech nebo sbalení všech aktivit

1. Pomocí tlačítek **Rozbalit vše** a **sbalit všechna** v uživatelském rozhraní můžete rozbalit nebo sbalit všechny aktivity v rámci aktuálního kořenu s popisem cesty. Všimněte si, že Rozbalit vše a Sbalit vše jsou globální stavy. To znamená, že když změníte kořenovou aktivitu pomocí navigace s popisem cesty, všechny stavy rozbalíte nebo sbalíte, dokud nekliknete na tlačítko **obnovit**.

2. Po použití možnosti Rozbalit vše nebo sbalit všechny stavy můžete kliknout na tlačítko **obnovit** , které se zobrazí, abyste se mohli podívat na stav dříve aplikovaný na každou aktivitu.

    > [!WARNING]
    > Pokud se u aktivity, jako <xref:System.Activities.Statements.Flowchart> je třeba, nerozhodlo o rozbalení, funkce přidružená tlačítkům **Rozbalit vše** a **sbalit všechna** jsou v Návrháři **vývojového diagramu** zakázané. Další informace o návrháři **vývojového diagramu** najdete v tématu [vývojové diagramy](../workflow-designer/flowchart-activity-designer.md) .

    > [!WARNING]
    > Možnost Rozbalit vše má také zvláštní efekt v Návrháři aktivity **Switch** a **TryCatch** . Po kliknutí na **Rozbalit vše** se zobrazí všechny případy přepínače a všechny bloky try/catch/finally. Kliknutím na tlačítko **obnovit** nebo **Sbalit vše** vrátíte tyto návrháře do jejich výchozího stavu, ze kterého můžete kliknutím na jednotlivý případ/blok zobrazit jeho obsah.
