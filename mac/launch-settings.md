---
title: podpora pro launchSettings.json
description: Tento dokument popisuje podporu pro spuštěníSettings.json v Sadě Visual Studio pro Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: d35bfed901dca960ae21b4e2cf2fa75067c1b3ee
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "73715930"
---
# <a name="launchsettingsjson"></a>launchSettings.json

Při vývoji ASP.NET základní projekty, můžete nakonfigurovat, jak by měl být projekt spuštěn ve scénářích vývoje přizpůsobením obsahu souboru launchSettings.json. V sadě Visual Studio for Mac můžete tento soubor aktualizovat pomocí uj. Tento soubor je stejný konfigurační soubor, který můžete použít při `dotnet`spuštění sady Visual Studio v systému Windows nebo z příkazového řádku až po aplikaci . Tento soubor je uložen v projektu ve složce Vlastnosti.

Podrobnější informace najdete [v tématu Použití více prostředí v ASP.NET jádra](/aspnet/core/fundamentals/environments). V tomto článku se budeme zabývat tím, jak tento soubor aktualizovat ve Visual Studiu pro Mac.

## <a name="update-the-start-configuration-by-using-visual-studio-for-mac"></a>Aktualizace počáteční konfigurace pomocí Visual Studia pro Mac

Soubor launchSettings.json můžete přímo upravit v sadě Visual Studio for Mac nebo můžete upravit pomocí možností projektu. Chcete-li se dostat k možnostem projektu, klepněte pravým tlačítkem myši na projekt a vyberte **možnosti**.

![Místní nabídka projektu s vybranou možností Možnosti](media/vsmac-ctx-proj-options.png)

Vyberte **možnost Spustit** > **výchozí konfigurace** > **.**

!["Spustit", "Konfigurace" a "Výchozí" v možnostech projektu](media/vsmac-run-config-default.png)

V první řadě zde nakonfigurujete dvě věci:

 - Proměnné prostředí
 - Adresa URL aplikace pro projekt

## <a name="configure-environment-variables"></a>Konfigurace proměnných prostředí

Mřížku můžete použít k určení hodnot pro proměnné prostředí. Tyto proměnné prostředí se nastaví při spuštění aplikace v sadě Visual Studio for Mac. Při vývoji ASP.NET základní aplikace, měli byste `ASPNETCORE_ENVIRONMENT` si být vědomi proměnné speciální prostředí. Další informace najdete [v tématu Použití více prostředí v ASP.NET jádra](/aspnet/core/fundamentals/environments).


## <a name="configure-the-start-url"></a>Konfigurace počáteční adresy URL

Chcete-li nakonfigurovat adresu URL, se kterou bude aplikace spuštěna, přejděte na kartu **ASP.NET jádro.**

![Adresa URL aplikace v možnostech projektu](media/vsmac-run-config-default-aspnetcore.png)

Zde můžete zadat adresu URL, kterou bude aplikace poslouchat při spuštění.