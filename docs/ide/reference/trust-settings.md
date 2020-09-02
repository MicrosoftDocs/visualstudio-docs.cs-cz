---
title: Nastavení důvěryhodnosti pro soubory a složky
description: Naučte se, jak změnit nastavení důvěryhodnosti pro soubory a složky, aby se zajistila bezpečnost sady Visual Studio.
author: 2percentsilk
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
ms.openlocfilehash: 492a94962d255a9d18dcabdababf7fa6a540ada1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88197391"
---
# <a name="configure-trust-settings-for-files-and-folders"></a>Konfigurace nastavení důvěryhodnosti pro soubory a složky

Visual Studio vyzývá ke schválení uživatelem před otevřením projektů, které mají [značku webu](/previous-versions/windows/internet-explorer/ie-developer/compatibility/ms537628(v=vs.85)). Pro zvýšení zabezpečení můžete také nakonfigurovat sadu Visual Studio tak, aby se před otevřením libovolného souboru nebo složky s označením webového atributu nebo neurčeného jako *důvěryhodného*zobrazila výzva k schválení uživatele. Kontroly souborů a složek jsou ve výchozím nastavení zakázané.

> [!WARNING]
> Před schválením souboru, složky nebo řešení byste se měli ujistit, že pochází od důvěryhodné osoby nebo z důvěryhodného umístění.

## <a name="configure-trust-settings"></a>Konfigurace nastavení důvěryhodnosti

Chcete-li změnit nastavení důvěryhodnosti, postupujte podle těchto kroků:

1. Otevřete **nástroje**  >  **Možnosti**  >  **Nastavení důvěryhodnosti** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti** .

2. Vyberte úroveň kontrol, které chcete pro soubory a složky. Můžete mít různé kontroly pro každé z nich. Možnosti:

   * **Bez ověření**: Visual Studio neprovede žádné kontroly.

   * **Ověřit označení webového atributu**: Pokud má soubor nebo složka značku webového atributu, aplikace Visual Studio zablokuje a požádá o oprávnění k otevření.

   * **Ověřte, že cesta je důvěryhodná**: Pokud cesta k souboru nebo složce není součástí seznamu **důvěryhodných cest** , aplikace Visual Studio zablokuje a požádá o oprávnění k otevření.

   ![Možnosti ověření důvěryhodnosti](media/trust-settings.png)

## <a name="add-trusted-paths"></a>Přidat důvěryhodné cesty

K přidání důvěryhodných cest použijte následující postup:

1. Otevřete **nástroje**  >  **Možnosti**  >  **Nastavení důvěryhodnosti** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti** .

2. V dialogovém okně **nastavení vztahu důvěryhodnosti** klikněte na **Přidat** a pak vyberte **soubor** nebo **Složka**.

3. Přejděte na adresu a vyberte soubor nebo složku, které chcete přidat do seznamu důvěryhodných souborů.

   Cesta k souboru nebo složce se zobrazí v seznamu **důvěryhodných cest** .

   ![Přidaných důvěryhodných cest](media/trusted-paths.png)

## <a name="remove-trusted-paths"></a>Odebrání důvěryhodných cest

K odebrání důvěryhodných cest použijte následující postup:

1. Otevřete **nástroje**  >  **Možnosti**  >  **Nastavení důvěryhodnosti** a v pravém podokně vyberte odkaz **Konfigurovat nastavení důvěryhodnosti** .

2. V seznamu **důvěryhodné cesty** vyberte cestu, kterou chcete odebrat, a potom klikněte na **Odebrat**.

   > [!TIP]
   > Chcete-li vybrat více položek, podržte při výběru cest stisknutou **klávesu SHIFT** .

   Vybrané cesty se odeberou ze seznamu **důvěryhodných cest** .
