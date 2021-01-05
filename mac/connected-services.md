---
title: Připojené služby
description: Naučte se, jak přidat službu Azure Data Storage, ověřování a nabízená oznámení z Visual Studio pro Mac do aplikace pro různé platformy.
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: sayedihashimi
ms.author: sayedha
ms.date: 11/06/2018
ms.topic: how-to
ms.openlocfilehash: 69ad6007283b3c56a8d0e5902cc2b9bdc445f220
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847085"
---
# <a name="connected-services-walkthrough"></a>Návod k připojeným službám

Pracovní postup připojených služeb přináší Azure Portal pracovní postup do Visual Studio pro Mac, takže nemusíte mít projekt v přidávání služeb.

Tento návod ukazuje, jak přidat službu back-endu Azure, která přináší cloudové úložiště dat, ověřování a nabízená oznámení v aplikaci Xamarin. Forms s přenosnou knihovnou tříd (PCL) pro více platforem.

1. Začněte tím, že dvakrát kliknete na uzel **připojené služby** v řešení, které přináší **galerii služeb**.
  Toto je seznam všech dostupných služeb pro typ aplikace. Kliknutím na položku vyberte službu (například **mobilní back-end s Azure App Service**).

    [![Uzel připojených služeb v Visual Studio pro Mac](media/connected-services-image001-sml.png "Uzel připojených služeb v Visual Studio pro Mac")](media/connected-services-image001.png#lightbox)

2. Stránka Podrobnosti služby obsahuje popis služby a závislosti, které mají být nainstalovány.
  Kliknutím na tlačítko **Přidat** přidáte závislosti do aplikace:

    [![Mobilní back-end s Azure](media/connected-services-image002-sml.png "Mobilní back-end s Azure")](media/connected-services-image002.png#lightbox)

3. Aby fungovaly, je nutné přidat závislosti do projektů PCL i pro konkrétní platformu.
  Zaškrtněte políčka pro přidání služby do každého projektu, který bude odkazovat na něj (buď přímo, nebo nepřímo):

    [![Zkontroluje všechny projekty, které by měly odkazovat na službu.](media/connected-services-image003-sml.png "Zkontroluje všechny projekty, které by měly odkazovat na službu.")](media/connected-services-image003.png#lightbox)

4. V dialogových oknech **přijetí licence** pro balíčky NuGet vyberte **přijmout** .
  Můžou existovat dvě dialogová okna, která se dají přijmout, jedna pro MobileClient a závislosti a druhá pro SQLiteStore, která se vyžaduje pro synchronizaci offline dat:

    [![Přijmout licenční smlouvy](media/connected-services-image004-sml.png "Přijmout licenční smlouvy")](media/connected-services-image004.png#lightbox)

    ![Okno přijetí licence](media/connected-services-image005.png "Okno přijetí licence")

5. Po přidání závislostí se zobrazí výzva, abyste se přihlásili pomocí účtu, který chcete použít ke komunikaci s Azure.
  Pokud jste už přihlášení pomocí ID Microsoftu, Visual Studio pro Mac se pokusí načíst vaše předplatná Azure a všechny služby App Service, které jsou k nim přidružené. Pokud nemáte žádná předplatná, můžete si ji přidat tak, že se zaregistrujete k bezplatné zkušební verzi nebo si koupíte plán předplatného v Azure Portal.

6. Vyberte ze seznamu službu App Service. Tím se kód šablony pro objekt vyplní `MobileServiceClient` odpovídající adresou URL služby App Service v Azure:

    [![Vybrat App Service ze seznamu](media/connected-services-image006-sml.png "Vybrat App Service ze seznamu")](media/connected-services-image006.png#lightbox)

    Pokud nejsou uvedené žádné služby, klikněte na tlačítko **Nový** (viz krok 9.)

7. Zkopírujte kód šablony pro do `MobileServiceClient` PCL. Umístění souboru není důležité, pokud je k dispozici pouze jedna instance.
  Doporučený postup je vytvořit `AzureService` třídu, která zpracovává všechny interakce Azure a používá `MobileServiceClient` :

    ![Kopírovat konfigurační kód do přístupového bodu](media/connected-services-image007.png "Kopírovat konfigurační kód do aplikace")

8. Podle dokumentace v části **Další kroky** přidejte data, offline synchronizaci, ověřování a nabízená oznámení do vaší aplikace:

    [![Projděte si pokyny k dalším krokům.](media/connected-services-image008-sml.png "Projděte si pokyny k dalším krokům.")](media/connected-services-image008.png#lightbox)

9. Pokud nemáte žádné existující služby App Services, můžete v rámci Visual Studio pro Mac vytvořit nové služby.
  Kliknutím na tlačítko **Nový** v levém dolním rohu seznamu služby otevřete dialogové okno **Nový App Service** :

    [![Vytvoření nové služby App Service v Visual Studio pro Mac](media/connected-services-image009-sml.png "Vytvoření nové služby App Service v Visual Studio pro Mac")](media/connected-services-image009.png#lightbox)

Nová služba vyžaduje následující parametry:

- **Název služby App Service** – jedinečný název nebo ID pro plán
- **Předplatné** – předplatné, které chcete použít pro platbu za službu
- **Skupina prostředků** – způsob nebo uspořádání všech prostředků Azure pro projekt. Možnost použít existující nebo vytvořit novou. Pokud je to vaše první služba Azure, vytvořte novou.
- **Plán služeb** – určuje umístění a náklady na všechny prostředky, které ho používají. Možnost použít existující nebo vytvořit novou. Pokud je to vaše první služba Azure, použijte výchozí jednu nebo vytvořte novou v bezplatné úrovni (F1).

Další informace najdete v [dokumentaci k mobilním aplikacím](/azure/app-service-mobile/) .

## <a name="see-also"></a>Viz také

- [Připojené služby (Visual Studio ve Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)