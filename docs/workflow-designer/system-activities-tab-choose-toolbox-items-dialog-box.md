---
title: System. Activities, výběr položek sady nástrojů
description: V Návrhář postupu provádění se dozvíte, jak karta System. Activities zobrazuje seznam aktivit programovací model Windows Workflow Foundation (WF), šablon a položek, které máte k dispozici.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73027013916d909fd5d9f4c9f00949ce9a863708
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867942"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Karta System. Activities, dialogové okno zvolit položky sady nástrojů

Tato karta dialogového okna **zvolit položky sady nástrojů** zobrazuje seznam aktivit programovací model Windows Workflow Foundation (WF), šablon a položek, které jsou vám k dispozici. Chcete-li zobrazit tento seznam, vyberte možnost **zvolit položky sady nástrojů** v nabídce **nástroje** nebo kliknutím pravým tlačítkem myši na **panel nástrojů** a výběrem možnosti **zvolit položky** zobrazíte dialogové okno **zvolit položky sady nástrojů** a poté vyberte kartu **System. Activities** . Seznam obsahuje aktivity pracovního postupu ze sestavení System. Activities, System. ServiceModel. Activities a System. Activities. Core. Presentation. ve výchozím nastavení se ale kontrolují jenom zobrazené aktivity poskytnuté systémem a aktivity přidané prostřednictvím jiných sestavení, která jsou zobrazená v **sadě nástrojů** . Nedávno přidané aktivity jsou automaticky kontrolovány a zobrazeny v sadě **nástrojů** po kliknutí na tlačítko **OK** v dialogovém okně. Tyto položky se také zobrazí v sadě **nástrojů** v rámci nové kategorie, která odpovídá oboru názvů, kde se nachází aktivita/položka/šablona.

> [!WARNING]
> Pokud se pokusíte přidat sestavení, které neobsahuje žádné aktivity pracovního postupu, zobrazí se chybové dialogové okno s vysvětlením, že sestavení neobsahuje žádné aktivity.

Toto dialogové okno je projekt nezávislá, takže se na kartě **System. Activities** i nadále zobrazují samostatné XAML nebo typ projektu bez pracovního postupu.

Filtrování je provedeno na každé kartě a není možné přidat aktivity pracovního postupu prostřednictvím karty **komponenty rozhraní .NET** . Přidejte je pomocí samotné karty **System. Activities** .

Z této karty dialogového okna můžete zrušit kontrolu všech položek, které nechcete zobrazit v **sadě nástrojů** , nebo můžete použít možnost z nabídky **Odstranit** kliknutím pravým tlačítkem myši v sadě **nástrojů** a zrušit odkazování sestavení neodstranit položku ze **sady nástrojů**.

Vytvoření instance aktivity přetáhnutím a přetažením v Návrháři přidáte sestavení, které obsahuje položku na seznam odkazovaných sestavení automaticky. Také Pokud aktivita odkazuje na sestavení C, nepřidá C do odkazovaného seznamu sestavení. Sestavení C musí být v globální mezipaměti sestavení (GAC) nebo ve stejném adresáři jako aktivita B. V samostatném případě musí být sestavení v globální mezipaměti sestavení (GAC) nebo cesty testu VS. Jenom potom můžete aktivitu přetáhnout na plochu návrháře pracovního postupu.

Nastavení **sady nástrojů** se ve výchozím nastavení ukládají jako uživatelské možnosti, takže při příštím otevření **sady nástrojů** se zobrazí váš přizpůsobený seznam aktivit pracovních postupů. Jedním z nich je, že pokud jste přidali konkrétní položky domény do **sady nástrojů** prostřednictvím dialogového okna **Vybrat položky sady nástrojů** , pořád se tyto položky zobrazí, i když pracujete v konzolové aplikaci pracovního postupu. Pokud je nechcete zobrazit, odstraňte je pomocí nabídky po kliknutí pravým tlačítkem myši nebo zrušte jejich výběr pomocí dialogového okna **zvolit položky sady nástrojů** , jak bylo uvedeno dříve.

Sloupce v tomto dialogovém okně obsahují následující informace:

Název
Zobrazuje seznam názvů aktivit pracovních postupů aktuálně registrovaných na místním počítači.

Hosting
Zobrazuje hierarchii oboru názvů .NET, která definuje strukturu aktivity.

Název sestavení \
Zobrazuje název a verzi sestavení .NET, která obsahuje aktivitu.

Službě
Zobrazuje umístění sestavení .NET, které obsahuje aktivity pracovního postupu. Výchozím umístěním pro všechna sestavení je globální mezipaměť sestavení (GAC).

Pokud chcete uvedené součásti seřadit, vyberte libovolné záhlaví sloupce.
