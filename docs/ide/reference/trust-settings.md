---
title: Nastavení důvěryhodnosti pro soubory a složky
description: Přečtěte si, jak změnit nastavení důvěryhodnosti souborů a složek, aby visual studio zůstalo zabezpečené.
author: abuchholtzau
ms.author: allisb
ms.date: 09/05/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.PathTrustOptions
helpviewer_keywords:
- file security
- folder security
- mark of the web
- trusted files
- trusted folders
ms.openlocfilehash: 011673bca7be569b5b350dc264148d5a7890d39c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62789623"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurace nastavení důvěryhodnosti souborů a složek

Visual Studio vyzve ke schválení uživatele před otevřením projektů, které mají [značku webu](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Chcete-li získat větší zabezpečení, můžete aplikaci Visual Studio také nakonfigurovat tak, aby před otevřením libovolného souboru nebo složky, která má značku webového atributu nebo která není označena jako *důvěryhodná*, vyzvala uživatele ke schválení . Kontroly souborů a složek jsou ve výchozím nastavení zakázány.

> [!WARNING]
> Před schválením souboru, složky nebo řešení byste se měli ujistit, že soubor, složka nebo řešení pocházejí od důvěryhodné osoby nebo důvěryhodného umístění.

## <a name="configure-trust-settings"></a>Konfigurace nastavení důvěryhodnosti

Chcete-li změnit nastavení důvěryhodnosti, postupujte takto:

1. Otevřete**Možnosti** >  **nástrojů** > **Důvěřovat nastavení** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti.**

2. Zvolte úroveň kontrol, které chcete u souborů a složek. Pro každou z nich můžete mít různé kontroly. Dostupné možnosti:

   * **Žádné ověření**: Visual Studio neprovádí žádné kontroly.

   * **Ověřte značku webového atributu**: Pokud soubor nebo složka obsahuje značku webového atributu, visual studio zablokuje a požádá o povolení k otevření.

   * **Ověření, že cesta je důvěryhodná**: Pokud cesta k souboru nebo složce není součástí seznamu **Důvěryhodné cesty,** sada Visual Studio zablokuje a požádá o oprávnění k otevření.

   ![Možnosti ověření důvěryhodnosti](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Přidání důvěryhodných cest

Chcete-li přidat důvěryhodné cesty, postupujte takto:

1. Otevřete**Možnosti** >  **nástrojů** > **Důvěřovat nastavení** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti.**

2. V dialogovém okně **Důvěřovat nastavením** klepněte na **tlačítko Přidat** a pak vyberte **Soubor** nebo **složku**.

3. Přejděte do seznamu důvěryhodných položek a vyberte je.

   Cesta k souboru nebo složce se zobrazí v seznamu **Důvěryhodné cesty.**

   ![Přidány důvěryhodné cesty](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Odebrání důvěryhodných cest

Chcete-li odebrat důvěryhodné cesty, postupujte takto:

1. Otevřete**Možnosti** >  **nástrojů** > **Důvěřovat nastavení** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti.**

2. V seznamu **Důvěryhodné cesty** vyberte cestu, kterou chcete odebrat, a klepněte na tlačítko **Odebrat**.

   > [!TIP]
   > Chcete-li vybrat více položek, podržte při výběru cest stisknutou klávesu **Shift.**

   Vybrané cesty budou odebrány ze seznamu **Důvěryhodné cesty.**
