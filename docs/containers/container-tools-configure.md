---
title: Konfigurace nástrojů kontejneru sady Visual Studio
description: Nakonfigurujte nástroje dostupné v Sadě Visual Studio pro práci s kontejnery Dockeru.
author: ghogen
ms.author: ghogen
ms.topic: conceptual
ms.date: 03/20/2019
ms.technology: vs-azure
ms.openlocfilehash: 0ae81ed19a7fa8a967a3f9c3fe83c9f0d9e3ae51
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73188770"
---
# <a name="how-to-configure-visual-studio-container-tools"></a>Konfigurace nástrojů kontejneru sady Visual Studio

Pomocí nastavení Visual Studia můžete řídit některé aspekty fungování Visual Studia s kontejnery Dockeru, včetně nastavení, která ovlivňují výkon a využití prostředků při práci s kontejnery Dockeru.

## <a name="container-tools-settings"></a>Nastavení nástrojů kontejneru

V hlavní nabídce zvolte **Nástroje > Možnosti**a **rozbalte položku Nástroje kontejneru > Nastavení**. Zobrazí se nastavení nástrojů kontejneru.

::: moniker range="vs-2017"

![Možnosti nástroje kontejneru visual studia, zobrazené: Automaticky vytahovat požadované image Dockeru při načtení projektu, Automaticky spustit kontejnery na pozadí, Automaticky zabít kontejnery při zavření řešení a Nezobrazovat výzvu k důvěřování certifikátu SSL.](./media/overview/visual-studio-docker-tools-options.png)
::: moniker-end

::: moniker range=">=vs-2019"

Nástroje kontejneru **Obecné** nastavení:

![Možnosti nástrojů kontejneru sady Visual Studio, které ukazují: V případě potřeby nainstalujte desktop Docker desktop a důvěřujte ASP.NET certifikátu SSL jádra.](./media/configure-container-tools/tools-options-1.png)

Kontejner nástroje **jeden projekt** a **Docker compose** nastavení:

![Možnosti nástroje kontejnerů visual studia, zobrazené: Ustupte kontejnery na zavření projektu, Pull požadované image Dockeru na projektu otevřít a spustit kontejnery na projektu otevřít.](./media/configure-container-tools/tools-options-2.png)
::: moniker-end

Následující tabulka vám může pomoci při rozhodování o nastavení těchto možností.

::: moniker range="vs-2017"
| Name (Název) | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Automatické vytahování požadovaných ibi Dockeru při zatížení projektu | Zapnuto | Docker Compose | Pro zvýšení výkonu při načítání projektů, Visual Studio spustí operace vyžádat Docker na pozadí tak, že když jste připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud právě načítáte projekty a procházíte kód, můžete to vypnout, abyste se vyhnuli stahování obrázků kontejnerů, které nepotřebujete. |
| Automatické spouštění kontejnerů na pozadí | Zapnuto | Docker Compose | Znovu pro zvýšení výkonu Visual Studio vytvoří kontejner s připojením svazku připravené pro při vytváření a spuštění kontejneru. Pokud chcete řídit, kdy je váš kontejner vytvořen, vypněte toto. |
| Automaticky zabít kontejnery na řešení zavřít | Zapnuto | Docker Compose | Vypněte tuto otázku, pokud chcete, aby kontejnery pro vaše řešení nadále spouštěly po zavření řešení nebo zavření sady Visual Studio. |
| Nezobrazovat výzvu k důvěřování certifikátu Localhost SSL | Vypnuto | ASP.NET Projekty Core 2.1 | Pokud certifikát Localhost SSL není důvěryhodný, Visual Studio zobrazí výzvu při každém spuštění projektu, pokud toto políčko není zaškrtnuto. |
::: moniker-end

::: moniker range=">=vs-2019"

V následující tabulce jsou popsána **obecná** nastavení:

| Name (Název) | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| V případě potřeby nainstalujte desktop Dockeru | Vyzvat mě | Jeden projekt, Docker Compose | Zvolte, jestli chcete být vyzváni, pokud není nainstalována aplikace Docker Desktop. |
| Důvěřovat ASP.NET základní certifikát SSL | Vyzvat mě | ASP.NET projekty Core 2.x | Pokud je nastavena **možnost Zobrazit ,** pokud není certifikát Localhost SSL důvěryhodný, zobrazí visual studio při každém spuštění projektu výzvu. |

Následující tabulka popisuje nastavení **jednoduchého projektu** a **dockerového komponování:**

| Name (Název) | Výchozí nastavení | Platí pro | Popis |
| -----|:---------------:|:----------:| ----------- |
| Vyžádat požadované image Dockeru při otevření projektu | True | Jeden projekt, Docker Compose | Pro zvýšení výkonu při načítání projektů, Visual Studio spustí operace vyžádat Docker na pozadí tak, že když jste připraveni ke spuštění kódu, image je již stažena nebo v procesu stahování. Pokud právě načítáte projekty a procházíte kód, můžete nastavit hodnotu **False,** abyste se vyhnuli stahování iobrazů kontejnerů, které nepotřebujete. |
| Spustit kontejnery při otevření projektu | True | Jeden projekt, Docker Compose | Znovu pro zvýšení výkonu Visual Studio vytvoří kontejner předem tak, aby je připraven pro při vytváření a spuštění kontejneru. Pokud chcete řídit, kdy je kontejner vytvořen, nastavte hodnotu **False**. |
| Zastavit kontejnery při zavření projektu | True | Jeden projekt a Docker Compose | Nastavte na **false,** pokud chcete kontejnery pro vaše řešení pokračovat v běhu po zavření řešení nebo zavření sady Visual Studio. |

::: moniker-end
> [!WARNING]
> Pokud certifikát Localhost SSL není důvěryhodný a zaškrtnete políčko potlačit výzvy, pak https webové požadavky může selhat za běhu ve vaší aplikaci nebo službě. V takovém případě zaškrtněte políčko **Nezobrazovat výzvu,** spusťte projekt a na výzvu uveďte důvěryhodnost.

## <a name="next-steps"></a>Další kroky

Další informace o práci s kontejnery v sadě Visual Studio najdete v tomto [přehledu](overview.md).