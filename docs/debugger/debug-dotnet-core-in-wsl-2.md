---
title: Ladění aplikací .NET Core v WSL 2
description: Naučte se spouštět a ladit aplikace .NET Core v WSL 2, aniž byste opustili aplikaci Visual Studio.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227647"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Ladění aplikací .NET Core v WSL 2 se sadou Visual Studio

Aplikace .NET Core můžete snadno spouštět a ladit v systému Linux, aniž by bylo nutné opustit aplikaci Visual Studio pomocí WSL 2. Pokud jste vývojář pro různé platformy, můžete tuto metodu použít jako jednoduchý způsob testování více cílových prostředí.

Pro uživatele Windows .NET, který cílí na Linux, WSL 2 žije na sladkém místě mezi výrobou a produktivitou v produkčním prostředí. V aplikaci Visual Studio můžete již ladit vzdálené prostředí Linux pomocí [vzdáleného ladicího programu](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)nebo s kontejnery pomocí [nástrojů kontejnerů](../containers/overview.md). Když je provozní realitou hlavní záležitost, měli byste použít jednu z těchto možností. Když je snadná a rychlá vnitřní smyčka důležitější, je WSL 2 skvělou možností.

Nemusíte volit jenom jednu metodu! Můžete mít spouštěcí profil pro Docker a WSL 2 ve stejném projektu a vybrat, podle toho, co je vhodné pro konkrétní běh. A když je vaše aplikace nasazená, můžete se k ní kdykoli připojit pomocí vzdáleného ladicího programu, pokud dojde k nějakému problému.

## <a name="prerequisites"></a>Požadavky

- Visual Studio 2019 v 16.9 Preview 1 nebo novější verze s volitelnou komponentou .NET Core s laděním WSL 2.

  Volitelná součást je standardně součástí sady .NET Core pro různé platformy nebo úlohy vývoje ASP.NET a webu. Je nutné nainstalovat jednu nebo obě z těchto úloh.

- Nainstalujte [WSL 2](/windows/wsl/about).

- Nainstalujte [distribuci](https://aka.ms/wslstore) podle svého výběru.

## <a name="start-debugging-with-wsl-2"></a>Spuštění ladění pomocí WSL 2

1. Po instalaci požadovaných součástí otevřete ASP.NET Core webové aplikace nebo konzolovou aplikaci .NET Core v aplikaci Visual Studio uvidíte nový profil spuštění s názvem WSL 2:

   ![WSL 2 – profil spuštění v seznamu profil spuštění](media/linux-wsl2-debugging-select-launch-profile.png)

1. Vyberte tento profil a přidejte ho do svého *launchSettings.jsv*.

   V následujícím příkladu jsou uvedeny některé z klíčových atributů v souboru.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Jakmile vyberete nový profil, rozšíření zkontroluje, jestli je vaše distribuce WSL 2 nakonfigurovaná tak, aby spouštěla aplikace .NET Core, a pomůže vám nainstalovat chybějící závislosti. Po instalaci těchto závislostí jste připraveni k ladění v WSL 2.

1. Spusťte ladění jako normální a vaše aplikace se spustí ve výchozí distribuci WSL 2.

   Snadný způsob, jak ověřit, že používáte v systému Linux, je zkontrolovat hodnotu `Environment.OSVersion` .

>[!NOTE]
> Testovány jsou jenom Ubuntu a Debian a podporují se. Jiná distribuce podporovaná rozhraním .NET Core by měla fungovat, ale vyžadují ruční instalaci [modulu runtime .NET Core](https://aka.ms/wsldotnet) a [kudrlinkou](https://curl.haxx.se/).

## <a name="choose-a-specific-distribution"></a>Zvolit konkrétní distribuci

Ve výchozím nastavení používá spouštěcí profil WSL 2 výchozí distribuci nastavenou v *wsl.exe*. Pokud chcete, aby váš profil pro spuštění cílí na konkrétní distribuci, můžete upravit svůj spouštěcí profil bez ohledu na jeho výchozí nastavení. Pokud například ladíte webovou aplikaci a chcete ji otestovat v Ubuntu 20,04, váš profil spuštění by vypadal takto:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Cílová vícenásobná distribuce

Pokud pracujete na aplikaci, která potřebuje běžet v několika distribucích a chcete rychle testovat každý z nich, můžete mít několik spouštěcích profilů. Například pokud potřebujete otestovat konzolovou aplikaci na Debian, Ubuntu 18,04 a Ubuntu 20,04, můžete použít následující spouštěcí profily:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Pomocí těchto profilů spuštění můžete snadno přepínat mezi vašimi cílovými distribucí, aniž byste opustili pohodlí sady Visual Studio.

![Několik profilů spuštění WSL 2 v seznamu profil spuštění](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Nastavení WSL v profilu spuštění

V následující tabulce jsou uvedena nastavení podporovaná v profilu spuštění.

|Name|Výchozí|Účel|Podporuje tokeny?|
|-|-|-|-|
|executablePath|dotnet|Spustitelný soubor, který se má spustit|Ano|
|CommandLineArgs –|Hodnota TargetPath vlastnosti sady MSBuild mapovaná na prostředí WSL|Argumenty příkazového řádku předané do executablePath|Ano|
|workingDirectory|Pro konzolové aplikace: {*OutDir*}</br>Pro Web Apps: {*ProjectDir*}|Pracovní adresář, ve kterém se má spustit ladění|Ano|
|environmentVariables||Páry klíč-hodnota proměnných prostředí, které se mají nastavit pro laděný proces.|Ano|
|setupScriptPath||Skript, který se má spustit před laděním Užitečné ke spouštění skriptů jako ~/.bash_profile.|Ano|
|distribuční.||Název distribuce WSL, která se má použít|Ne|
|launchBrowser|false (nepravda)|Bez ohledu na to, jestli se má spustit prohlížeč|Ne|
|launchUrl||Adresa URL, která se má spustit, pokud má launchBrowser hodnotu true|Ne|

Podporované tokeny:

{*ProjectDir*} – cesta k adresáři projektu

{*OutDir*} – hodnota vlastnosti MSBuild `OutDir`

>[!NOTE]
> Všechny cesty jsou pro WSL, ne pro Windows.
