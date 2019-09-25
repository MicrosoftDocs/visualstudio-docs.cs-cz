---
title: Podpora launchSettings. JSON
description: Tento dokument popisuje podporu souboru launchSettings. JSON v Visual Studio pro Mac
author: sayedihashimi
ms.author: sayedha
ms.date: 09/18/2019
ms.assetid: a556f9d7-86a8-408e-aa54-392584845889
ms.openlocfilehash: e7de368dd26bf2724a7bc060dade46422817da1e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71213757"
---
# <a name="launchsettingsjson"></a>launchSettings. JSON

Při vývoji ASP.NET Core projektů můžete nakonfigurovat, jak má být projekt spuštěn ve scénářích vývoje, přizpůsobením obsahu `launchSettings.json` souboru. V Visual Studio pro Mac můžete tento soubor aktualizovat pomocí uživatelského rozhraní možností projektu nebo přímo úpravou `launchSettings.json` souboru. Tento soubor je stejný konfigurační soubor, který lze použít při spuštění sady Visual Studio ve Windows nebo z příkazového řádku pomocí `dotnet`příkazu. Tento soubor je uložený v projektu `Properties` ve složce.

Podrobnější informace můžete přejít na [použití více prostředí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments). V tomto dokumentu se dozvíte, jak tento soubor aktualizovat v Visual Studio pro Mac.

## <a name="updating-start-configuration-using-visual-studio-for-mac"></a>Aktualizace konfigurace zahájení pomocí Visual Studio pro Mac

Můžete přímo upravit `launchSettings.json` v Visual Studio pro Mac nebo můžete použít možnosti projektu pro jeho úpravu. Chcete-li se dostat k možnostem projektu, klikněte pravým tlačítkem myši na projekt a vyberte možnost možnosti. Podívejte se na obrázek níže.

![vybrané možnosti místní nabídky projektu](media/vsmac-ctx-proj-options.png)

Až se dostanete do tohoto dialogu, přejdete na Spustit > Konfigurace > výchozí.

![Spustit výchozí konfigurace](media/vsmac-run-config-default.png)

Tady můžete nakonfigurovat dvě věci.

 - Proměnné prostředí, které jsou nastaveny při spuštění
 - Počáteční adresa URL projektu

## <a name="configure-environment-variables"></a>Konfigurace proměnných prostředí

Pomocí mřížky můžete zadat hodnoty pro proměnné prostředí. Tyto proměnné prostředí se nastaví při spuštění aplikace v rámci Visual Studio pro Mac. Při vývoji ASP.NET Corech aplikací byste měli znát speciální `ASPNETCORE_ENVIRONMENT` proměnnou prostředí. Další informace najdete v tématu [použití více prostředí v ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/environments).


## <a name="configure-start-url"></a>Konfigurace počáteční adresy URL

Chcete-li nakonfigurovat adresu URL, na které bude aplikace spuštěna, použijte přechod na kartu ASP.NET Core.

![Počáteční adresa URL možností proj](media/vsmac-run-config-default-aspnetcore.png)

Tady můžete zadat adresy URL, na kterých bude aplikace při spuštění naslouchat.