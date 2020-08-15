---
title: Nastavení spuštění nástrojů kontejneru sady Visual Studio
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: de0e3cc4e563f7082b91b904a110996cdb85b3b4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2020
ms.locfileid: "88247978"
---
# <a name="container-tools-launch-settings"></a>Nastavení spuštění nástrojů kontejneru

Ve složce *Properties* v projektu ASP.NET Core můžete najít launchSettings.jsv souboru, který obsahuje nastavení, která určují, jak se vaše webová aplikace spouští ve vývojovém počítači. Podrobné informace o tom, jak se tento soubor používá při vývoji ASP.NET, najdete v tématu [použití více prostředí v ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). V *launchSettings.jsna*se nastavení v části **Docker** vztahují k způsobu, jakým aplikace Visual Studio zpracovává kontejnery aplikací.

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

Nastavení příkazového řádku označuje, že tato část se vztahuje na nástroje kontejneru. V následující tabulce jsou uvedeny vlastnosti, které lze nastavit v této části:

::: moniker range="vs-2017"

|Název nastavení|Verze|Příklad|Popis|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Označuje, zda se má po úspěšném spuštění projektu spustit prohlížeč.|
|launchUrl|Visual Studio 2017|"launchUrl": "{schéma}://{ServiceHost}: {ServicePort}"|Tato adresa URL se používá při spuštění prohlížeče.  Podporované náhradní tokeny pro tento řetězec jsou:<br>   {Schéma} – v závislosti na tom, jestli se používá SSL, nahradí buď http, nebo HTTPS.<br>   {ServiceHost} – obvykle se nahrazuje řetězcem "localhost". Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starší, nahradí se tím i IP adresou kontejneru.<br>   {ServicePort} – obvykle se nahrazuje buď sslPort nebo httpPort, v závislosti na tom, jestli se používá SSL.  Při cílení na kontejnery Windows ve Windows 10 RS3 nebo starší se ale v závislosti na tom, jestli se používá SSL, nahradí buď "443", nebo "80".|

::: moniker-end

::: moniker range=">=vs-2019"

| Název nastavení         | Příklad                                               | Popis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| CommandLineArgs –      | "CommandLineArgs –": "--mysetting hodnota"              | Tyto argumenty příkazového řádku pro spuštění vaší aplikace se použijí při spuštění projektu v kontejneru.                                     |
| environmentVariables | "environmentVariables": {                             | Tyto hodnoty proměnných prostředí jsou předány procesu při jeho spuštění v kontejneru.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Tento port na hostiteli je při spuštění kontejneru mapován na port 80 kontejneru.                                |
|                      |                                                       | Pokud tento parametr nezadáte, hodnota se převezme z hodnoty iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Označuje, zda se má po úspěšném spuštění projektu spustit prohlížeč.                                       |
| launchUrl            | "launchUrl": "{schéma}://{ServiceHost}: {ServicePort}" | Tato adresa URL se používá při spuštění prohlížeče. Podporované náhradní tokeny pro tento řetězec jsou:                          |
|                      |                                                       | -{Schéma} – v závislosti na tom, jestli se používá SSL, nahradí buď http, nebo HTTPS.                                   |
|                      |                                                       | – {ServiceHost} – obvykle se nahrazuje řetězcem "localhost".                                                                    |
|                      |                                                       | Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starší, nahradí se tím i IP adresou kontejneru.           |
|                      |                                                       | -{ServicePort} – obvykle se nahrazuje buď sslPort nebo httpPort, v závislosti na tom, jestli se používá SSL.                   |
|                      |                                                       | Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starším, je ale nahrazuje se buď "443", nebo "80".         |
|                      |                                                       | záleží na tom, jestli se používá protokol SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Tento port na hostiteli je při spuštění kontejneru mapován na port 443 kontejneru.                               |
|                      |                                                       | Pokud tento parametr nezadáte, hodnota se převezme z hodnoty iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Určuje, zda se má při spuštění projektu použít protokol SSL. Pokud useSSL není zadaný, použije se SSL, když sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Další kroky

Nakonfigurujte projekt nastavením [vlastností kontejnerových nástrojů](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také

[Docker Compose vlastnosti sestavení](docker-compose-properties.md)
