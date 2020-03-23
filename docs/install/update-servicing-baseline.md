---
title: Aktualizace sady Visual Studio v servisním směrném plánu
description: Přečtěte si, jak aktualizovat visual studio při zachování směrného plánu obsluhy.
ms.date: 07/17/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9f31a3f7ae5e0e0ca4150d88870b9e48493bffcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114956"
---
# <a name="update-visual-studio-while-on-a-servicing-baseline"></a>Aktualizace sady Visual Studio v servisním směrném plánu

Visual Studio aktualizujeme často během životního cyklu produktu. Existují dva typy aktualizací: 

* **Menší aktualizace**&mdash;vydání například 16.0 až&mdash;16.1, které obsahují nové funkce a součásti.  
* **Aktualizace obsluhy**– například 16.0.4 až 16.0.5 – které obsahují pouze cílené opravy kritických problémů.

Správci rozlehlé sítě se mohou rozhodnout, že budou mít své klienty na směrné úrovni obsluhy. Směrný plán obsluhy je podporován aktualizacemi obsluhy po dobu jednoho roku po vydání dalšího směrného plánu obsluhy.

Možnost směrného plánu obsluhy poskytuje vývojářům a správcům větší flexibilitu při přijímání nových funkcí, oprav chyb nebo součástí zahrnutých do nových dílčích aktualizací. První směrný plán obsluhy je 16.0.x. Další informace naleznete v [tématu Možnosti podpory pro podnikové a profesionální zákazníky](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers).

## <a name="how-to-get-onto-a-servicing-baseline"></a>Jak se dostat k směrnému plánu obsluhy

Chcete-li začít používat směrný plán údržby, stáhněte si instalační nástroj sady Visual Studio s pevnou verzí z [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0). Zaváděcí nástroje mají odkazy na konfigurace produktu, úlohy a součásti pro danou konkrétní verzi.

> [!NOTE]
> Dávejte pozor, abyste rozlišovali mezi zaváděcím nástrojem s pevnou verzí a standardními zaváděcími nástrojami. Standardní zaváděcí nástroje jsou nakonfigurovány tak, aby používaly nejnovější dostupnou verzi sady Visual Studio. Standardní nástroje boostrappers mají číslo v názvu souboru (například vs_enterprise__123456789-123456789.exe), když jsou staženy z My.VisualStudio.com.

Během instalace musí správci rozlehlé sítě nakonfigurovat své klienty, aby zabránili aktualizaci klientů na nejnovější verzi. Existuje několik způsobů, jak to provést:
- [Změňte `channelUri` nastavení v konfiguračním souboru odpovědí](update-servicing-baseline.md#install-a-servicing-baseline-on-a-network) tak, aby používalmanifest kanálu v rozložení nebo místní složce.
- [Upravte channelUri prostřednictvím spuštění příkazového řádku](update-servicing-baseline.md#install-a-servicing-baseline-via-the-internet) použít neexistující soubor.
- [Nastavte v klientském systému zásady pro zakázání aktualizací](update-servicing-baseline.md#use-policy-settings-to-disable-clients-from-updating), abyste zabránili klientům v samoaktualizaci.

### <a name="install-a-servicing-baseline-on-a-network"></a>Instalace směrného plánu obsluhy v síti

Správci, kteří používají instalaci rozložení `channelUri` sítě, by měli upravit hodnotu v souboru *response.json* v rozvržení tak, aby používala soubor *channelmanifest.json,* který je ve stejné složce. Postup, který je třeba provést, naleznete v [tématu Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md). Změna `channelUri` hodnoty umožňuje klientům vyhledat aktualizace v umístění rozložení.

### <a name="install-a-servicing-baseline-via-the-internet"></a>Instalace směrného plánu údržby přes internet

Pro internetovou instalaci přidejte `--channelUri` s neexistujícím manifestem kanálu do příkazového řádku použitého ke spuštění instalačního příkazu. Tím zakážete visual studio používat nejnovější dostupnou verzi pro aktualizaci. Tady je příklad:

```cmd
vs_enterprise.exe --channelUri c:\doesnotexist.chman
```

### <a name="use-policy-settings-to-disable-clients-from-updating"></a>Zakázání aktualizací klientů pomocí nastavení zásad

Další možností pro řízení aktualizací na klientovi je [vypnutí oznámení o aktualizaci](controlling-updates-to-visual-studio-deployments.md). Tuto možnost použijte, pokud se při instalaci nezměnila hodnota channelUri. Zakáže klientovi přijímat odkazy na nejnovější dostupnou verzi. Zaváděcí nástroj s pevnou verzí je stále nutné aktualizovat na konkrétní verzi v klientovi.

## <a name="how-to-stay-on-a-servicing-baseline"></a>Jak zůstat na servisním směrnému plánu

Pokud je k dispozici aktualizace pro směrný plán údržby, jsou soubory zaváděcího nástroje s pevnou verzí k dispozici pro aktualizaci údržby v [My.VisualStudio.com](https://my.visualstudio.com/Downloads?q=visual%20studio%202019%20version%2016.0).

Pro správce, kteří nasazují pomocí instalace rozložení sítě, by měl správce aktualizovat [umístění rozložení](update-a-network-installation-of-visual-studio.md). Klienti, kteří jsou nainstalováni z umístění, obdrží oznámení o aktualizaci. Pokud aktualizace musí být nasazena pro klienty, postupujte [podle těchto pokynů](update-a-network-installation-of-visual-studio.md#deploy-an-update-to-client-machines). Při úpravě 'response.json' pro aktualizaci, nepřidávejte další úlohy, součásti nebo jazyky. Správa těchto nastavení musí být provedena jako "upravit" nasazení po produktu byla aktualizována.

Pro internetovou instalaci spusťte zaváděcí `--channelUri` nástroj nové pevné verze s parametrem směřujícím na neexistující manifest kanálu v klientovi. Pokud je aktualizace nasazena v tichém nebo pasivním režimu, použijte dva samostatné příkazy:

1. Aktualizujte instalační program sady Visual Studio:

    ```cmd
    vs_enterprise.exe --quiet --update
    ```

2. Aktualizujte samotnou aplikaci Visual Studio:

    ```cmd
    vs_enterprise.exe update --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" --quiet --wait --norestart --channelUri c:\doesnotexist.chman
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Jak definovat nastavení v souboru odpovědí](automated-installation-with-response-file.md)
* [Řízení aktualizací nasazení sady Visual Studio v síti](controlling-updates-to-visual-studio-deployments.md)
* [Životní cyklus produktu Visual Studio a servis](/visualstudio/releases/2019/servicing/)
