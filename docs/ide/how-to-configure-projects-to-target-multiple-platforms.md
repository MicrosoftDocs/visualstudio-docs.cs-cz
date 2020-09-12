---
title: Konfigurace projektů pro více cílových platforem
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2643e7f413a68d820780db80c87818dd0b8b9c03
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036506"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Postupy: konfigurace projektů k cílení na více platforem

Visual Studio nabízí způsob, jak řešení cílit na několik různých architektur PROCESORů nebo platforem najednou. K nastavením těchto vlastností se dostanete prostřednictvím dialogového okna **Configuration Manager** .

## <a name="target-a-platform"></a>Cíl platformy

Dialogové okno **Configuration Manager** umožňuje vytvářet a nastavovat konfigurace a platformy na úrovni řešení a projektu. Každá kombinace konfigurací a cílů na úrovni řešení může mít přidruženou jedinečnou sadu vlastností, což vám umožní snadno přepínat mezi například konfigurací vydání, která cílí na platformu [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] , konfigurace vydané verze, která cílí na platformu x86, a konfiguraci ladění, která cílí na platformu x86.

1. V nabídce **Sestavení** (Build) klikněte na **Správce konfigurace**.

2. V **poli Aktivní platforma řešení**vyberte platformu, pro kterou chcete své řešení cílit, nebo vyberte, pokud chcete **\<New>** vytvořit novou platformu. Sada Visual Studio zkompiluje vaši aplikaci a určí cílovou platformu, která je nastavena jako aktivní platforma v dialogovém okně **Configuration Manager** .

## <a name="remove-a-platform"></a>Odebrání platformy

Pokud si myslíte, že nemáte potřebnou platformu, můžete ji odebrat pomocí dialogového okna **Configuration Manager** . Tím se odeberou všechna nastavení řešení a projektů, která jste nakonfigurovali pro danou kombinaci konfigurace a cíle.

1. V nabídce **Sestavení** (Build) klikněte na **Správce konfigurace**.

2. V **poli Aktivní platforma řešení**vyberte **\<Edit>** . Otevře se dialogové okno **Upravit platformy řešení** .

3. Klikněte na platformu, kterou chcete odebrat, a klikněte na **Odebrat**.

## <a name="target-multiple-platforms-with-one-solution"></a>Naplánování více platforem jedním řešením

Vzhledem k tomu, že můžete změnit nastavení na základě kombinace nastavení konfigurace a platformy, můžete nastavit řešení, které může cílit na více než jednu platformu.

### <a name="to-target-multiple-platforms"></a>Cílení na více platforem

1. Použijte **Configuration Manager** k přidání alespoň dvou cílových platforem pro řešení.

2. Vyberte platformu, kterou chcete cílit ze seznamu **aktivních platforem řešení** .

3. Sestavte řešení.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Sestavení více konfigurací řešení najednou

1. Použijte **Configuration Manager** k přidání alespoň dvou cílových platforem pro řešení.

2. Okno **sestavení dávky** použijte k sestavení několika konfigurací řešení najednou.

   Je možné, že máte platformu na úrovni řešení nastavenou na, například [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] , a nemají žádné projekty v rámci tohoto řešení, které cílí na stejnou platformu. Ve vašem řešení je také možné mít více projektů, které cílí na různé platformy. Pokud máte jednu z těchto situací, doporučuje se vytvořit novou konfiguraci s popisným názvem, aby nedocházelo k nejasnostem.

## <a name="see-also"></a>Viz také

- [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Sestavování a čištění projektů a řešení v aplikaci Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
