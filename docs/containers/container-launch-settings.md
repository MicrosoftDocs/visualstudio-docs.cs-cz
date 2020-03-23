---
title: Nastavení spuštění nástrojů pro kontejnery sady Visual Studio
author: ghogen
description: Přehled procesu sestavení kontejnerových nástrojů
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1c9786c29573da3b0149a9ec6578f2ce58c4de9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542591"
---
# <a name="container-tools-launch-settings"></a>Nastavení spuštění nástrojů kontejneru

Ve složce *Vlastnosti* v projektu ASP.NET Core najdete soubor launchSettings.json, který obsahuje nastavení, která řídí způsob spuštění webové aplikace ve vývojovém počítači. Podrobné informace o tom, jak se tento soubor používá při vývoji ASP.NET, naleznete [v tématu Použití více prostředí v ASP.NET core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). Při *spuštěníSettings.json*nastavení v části **Docker** souvisí s tím, jak Visual Studio zpracovává kontejnerizované aplikace.

::: moniker range="vs-2017"
```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

Nastavení commandName určuje, že se tato část vztahuje na nástroje kontejneru. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit v této části:

::: moniker range="vs-2017"

|Název nastavení|Version|Příklad|Popis|
|------------|-------|-------|---------------|
|spuštěníProhlížeč|Visual Studio 2017|"launchBrowser": true|Označuje, zda se má spustit prohlížeč po úspěšném spuštění projektu.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Tato adresa URL se používá při spouštění prohlížeče.  Podporované náhradní tokeny pro tento řetězec jsou:<br>   {Scheme} - Nahrazeno buď "http" nebo "https" v závislosti na tom, zda je použit protokol SSL.<br>   {ServiceHost} - Obvykle nahrazen "localhost". Při cílení kontejnerů systému Windows v systému Windows 10 RS3 nebo starší, i když je nahrazen a IP kontejneru.<br>   {ServicePort} - Obvykle nahrazen buď sslPort nebo httpPort, v závislosti na tom, zda je použit SSL.  Při cílení kontejnerů systému Windows v systému Windows 10 RS3 nebo starší, i když je nahrazen buď "443" nebo "80", v závislosti na tom, zda se používá SSL.|

::: moniker-end

::: moniker range=">=vs-2019"

| Název nastavení         | Příklad                                               | Popis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| příkazLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Tyto argumenty příkazového řádku se používají při spouštění projektu v kontejneru.                                     |
| environmentVariables | "proměnné prostředí": {                             | Tyto hodnoty proměnných prostředí jsou předány procesu při spuštění v kontejneru.                       |
|                      | "ASPNETCORE_URLS":https://+:443" ; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Tento port na hostiteli je mapován na port kontejneru 80 při spouštění kontejneru.                                |
|                      |                                                       | Pokud není zadán, hodnota je převzata z hodnoty iisSettings.                                                          |
| spuštěníProhlížeč        | "launchBrowser": true                                 | Označuje, zda se má spustit prohlížeč po úspěšném spuštění projektu.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Tato adresa URL se používá při spouštění prohlížeče. Podporované náhradní tokeny pro tento řetězec jsou:                          |
|                      |                                                       | - {Scheme} - Nahrazeno buď "http" nebo "https" v závislosti na tom, zda se používá SSL.                                   |
|                      |                                                       | - {ServiceHost} - Obvykle nahrazen "localhost".                                                                    |
|                      |                                                       | Při cílení kontejnerů systému Windows v systému Windows 10 RS3 nebo starší, i když je nahrazen a IP kontejneru.           |
|                      |                                                       | - {ServicePort} - Obvykle nahrazen buď sslPort nebo httpPort, v závislosti na tom, zda je použit SSL.                   |
|                      |                                                       | Při cílení kontejnerů systému Windows v systému Windows 10 RS3 nebo starší, je však nahrazen buď "443" nebo "80",         |
|                      |                                                       | v závislosti na tom, zda se používá SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Tento port na hostiteli je mapován na port kontejneru 443 při spuštění kontejneru.                               |
|                      |                                                       | Pokud není zadán, hodnota je převzata z hodnoty iisSettings.                                                          |
| použitíSSL               | "useSSL": true                                        | Označuje, zda se má při spouštění projektu použít ssl. Pokud useSSL není zadán, pak SSL se používá při sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Další kroky

Nakonfigurujte projekt nastavením [vlastností sestavení Nástroje kontejneru](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Vlastnosti sestavení dockeru](docker-compose-properties.md)
