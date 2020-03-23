---
title: 'Postup: Konfigurace projektů pro cílení na více platforem'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b86a5c95131a4dcb2e6af199b57e9c8302790b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114449"
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Postup: Konfigurace projektů pro cílení na více platforem

Visual Studio poskytuje způsob, jak řešení cílit na několik různých architektur procesoru nebo platformy najednou. K vlastnostem, které je chcete nastavit, se přistupuje prostřednictvím dialogového okna **Správce konfigurace.**

## <a name="target-a-platform"></a>Cílení na platformu

Dialogové okno **Konfigurátor** umožňuje vytvářet a nastavovat konfigurace a platformy na úrovni řešení a na úrovni projektu. Každá kombinace konfigurace a cíle na úrovni řešení může mít jedinečnou sadu vlastností s ním spojené, což vám [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] umožní snadno přepínat mezi, například konfigurace vydání, která se zaměřuje na platformu, konfigurace verze, která se zaměřuje na platformu x86 a konfigurace ladění, která se zaměřuje na platformu x86.

1. V nabídce **Sestavení** (Build) klikněte na **Správce konfigurace**.

2. V **poli Aktivní platforma řešení**vyberte platformu, na kterou má vaše řešení cílit, nebo vyberte ** \<Nový>** a vytvořte novou platformu. Visual Studio zkompiluje vaši aplikaci tak, aby cílila na platformu, která je nastavena jako aktivní platforma v dialogovém okně **Správce konfigurace.**

## <a name="remove-a-platform"></a>Odebrání platformy

Pokud si uvědomíte, že platformu nepotřebujete, můžete ji odebrat pomocí dialogového okna **Správce konfigurace.** Tím odeberete všechna nastavení řešení a projektu, která jste nakonfigurovali pro tuto kombinaci konfigurace a cíle.

1. V nabídce **Sestavení** (Build) klikněte na **Správce konfigurace**.

2. V **poli Aktivní platforma řešení**vyberte ** \<Upravit>**. Otevře se dialogové okno **Upravit platformy řešení.**

3. Klikněte na platformu, kterou chcete odebrat, a klikněte na **Odebrat**.

## <a name="target-multiple-platforms-with-one-solution"></a>Cílení na více platforem pomocí jednoho řešení

Vzhledem k tomu, že můžete změnit nastavení na základě kombinace nastavení konfigurace a platformy, můžete nastavit řešení, které může cílit na více než jednu platformu.

### <a name="to-target-multiple-platforms"></a>Cílení na více platforem

1. Pomocí **nástroje Configuration Manager** můžete přidat alespoň dvě cílové platformy pro řešení.

2. Ze seznamu **Aktivní platforma řešení** vyberte platformu, na kterou chcete cílit.

3. Sestavte řešení.

### <a name="to-build-multiple-solution-configurations-at-once"></a>Vytvoření více konfigurací řešení najednou

1. Pomocí **nástroje Configuration Manager** můžete přidat alespoň dvě cílové platformy pro řešení.

2. Okno **Dávkové sestavení** slouží k vytvoření několika konfigurací řešení najednou.

   Je možné mít platformu na úrovni řešení nastavenou například [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]na a nemají žádné projekty v rámci tohoto řešení zaměřené na stejnou platformu. Je také možné mít více projektů ve vašem řešení, z nichž každý se zaměřuje na různé platformy. Pokud máte některou z těchto situací, doporučujeme vytvořit novou konfiguraci s popisným názvem, abyste předešli nejasnostem.

## <a name="see-also"></a>Viz také

- [Postup: Vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)
- [Vysvětlení konfigurací sestavení](../ide/understanding-build-configurations.md)
- [Vytváření a čištění projektů a řešení v sadě Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
