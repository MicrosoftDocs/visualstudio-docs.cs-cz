---
title: Připojené služby
description: Přidání úložiště dat, ověřování a nabízených oznámení Azure do mobilních aplikací z Visual Studia pro Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.openlocfilehash: 34a4344be0e48d41829a7bf7df660a91d4f897b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "67693092"
---
# <a name="connected-services-walkthrough"></a>Návod k připojeným službám

Pracovní postup Připojené služby přináší pracovní postup portálu Azure do Visual Studia pro Mac, takže nemusíte opustit projekt a přidávat služby.

Tento návod ukazuje, jak přidat back-endovou službu Azure, která přináší cloudové úložiště dat, ověřování a nabízená oznámení do aplikace PCL (Portable Class Library) napříč platformami.

1. Začněte poklepáním na uzel **Připojené služby** v řešení, které vyvolá **Galerii služeb**.
  Toto je seznam všech dostupných služeb pro typ aplikace. Kliknutím na něj vyberte službu (například **mobilní back-end se službou Azure App Service).**

    [![Uzel Připojené služby v Visual Studiu pro Mac](media/connected-services-image001-sml.png "Uzel Připojené služby v Visual Studiu pro Mac")](media/connected-services-image001.png#lightbox)

2. Stránka Podrobnosti o službě obsahuje popis služby a závislosti, které mají být nainstalovány.
  Kliknutím na tlačítko **Přidat** přidáte závislosti do aplikace:

    [![Mobilní back-end s Azure](media/connected-services-image002-sml.png "Mobilní back-end s Azure")](media/connected-services-image002.png#lightbox)

3. Závislosti je třeba přidat do PCL a projekty specifické pro platformu k práci.
  Zaškrtnutím zaškrtávacích políček přidáte službu do každého projektu, který na něj bude odkazovat (přímo nebo nepřímo):

    [![Zkontrolujte všechny projekty, které by měly odkazovat na službu](media/connected-services-image003-sml.png "Zkontrolujte všechny projekty, které by měly odkazovat na službu")](media/connected-services-image003.png#lightbox)

4. V dialogových oknech **Přijetí licence** pro balíčky NuGet zvolte **Přijmout.**
  Mohou existovat dvě dialogová okna, která mají být přijímána, jedno pro mobilníklienta a závislosti a druhé pro SQLiteStore, které je vyžadováno pro synchronizaci dat offline:

    [![Přijmout licenční smlouvy](media/connected-services-image004-sml.png "Přijmout licenční smlouvy")](media/connected-services-image004.png#lightbox)

    ![Okno Přijetí licence](media/connected-services-image005.png "Okno Přijetí licence")

5. Po přidání závislostí budete vyzváni k přihlášení pomocí účtu, který chcete použít ke komunikaci s Azure.
  Pokud jste už přihlášeni pomocí Microsoft ID, Visual Studio pro Mac se pokusí načíst vaše předplatná Azure a všechny aplikační služby s nimi spojené. Pokud nemáte žádná předplatná, můžete si je přidat tak, že si zaregistrujete bezplatnou zkušební verzi nebo si na webu Azure Portal zakoupíte plán předplatného.

6. Vyberte službu aplikace ze seznamu. Tím se kód šablony `MobileServiceClient` objektu vyplní odpovídající adresou URL služby aplikace v Azure:

    [![Výběr služby aplikace ze seznamu](media/connected-services-image006-sml.png "Výběr služby aplikace ze seznamu")](media/connected-services-image006.png#lightbox)

    Pokud nejsou uvedeny žádné služby, klikněte na tlačítko **Nový** (viz krok 9.)

7. Zkopírujte kód šablony `MobileServiceClient` pro pcl. Umístění souboru není důležité, pokud existuje pouze jedna instance.
  Doporučeným přístupem je `AzureService` vytvoření třídy, která zpracovává všechny `MobileServiceClient`interakce Azure a používá :

    ![Zkopírujte konfigurační kód do ap](media/connected-services-image007.png "Kopírování konfiguračního kódu do aplikace")

8. Podle dokumentace v **dalších krocích** přidejte do aplikace data, offline synchronizaci, ověřování a nabízená oznámení:

    [![Projděte si pokyny k dalším krokům](media/connected-services-image008-sml.png "Projděte si pokyny k dalším krokům")](media/connected-services-image008.png#lightbox)

9. Pokud nemáte žádné existující služby aplikace, můžete vytvořit nové služby z Visual Studia pro Mac.
  Kliknutím na tlačítko **Nový** v levém dolním rohu seznamu služeb otevřete dialogové okno **Nová služba aplikace:**

    [![Vytvoření nové služby aplikace ve Visual Studiu pro Mac](media/connected-services-image009-sml.png "Vytvoření nové služby aplikace ve Visual Studiu pro Mac")](media/connected-services-image009.png#lightbox)

Nová služba vyžaduje následující parametry:

- **Název služby aplikace** – jedinečný název/id plánu
- **Předplatné** – předplatné, které chcete použít k zaplacení služby
- **Skupina prostředků** – způsob nebo uspořádání všech prostředků Azure pro projekt. Možnost použít existující nebo vytvořit nový. Pokud se jedná o první službu Azure, vytvořte novou.
- **Plán služeb** – určuje umístění a náklady všech zdrojů, které jej používají. Možnost použít existující nebo vytvořit nový. Pokud se jedná o vaši první službu Azure, použijte výchozí nebo vytvořte novou ve volné vrstvě (F1).

Další informace naleznete v [dokumentaci](/azure/app-service-mobile/) k mobilním aplikacím.

## <a name="see-also"></a>Viz také

- [Připojené služby (Visual Studio ve Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)