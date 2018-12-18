---
title: 'Postupy: Konfigurace projektů pro více cílových platforem'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 308858941d03f6341cf3d22af074be45d790e16b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930216"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Postupy: Konfigurace projektů pro více cílových platforem

Visual Studio poskytuje způsob, jak řešení, které cílí několika různými architekturami procesoru nebo platformy, najednou. Vlastnosti, které chcete nastavit tyto jsou přístupné prostřednictvím **nástroje Configuration Manager** dialogové okno.

## <a name="target-a-platform"></a>Cílové platformy

**Nástroje Configuration Manager** dialogové okno umožňuje vytvořit a nastavit na úrovni řešení a projektu konfigurace a platformy. Každou kombinaci konfigurace na úrovni řešení a cíle může mít jedinečnou sadu vlastností, které jsou spojené s, což umožňuje snadno přepínat mezi, například konfiguraci vydané verze, který cílí [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] platformy, konfiguraci vydané verze který cílí na x x86 platformu a konfiguraci ladění, který se zaměřuje x86 platformy.

1.  Na **sestavení** nabídky, klikněte na tlačítko **nástroje Configuration Manager**.

2.  V **pole platforma aktivního řešení**, vyberte platformu vašeho řešení do cíle, nebo vyberte  **\<nový >** vytvořit nové platformy. Sada Visual Studio zkompiluje vaší aplikace pro cílení na platformy, které je nastaveno jako aktivní platformu v **nástroje Configuration Manager** dialogové okno.

## <a name="remove-a-platform"></a>Odebrat platformu

Pokud zjistíte, že nemáte žádné požadavky platformu, můžete odebrat pomocí **nástroje Configuration Manager** dialogové okno. Tato akce odebere všechna nastavení řešení a projektů, které jste nakonfigurovali pro kombinaci konfigurace a cíl.

1.  Na **sestavení** nabídky, klikněte na tlačítko **nástroje Configuration Manager**.

2.  V **pole platforma aktivního řešení**vyberte  **\<Upravit >**. **Upravit platformy řešení** zobrazí se dialogové okno.

3.  Klikněte na platformu, kterou chcete odebrat a klikněte na tlačítko **odebrat**.

## <a name="target-multiple-platforms-with-one-solution"></a>Vyvíjet pro víc platforem s jedním z řešení

Vzhledem k tomu, že můžete změnit nastavení založené na kombinaci konfigurace a nastavení platformy, můžete nastavit řešení, které můžete cílit na více než jednu platformu.

### <a name="to-target-multiple-platforms"></a>Pro více cílových platforem

1.  Použití **nástroje Configuration Manager** přidat alespoň dvě cílové platformy pro řešení.

2.  Vyberte platformu, kterou chcete cílit na z **platformou aktivního řešení** seznamu.

3.  Sestavte řešení.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Chcete-li sestavení více konfigurací řešení najednou

1. Použití **nástroje Configuration Manager** přidat alespoň dvě cílové platformy pro řešení.

2. Použití **dávkové sestavení** okna k sestavení několika konfigurací řešení najednou.

   Je možné mít nastaveno na hodnotu, například platformu úrovni řešení [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], a mít žádné projekty v rámci tohoto řešení, které cílí na stejnou platformu. Také je možné mít více projektů v řešení, každý cílí na různé platformy. Doporučuje se, že pokud některou z těchto situací, můžete vytvořit novou konfiguraci pomocí popisný název, aby nedocházelo k záměně.

## <a name="see-also"></a>Viz také:

- [Postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Principy konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Sestavení a vyčištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
