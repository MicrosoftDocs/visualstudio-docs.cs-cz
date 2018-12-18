---
title: Připojené služby
description: Přidání úložiště dat Azure, ověřování a nabízená oznámení do mobilní aplikace ze sady Visual Studio pro Mac
ms.assetid: 41CB62FF-0F39-4CE8-8917-6A77F058719F
author: conceptdev
ms.author: crdun
ms.date: 11/06/2018
ms.openlocfilehash: ada47aa3d0cb0d9917404efc2775b843223c6e86
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948943"
---
# <a name="connected-services-walkthrough"></a>Názorný postup připojené služby

Připojené služby pracovního postupu přináší pracovními postupy Azure portal do sady Visual Studio pro Mac, takže není nutné opustit váš projekt na přidání služeb.

Tento návod ukazuje, jak přidat službu back-endu Azure, která přináší datové úložiště v cloudu, ověřování a odesílání nabízených oznámení do aplikace Xamarin.Forms Přenosná knihovna tříd (PCL) napříč platformami.

1. Začněte tím, že poklikáte na **připojené služby** uzlu v řešení, kterým se zobrazí **Galerie služby**.
  Toto je seznam všech dostupných služeb pro typ aplikace. Vyberte službu (například **mobilní back-end pomocí služby Azure App Service**) kliknutím na ni.

    [![Uzel připojených služeb v sadě Visual Studio pro Mac](media/connected-services-image001-sml.png "uzel připojené služby v sadě Visual Studio pro Mac")](media/connected-services-image001.png#lightbox)

2. Stránka Podrobnosti služby obsahuje popis služeb a závislosti a nainstalovat.
  Klikněte na tlačítko **přidat** tlačítko pro přidání závislosti na aplikaci:

    [![Mobilní back-end s využitím Azure](media/connected-services-image002-sml.png "mobilní back-end s využitím Azure")](media/connected-services-image002.png#lightbox)

3. Závislostí je potřeba přidat PCL a specifické pro platformu projekty pracovat.
  Vyberte zaškrtávací políčka pro přidání služby do jakéhokoliv projektu, který bude na něj odkazovat (přímo nebo nepřímo):

    [![Zkontrolujte všechny projekty, které by měly odkazovat službu](media/connected-services-image003-sml.png "zkontrolovat všechny projekty, které by měly odkazovat služby")](media/connected-services-image003.png#lightbox)

4. Zvolte **přijmout** na **přijetí licence** dialogová okna pro balíčky NuGet.
  Můžou existovat dva dialogová okna tak, aby přijímal, jeden MobileClient a závislosti a druhý pro SQLiteStore, které jsou požadovány pro synchronizaci dat offline:

    [![Přijměte licenční smlouvy](media/connected-services-image004-sml.png "přijetí licenční smlouvy")](media/connected-services-image004.png#lightbox)

    ![Okno přijetí licence](media/connected-services-image005.png "okno přijetí licence")

5. Po přidání jsou závislosti, budete vyzváni k přihlášení pomocí účtu, který chcete použít ke komunikaci s Azure.
  Pokud již jste přihlášeni pomocí účtu Microsoft ID, Visual Studio pro Mac se pokusí načíst vaše předplatná Azure a všechny aplikace služby k nim má přiřazené. Pokud nemáte žádné předplatné, můžete přidat pomocí registrace bezplatné zkušební verze nebo zakoupení plánu předplatného na webu Azure Portal.

6. Vyberte ze seznamu služby app service. Tato hodnota se vyplní kód šablony pro `MobileServiceClient` objekt s odpovídající adresy URL služby app Service v Azure:

    [![Vyberte službu app service ze seznamu](media/connected-services-image006-sml.png "vyberte ze seznamu službu app service")](media/connected-services-image006.png#lightbox)

    Pokud nejsou žádné služby uvedené, klikněte na tlačítko **nový** tlačítko (viz krok 9.)

7. Zkopírujte kód šablony pro `MobileServiceClient` do PCL. Umístění souboru není důležité, tak dlouho, dokud existuje pouze jedna instance.
  Doporučený postup je vytvořit `AzureService` třídu, která zpracovává všechny Azure interakce a používá `MobileServiceClient`:

    ![Zkopírujte do přístupový bod konfigurace kód](media/connected-services-image007.png "zkopírujte config kód do aplikace")

8. Postupujte podle dokumentace v **další kroky** k přidání offline synchronizace dat, ověřování a nabízená oznámení do vaší aplikace:

    [![Projít další kroky pokyny](media/connected-services-image008-sml.png "projít pokyny pro další kroky")](media/connected-services-image008.png#lightbox)

9. Pokud nemáte žádné existující aplikační služby, můžete vytvořit nové služby od sady Visual Studio pro Mac.
  Klikněte na tlačítko **nový** tlačítko v levé dolní části seznamu služeb otevřete **novou službu App Service** dialogové okno:

    [![Vytvořit novou službu app service v sadě Visual Studio pro Mac](media/connected-services-image009-sml.png "vytvořit novou službu app service v sadě Visual Studio pro Mac")](media/connected-services-image009.png#lightbox)

Nová služba vyžaduje následující parametry:

-   **Název služby App service** – jedinečný název nebo id plánu.
-   **Předplatné** – předplatné chcete použít k platbám za službu
-   **Skupina prostředků** – způsob, jak nebo uspořádání všech vašich prostředků Azure pro projekt. Možnost použít existující nebo vytvořte novou. Pokud je toto první služby Azure, vytvořte novou.
-   **Plánování služby** – Určuje umístění a náklady na všechny prostředky, které ji používají. Možnost použít existující nebo vytvořte novou. Pokud je toto první služby Azure, použijte výchozí hodnotu nebo vytvořte novou úroveň free (F1).

Přejděte [dokumentace k Mobile apps](/azure/app-service-mobile/) Další informace.

## <a name="see-also"></a>Viz také:

- [Připojené služby (Visual Studio na Windows)](/visualstudio/azure/vs-azure-tools-connected-services-storage)