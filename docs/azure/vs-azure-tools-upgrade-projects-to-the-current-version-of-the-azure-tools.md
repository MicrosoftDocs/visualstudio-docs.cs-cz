---
title: Upgradovat projekty na aktuální verzi nástrojů Azure
description: Zjistěte, jak upgradovat projekt Azure v aplikaci Visual Studio na aktuální verzi nástrojů Azure.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: f9f806ad2d5e9d72d9459ba48c0d7c9525acb30e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843771"
---
# <a name="how-to-upgrade-projects-to-the-current-version-of-the-azure-tools-for-visual-studio"></a>Postup upgradu projektů na aktuální verzi nástrojů Azure pro Visual Studio
## <a name="overview"></a>Přehled
Po instalaci aktuální verze nástrojů Azure (nebo předchozí verze, která je novější než 1,6) se budou automaticky upgradovat všechny projekty, které byly vytvořené pomocí nástrojů Azure Tools před 1,6 (listopad 2011), jakmile je otevřete. Pokud jste vytvořili projekty pomocí verze 1,6 (listopadu 2011) těchto nástrojů a stále máte nainstalovanou verzi, můžete tyto projekty otevřít ve starší verzi a později rozhodnout, zda je chcete upgradovat.

## <a name="how-your-project-changes-when-you-upgrade-it"></a>Způsob změny projektu při jeho upgradu
Pokud je projekt automaticky upgradován nebo pokud určíte, že chcete upgradovat, projekt je upraven pro práci s aktuálními verzemi určitých sestavení a některé vlastnosti jsou také změněny, jak je popsáno v této části. Pokud váš projekt vyžaduje, aby byly jiné změny kompatibilní s novějšími verzemi nástrojů, musíte tyto změny provést ručně.

* web.config soubor pro webové role a soubor app.config pro role pracovního procesu jsou aktualizovány tak, aby odkazovaly na novější verzi Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener.dll.
* Microsoft.WindowsAzure.StorageClient.dll, Microsoft.WindowsAzure.Diagnostics.dll a Microsoft.WindowsAzure.ServiceRuntime.dll sestavení jsou upgradována na nové verze.
* Profily publikování, které se uložily v souboru projektu Azure (. soubor ccproj), se přesunou do samostatného souboru s příponou. azurePubXml v podadresáři **publikovat** .
* Některé vlastnosti v profilu publikování jsou aktualizované tak, aby podporovaly nové a změněné funkce. **AllowUpgrade** nahrazuje **DeploymentReplacementMethod** , protože můžete aktualizovat nasazenou cloudovou službu současně nebo přírůstkově.
* Vlastnost **UseIISExpressByDefault** je přidána a nastavena na hodnotu false, aby webový server, který se používá pro ladění, nebude automaticky změněn z Internetová informační služba (IIS) na IIS Express. IIS Express je výchozím webovým serverem pro projekty vytvořené v novějších verzích nástrojů.
* Pokud je služba Azure Caching hostovaná v jedné nebo více rolích projektu, při upgradu projektu se změní některé vlastnosti v konfiguraci služby (soubor. cscfg) a definice služby (soubor. csdef). Pokud projekt používá balíček NuGet pro ukládání do mezipaměti Azure, projekt se upgraduje na nejnovější verzi balíčku. Měli byste otevřít soubor web.config a ověřit, zda byla konfigurace klienta během procesu upgradu správně udržovaná. Pokud jste přidali odkazy na sestavení klienta Azure Caching bez použití balíčku NuGet, tato sestavení se neaktualizují. Tyto odkazy musíte ručně aktualizovat na nové verze.

> [!IMPORTANT]
> Pro projekty F # je nutné ručně aktualizovat odkazy na sestavení Azure tak, aby odkazovaly na novější verze těchto sestavení.
>
>

### <a name="how-to-upgrade-an-azure-project-to-the-current-release"></a>Postup upgradu projektu Azure na aktuální verzi
1. Nainstalujte aktuální verzi nástrojů Azure do instalace sady Visual Studio, kterou chcete použít pro upgradovaný projekt, a pak otevřete projekt, který chcete upgradovat. Pokud byl projekt vytvořen pomocí nástrojů Azure pro vydání před 1,6 (listopad 2011), projekt se automaticky upgraduje na aktuální verzi. Pokud byl projekt vytvořen ve verzi z listopadu 2011 a tato verze je stále nainstalována, projekt se otevře v této verzi.
2. V Průzkumník řešení otevřete místní nabídku uzlu projektu, zvolte možnost **vlastnosti** a pak zvolte kartu **aplikace** dialogového okna, které se zobrazí.

    Karta **aplikace** zobrazuje verzi nástrojů, která je přidružená k projektu. Pokud se zobrazí aktuální verze nástrojů Azure, projekt už je upgradovaný. Pokud jste nainstalovali novější verzi nástrojů, než je karta zobrazená, zobrazí se tlačítko **upgrade** .
3. Chcete-li upgradovat projekt na aktuální verzi nástrojů, klikněte na tlačítko **upgrade** .
4. Sestavte projekt a pak vyřešte všechny chyby, které jsou výsledkem změn rozhraní API. Informace o tom, jak změnit kód pro novou verzi, najdete v dokumentaci ke konkrétnímu rozhraní API.
