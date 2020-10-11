---
title: Dokumentace k offline nápovědě
description: Nainstalujte a zobrazte dokumentaci k offline nápovědě pro různé produkty a technologie, jako je například Visual Studio a .NET, pomocí Microsoft Help Viewer.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76e0ec4755584a7021d4f5489500aa53b9bad87e
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878966"
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

Pomocí Microsoft Help Viewer můžete na místní počítač nainstalovat a zobrazit obsah různých produktů a technologií. Mezi tyto produkty patří sady Visual Studio, .NET, Language Reference, SQL Server a vývoj pro Windows. Help Viewer umožňuje:

- Stáhněte si sady obsahu, které jsou také označovány jako knihy. To může být užitečné, pokud potřebujete pracovat "offline" a stále mít přístup k dokumentaci.

- Vyhledat témata podle názvu procházením a hledáním obsahu.

- Vyhledejte předměty v indexu.

- Hledání informací pomocí fulltextového vyhledávání.

- Témata zobrazení, záložek a tisk.

Chcete-li nainstalovat prohlížeč nápovědy, přečtěte si téma [instalace Microsoft Help Viewer](../help-viewer/installation.md). Chcete-li začít číst témata nápovědy v aplikaci Help Viewer místo online, přejděte do nabídky **help** v sadě Visual Studio a pak zvolte **nastavit předvolby nápovědy**  >  **Spustit v aplikaci Help Viewer**.

> [!TIP]
> Jiný způsob, jak místně stahovat obsah, abyste ho mohli zobrazit v případě, že nemáte připojení k Internetu, můžete si stáhnout jeho verzi ve formátu PDF. Mnohé sady dokumentace v docs.microsoft.com zahrnují odkaz na konec obsahu (obsah), ve kterém můžete stáhnout soubor PDF, který obsahuje všechny články pro daný obsah.
>
> ![Dokumentace ke stažení PDF pro Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Prohlídka programu Help Viewer

Informace v nainstalovaném obsahu můžete najít pomocí navigačních karet, zobrazit nainstalovaného obsahu na kartě nebo na kartách témat a spravovat obsah pomocí karty **Spravovat obsah** . Další úkoly můžete provádět také pomocí tlačítek na panelu nástrojů a vyhledat další informace v pravém dolním rohu okna.

### <a name="navigation-tabs"></a>Navigační karty

|Karta|Description|
|---|-----------|
|Obsah|Zobrazí nainstalovaný obsah jako hierarchii (obsah). Můžete zadat kritéria pro filtrování zobrazených názvů.|
|Index|Zobrazí abecední seznam indexovaných podmínek. Můžete vyhledat index, zadat kritéria pro filtrování položek a vyžadovat, aby položky indexu buď obsahovaly, nebo začínaly textem, který určíte.|
|Oblíbené|Témata "oblíbená" můžete vybrat kliknutím na tlačítko **Přidat k oblíbeným** a tato témata se zobrazí na této kartě. V části **Historie** se zobrazí seznam témat, která jste nedávno prohlíželi.|
|Hledat|Poskytuje textové pole, kde můžete hledat výrazy kdekoli v obsahu, včetně názvů kódu a témat.|

### <a name="view-topics"></a>Zobrazit témata

Každé téma se zobrazí na vlastní kartě a můžete současně otevřít více témat.

### <a name="manage-content"></a>Správa obsahu

Obsah můžete nainstalovat, aktualizovat, přesunout a odstranit pomocí karty **Spravovat obsah** . V horní části karty můžete použít správu **zdrojového kódu** k určení, zda se mají instalovat knihy z umístění v síti, nebo z disku nebo identifikátoru URI. V poli **cesta k místnímu úložišti** se zobrazí informace o tom, kde jsou knihy nainstalovány v místním počítači, a můžete je přesunout do jiného umístění, a to tak, že kliknete na tlačítko **přesunout** .

Seznam obsahu zobrazuje, které knihy si můžete nainstalovat nebo už máte nainstalovanou, zda je k dispozici aktualizace a jak velké jsou jednotlivé knihy. Jednu nebo více knih můžete nainstalovat nebo odebrat tak, že vyberete příslušné odkazy **Přidat** nebo **Odebrat** a pak kliknete na tlačítko **aktualizovat** v podokně **nedokončené změny** . Pokud jsou aktualizace dostupné pro všechny knihy, které jste už nainstalovali, můžete tento obsah aktualizovat tak, že v dolní části okna **kliknete na odkaz kliknout sem pro stažení** . Kromě toho jsou všechny nainstalované knihy aktualizovány, pokud jsou k dispozici aktualizace při instalaci dalších seznamů.

> [!NOTE]
> Funkce karty **Spravovat obsah** se může lišit, pokud správce aplikace Help Viewer tyto funkce deaktivuje nebo pokud není k dispozici žádný přístup k Internetu.

### <a name="toolbar-buttons"></a>Tlačítka panelu nástrojů

Panel nástrojů v okně aplikace **Help Viewer** obsahuje následující tlačítka:

- Tlačítko **Zobrazit téma v obsahu** zobrazuje umístění tématu na kartě **obsah** .

- Tlačítko **Přidat k oblíbeným** položkám přidá aktivní téma na kartu **Oblíbené** .

- Tlačítko **najít v tématu** zvýrazňuje hledaný text v aktivním tématu.

- Tlačítko **Tisk** tiskne nebo zobrazuje náhled aktivního tématu.

- Tlačítko **Možnosti prohlížeče** zobrazí nastavení, například velikost zobrazeného textu, počet výsledků hledání, které se mají vrátit, počet témat, která se mají zobrazit v historii, a zda chcete vyhledat aktualizace online.

- Tlačítko **Spravovat obsah** zpřístupní aktivní kartu **Spravovat obsah** .

- Malý trojúhelník na pravé straně otevře seznam karet, včetně karet témat a karty **Spravovat obsah** . Můžete zvolit název karty a nastavit tak jeho aktivní kartu.

## <a name="see-also"></a>Viz také

- [Instalace Microsoft Help Viewer](../help-viewer/installation.md)
- [Příručka pro správce prohlížeče nápovědy](../help-viewer/administrator-guide.md)
- [Instalace a Správa místního obsahu](../help-viewer/install-manage-local-content.md)
