---
title: Dokumentace ke službě offline Nápověda
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc9fd8b8684782f92c27563fb5d19a46d61c554e
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378128"
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

Můžete nainstalovat a zobrazit obsah pro různé produkty a technologie v místním počítači pomocí aplikace Microsoft Help Viewer. Tyto produkty zahrnují Visual Studio, rozhraní .NET Framework, referenční informace k jazyku, SQL Server a vývoj pro Windows. Aplikaci Help Viewer vám umožní:

- Stahovat sady obsahu, které jsou také označovány jako knihy. To může být užitečné, pokud potřebujete k práci "do režimu offline" a mít dál přístup k dokumentaci.

- Témata hledat podle názvu pomocí procházení a vyhledávání obsahu.

- Vyhledejte předměty v rejstříku.

- Vyhledejte informace pomocí fulltextového vyhledávání.

- Zobrazení, Záložka a tisknout témata.

K instalaci aplikace Help Viewer, naleznete v tématu [instalace aplikace Microsoft Help Viewer](../help-viewer/installation.md). Začne číst témat nápovědy v aplikaci Help Viewer, spíše než online, přejděte na **pomáhají** nabídky v sadě Visual Studio a klikněte na tlačítko **nastavení předvoleb nápovědy** > **spuštění v aplikaci Help Viewer** .

> [!TIP]
> Dalším způsobem, jak stáhnout obsah místně, takže ji můžete zobrazit, pokud nemáte připojení k Internetu je stahovat PDF verzi ho. Mnoho sad dokumentace na webu docs.microsoft.com obsahovat odkaz na konci obsah (TOC) Chcete-li stáhnout soubor PDF, který obsahuje všechny články pro tento obsah.
>
> ![Stáhněte si PDF pro dokumentaci k sadě Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Prohlídka Prohlížeč nápovědy

Můžete vyhledat informace v nainstalovaném obsahu pomocí navigačních karet, zobrazit nainstalovaný obsah témat nebo karty a spravovat obsah pomocí **spravovat obsah** kartu. Můžete také provádět další úkoly pomocí tlačítek na panelu nástrojů a vyhledat další informace v pravém dolním rohu okna.

### <a name="navigation-tabs"></a>Navigační karty

|Tabulátor|Popis|
|---|-----------|
|Obsah|Zobrazí nainstalovaný obsah jako hierarchii (tabulka obsah). Můžete určit kritéria filtru zobrazených názvů.|
|Index|Abecední seznam indexovaný podmínky zobrazí. V indexu, určit kritéria filtru položek a vyžadují tento index položky obsahovaly nebo začínaly textem, který zadáte.|
|Oblíbené položky|Můžete "Oblíbené" témat výběrem **přidat k oblíbeným položkám** tlačítko a témat se zobrazí na této kartě. **Historie** části se zobrazí seznam témat, která jste nedávno navštívili.|
|Hledat|Obsahuje textové pole, kde můžete vyhledat výrazy kdekoli v obsahu, včetně kódu a v názvech témat.|

### <a name="view-topics"></a>Zobrazit témata

Každé téma se zobrazí na vlastní kartě a můžete otevřít více témat najednou.

### <a name="manage-content"></a>Správa obsahu

Můžete nainstalovat, aktualizovat, přesunout a odstranit obsah pomocí **spravovat obsah** kartu. V horní části karty, můžete použít **zdrojová data instalace** ovládacího prvku určit, zda chcete instalovat knihy z umístění v síti nebo z disku nebo identifikátor URI. **Cesta k místnímu úložišti** ukazuje, kde jsou knihy nainstalovány v místním počítači, a můžete je přesunout do jiného umístění výběrem pole **přesunout** tlačítko.

Seznam obsahu zobrazuje, které knihy lze nainstalovat nebo jste již nainstalovali, zda je k dispozici aktualizace a jak velké jsou jednotlivé knihy. Může instalovat nebo odebírat jednu nebo více knih výběrem příslušné **přidat** nebo **odebrat** odkazy a potom kliknete **aktualizace** tlačítko **čekající na vyřízení změny** podokně. Pokud jsou aktualizace dostupné pro některé knihy, které jste již nainstalovali, můžete tento obsah aktualizovat kliknutím **pro stažení klikněte zde** odkaz v dolní části okna. Všechny nainstalované knihy navíc jsou aktualizovány, pokud při instalaci dalších knih jsou k dispozici aktualizace.

> [!NOTE]
> Funkce **spravovat obsah** kartu se můžou lišit, pokud správce aplikace Help Viewer konkrétní funkce deaktivuje nebo pokud je k dispozici bez připojení k Internetu.

### <a name="toolbar-buttons"></a>Tlačítka panelu nástrojů

V panelu nástrojů **aplikace Help Viewer** okno obsahuje následující tlačítka:

- **Zobrazit téma v obsahu** tlačítko zobrazí umístění tématu **obsah** kartu.

- **Přidat k oblíbeným položkám** tlačítko přidá aktivní téma **Oblíbené položky** kartu.

- **Najdete v tématu** tlačítko zvýrazní hledaný text v aktivním tématu.

- **Tisk** tlačítko vytiskne nebo zobrazí náhled aktivního tématu.

- **Možnosti prohlížeče** tlačítko zobrazí nastavení, například jak velikost zobrazovaného textu, počet výsledků hledání se vraťte, počet témat, chcete-li zobrazit v historii a zda chcete zjišťovat aktualizace online.

- **Spravovat obsah** tlačítko umožňuje **spravovat obsah** aktivní kartou.

- Kliknutím na malý trojúhelník na pravé straně se otevře seznam karet, včetně karet s tématy a **spravovat obsah** kartu. Můžete k němu na aktivní kartě Název karty.

## <a name="see-also"></a>Viz také:

- [Instalace aplikace Microsoft Help Viewer](../help-viewer/installation.md)
- [Příručka pro správce Prohlížeč nápovědy](../help-viewer/administrator-guide.md)
- [Instalace a Správa místního obsahu](../help-viewer/install-manage-local-content.md)
