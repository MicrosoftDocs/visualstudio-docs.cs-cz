---
title: Karta System. Activities, dialogové okno zvolit položky sady nástrojů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655173"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Karta System.Activities, dialogové okno Zvolit položky panelu nástrojů
Tato karta dialogového okna **zvolit položky sady nástrojů** zobrazí seznam [!INCLUDE[wf](../includes/wf-md.md)]ch aktivit, šablon a položek, které jsou vám k dispozici. Chcete-li zobrazit tento seznam, vyberte možnost **zvolit položky sady nástrojů** v nabídce **nástroje** nebo kliknutím pravým tlačítkem myši na **panel nástrojů** a výběrem možnosti **zvolit položky** zobrazíte dialogové okno **zvolit položky sady nástrojů** a potom vyberte jeho  **Karta System. Activities** . mimo pole obsahuje seznam aktivity pracovního postupu od sestavení System. Activities, System. ServiceModel. Activities a System. Activities. Core. Presentation. ve výchozím nastavení se ale kontrolují jenom zobrazené aktivity poskytnuté systémem a aktivity přidané prostřednictvím jiných sestavení, která jsou zobrazená v **sadě nástrojů** . Nedávno přidané aktivity jsou automaticky kontrolovány a zobrazeny v sadě **nástrojů** po kliknutí na tlačítko **OK** v dialogovém okně. Tyto položky se také zobrazí v sadě **nástrojů** v rámci nové kategorie, která odpovídá oboru názvů, kde se nachází aktivita/položka/šablona.

> [!WARNING]
> Pokud se pokusíte přidat sestavení, které neobsahuje žádné aktivity pracovního postupu, zobrazí se chybové dialogové okno s vysvětlením, že sestavení neobsahuje žádné aktivity.

 Toto dialogové okno je projekt nezávislá, takže se na kartě **System. Activities** i nadále zobrazují samostatné XAML nebo typ projektu bez pracovního postupu.

 Filtrování se provádí na každé kartě. To znamená, že není možné přidat aktivity pracovního postupu prostřednictvím karty **součásti .NET** . Musí být přidány prostřednictvím samotné karty **System. Activities** .

 Z této karty dialogového okna můžete zrušit kontrolu všech položek, které nechcete zobrazit v sadě **nástrojů** , nebo můžete použít možnost **Odstranit** kontextovou nabídku v **sadě nástrojů** a zrušit odkazování sestavení neodebírat položku z  **Sada nástrojů**.

 Vytvoření instance aktivity přetáhnutím a přetažením v Návrháři přidáte sestavení, které obsahuje položku na seznam odkazovaných sestavení automaticky. Také Pokud aktivita odkazuje na sestavení C, nepřidá C do odkazovaného seznamu sestavení. Sestavení C musí být v globální mezipaměti sestavení (GAC) nebo ve stejném adresáři jako aktivita B. V samostatném případě musí být sestavení v globální mezipaměti sestavení (GAC) nebo cesty testu VS. Jenom potom můžete aktivitu přetáhnout na plochu návrháře pracovního postupu.

 Nastavení **sady nástrojů** se ve výchozím nastavení ukládají jako uživatelské možnosti, takže při příštím otevření **sady nástrojů**se zobrazí váš přizpůsobený seznam aktivit pracovních postupů. Jedním z nich je, že pokud jste přidali konkrétní položky domény do **sady nástrojů** prostřednictvím dialogového okna **Vybrat položky sady nástrojů** , pořád se tyto položky zobrazí, i když pracujete v konzolové aplikaci pracovního postupu. Pokud je nechcete zobrazit, odstraňte je pomocí místní nabídky nebo zrušte jejich výběr pomocí dialogového okna **zvolit položky sady nástrojů** , jak bylo uvedeno dříve.

 Sloupce v tomto dialogovém okně obsahují následující informace:

 Název obsahuje seznam názvů aktivit pracovních postupů aktuálně zaregistrovaných na místním počítači.

 Obor názvů zobrazuje hierarchii oboru názvů .NET Framework knihovny tříd, který definuje strukturu aktivity.

 Název sestavení zobrazuje název a verzi .NET Framework sestavení, které obsahuje aktivitu.

 Adresář zobrazuje umístění sestavení .NET Framework, které obsahuje aktivity pracovního postupu. Výchozím umístěním pro všechna sestavení je globální mezipaměť sestavení (GAC).

 Pokud chcete uvedené součásti seřadit, vyberte libovolné záhlaví sloupce.