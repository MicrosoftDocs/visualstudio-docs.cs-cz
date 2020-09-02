---
title: Konfigurace nástrojů pro kontejner sady Visual Studio
description: Nakonfigurujte nástroje dostupné v aplikaci Visual Studio pro práci s kontejnery Docker.
author: ghogen
ms.author: ghogen
ms.topic: how-to
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: d2b3e2821e7697ad53b10a7148c22140aa1a07af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283213"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Jak konfigurovat nástroje kontejneru sady Visual Studio

Pomocí nastavení aplikace Visual Studio můžete řídit některé aspekty fungování sady Visual Studio s kontejnery Docker, včetně nastavení, která mají vliv na výkon a využití prostředků při práci s kontejnery Docker.

## <a name="container-tools-settings"></a>Nastavení nástrojů kontejneru

V hlavní nabídce vyberte **nástroje > možnosti**a rozbalte položku **nástroje kontejneru > nastavení**. Zobrazí se nastavení nástroje kontejneru.

::: moniker range="vs-2017"

![Možnosti nástrojů kontejnerů sady Visual Studio, které ukazují: automatické vyžádání požadovaných imagí Docker při načtení projektu, automatické spuštění kontejnerů na pozadí, automatické ukončení kontejnerů při zavření řešení a nedotazování na důvěryhodný certifikát SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

**Obecné** nastavení nástrojů kontejneru:

![Možnosti nástrojů kontejnerů sady Visual Studio, zobrazení: instalace Docker desktopu v případě potřeby a důvěryhodnost ASP.NET Core certifikát SSL.](./media/configure-container-tools/tools-options-1.png)

Nastavení **jednoho projektu** a **Docker Compose** v nástrojích kontejnerů:

![Možnosti nástrojů kontejnerů sady Visual Studio, zobrazení: deaktivační kontejnery při zavření projektu, vyžádané obrázky Docker v otevřeném projektu a spuštění kontejnerů v otevřeném projektu.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Následující tabulka vám může pomáhat při rozhodování, jak tyto možnosti nastavit.

::: moniker range="vs-2017"
| Název | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Při načtení projektu automaticky stáhnout požadované image Docker | Zapnout | Docker Compose | Pro zvýšení výkonu při načítání projektů aplikace Visual Studio spustí operaci získání dat Docker na pozadí, takže až budete připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud načítáte pouze projekty a kód procházení, můžete tuto možnost vypnout, aby nedocházelo ke stahování imagí kontejneru, které nepotřebujete. |
| Automatické spouštění kontejnerů na pozadí | Zapnout | Docker Compose | Pro zvýšení výkonu Visual Studio vytvoří kontejner s připojenými svazky, který je připravený pro sestavení a spuštění kontejneru. Pokud chcete určit, kdy se kontejner vytvoří, vypněte ho. |
| Automaticky odstranit kontejnery v blízkosti řešení | Zapnout | Docker Compose | Tuto funkci zapněte, pokud chcete, aby kontejnery pro vaše řešení nadále běžely po zavření řešení nebo ukončení sady Visual Studio. |
| Nedotazovat se na důvěřování certifikátům SSL místního hostitele | Vypnuto | Projekty ASP.NET Core 2,1 | Pokud se nejedná o důvěryhodný certifikát SSL pro localhost, Visual Studio se zobrazí dotaz při každém spuštění projektu, pokud není zaškrtnuto toto políčko. |
::: moniker-end

::: moniker range=">=vs-2019"

Následující tabulka popisuje **Obecná** nastavení:

| Název | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| V případě potřeby nainstalovat Docker Desktop | Zobrazit výzvu | Jeden projekt, Docker Compose | Vyberte, jestli se má zobrazit výzva, pokud není nainstalovaný Docker Desktop. |
| Důvěryhodný ASP.NET Core certifikát SSL | Zobrazit výzvu | ASP.NET Core 2. x projekty | Když se nastaví **výzva k zadání výzvy**, pokud není důvěryhodný certifikát SSL pro localhost, Visual Studio se zobrazí dotazování při každém spuštění projektu. |

Následující tabulka popisuje nastavení **jednoho projektu** a **Docker Compose** :

| Název | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Při otevření projektu vyžadovat vyžádání imagí Docker | Ano | Jeden projekt, Docker Compose | Pro zvýšení výkonu při načítání projektů aplikace Visual Studio spustí operaci získání dat Docker na pozadí, takže až budete připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud načítáte pouze projekty a kód procházení, můžete nastavit na **hodnotu false** , aby nedocházelo ke stahování imagí kontejneru, které nepotřebujete. |
| Spustit kontejnery v otevřeném projektu | Ano | Jeden projekt, Docker Compose | Pro zvýšení výkonu Visual Studio vytvoří kontejner předem, aby byl připravený pro sestavení a spuštění kontejneru. Pokud chcete řídit, kdy se kontejner vytvoří, nastavte **hodnotu false**. |
| Zastavit kontejnery při zavření projektu | Ano | Jeden projekt a Docker Compose | Nastavte na **hodnotu false** , pokud chcete, aby kontejnery pro vaše řešení pokračovaly v běhu i po zavření řešení nebo ukončení sady Visual Studio. |

::: moniker-end
> [!WARNING]
> Pokud certifikát localhost místního hostitele není důvěryhodný a zaškrtnete políčko pro potlačení výzvy, můžou webové požadavky HTTPS v době spuštění vaší aplikace nebo služby selhat. V takovém případě zrušte zaškrtnutí políčka **nedotazovat** se na výzvu, spusťte projekt a na příkazovém řádku uveďte vztah důvěryhodnosti.

## <a name="next-steps"></a>Další kroky

Další informace o práci s kontejnery v aplikaci Visual Studio najdete v tomto [přehledu](overview.md).