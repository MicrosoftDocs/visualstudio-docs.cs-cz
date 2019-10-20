---
title: 'Postupy: přidání aktivit do sady nástrojů (starší verze) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656611"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Postupy: přidání aktivit do sady nástrojů (starší verze)
Při sestavování řešení pracovního postupu se staršími [!INCLUDE[wfd1](../includes/wfd1-md.md)], která cílí na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], je možné do projektu pracovního postupu přidat vlastní aktivity a jejich návrháři, kteří jsou umístěni v **sadě nástrojů** , a získat tak snadný přístup. Do **sady nástrojů** můžete také přidat aktivity přímo z knihovny DLL (Dynamic-Link Library).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Přidání aktivity do sady nástrojů z knihovny DLL

1. V části **pracovní postup systému Windows**klikněte pravým tlačítkem myši na plochu okna panelu nástrojů a pak klikněte na **zvolit položky**.

2. V dialogovém okně **zvolit položky sady nástrojů** klikněte na kartu **komponenty System. Activities** a pak klikněte na tlačítko **Procházet** v pravé dolní části okna.

3. Vyberte knihovnu DLL z adresáře souborů, který obsahuje implementaci vlastní aktivity, kterou chcete přidat do **sady nástrojů**, a poté klikněte na tlačítko **otevřít**.

4. Kliknutím na tlačítko **OK** dokončete přidávání aktivity do sady nástrojů.

## <a name="see-also"></a>Viz také
 Používání starších [aktivit pracovních postupů](../workflow-designer/legacy-workflow-activities.md) [návrháře aktivit v Návrháři](../workflow-designer/using-the-legacy-activity-designer.md)