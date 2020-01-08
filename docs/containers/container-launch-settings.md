---
title: Nastavení spuštění nástrojů kontejneru sady Visual Studio
author: ghogen
description: Přehled procesu sestavení nástrojů kontejneru
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: b8c732fb847e4d9944e0d6a5405a29e7879cbdc9
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75400867"
---
# <a name="container-tools-launch-settings"></a>Nastavení spuštění nástrojů kontejneru

Ve složce *Properties* v ASP.NET Core projektu můžete najít soubor launchSettings. JSON, který obsahuje nastavení, která určují, jak se vaše webová aplikace spouští ve vývojovém počítači. Podrobné informace o tom, jak se tento soubor používá při vývoji ASP.NET, najdete v tématu [použití více prostředí v ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2). V *launchSettings. JSON*se nastavení v části **Docker** vztahují k způsobu, jakým aplikace Visual Studio zpracovává kontejnery aplikací.

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

|Název nastavení|Version|Příklad|Popis|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Označuje, zda se má po úspěšném spuštění projektu spustit prohlížeč.|
|launchUrl|Visual Studio 2017|"launchUrl": "schéma\<>://\<serviceHost >:\<servicePort >"|Tato adresa URL se používá při spuštění prohlížeče.  Podporované náhradní tokeny pro tento řetězec jsou:<br>   > schématu \<– v závislosti na tom, jestli se používá SSL, nahradí buď http nebo HTTPS.<br>   \<serviceHost > – obvykle nahrazuje "localhost". Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starší, nahradí se tím i IP adresou kontejneru.<br>   \<servicePort > – obvykle nahrazuje buď sslPort nebo httpPort, v závislosti na tom, jestli se používá protokol SSL.  Při cílení na kontejnery Windows ve Windows 10 RS3 nebo starší se ale v závislosti na tom, jestli se používá SSL, nahradí buď "443", nebo "80".|

::: moniker-end

::: moniker range=">=vs-2019"

| Název nastavení         | Příklad                                               | Popis                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| CommandLineArgs –      | "CommandLineArgs –": "--mysetting hodnota"              | Tyto argumenty příkazového řádku se používají při spuštění projektu v kontejneru.                                     |
| environmentVariables | "environmentVariables": {                             | Tyto hodnoty proměnných prostředí jsou předány procesu při jeho spuštění v kontejneru.                       |
|                      | "ASPNETCORE_URLS": "https://+:443; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Tento port na hostiteli je při spuštění kontejneru mapován na port 80 kontejneru.                                |
|                      |                                                       | Pokud tento parametr nezadáte, hodnota se převezme z hodnoty iisSettings.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Označuje, zda se má po úspěšném spuštění projektu spustit prohlížeč.                                       |
| launchUrl            | "launchUrl": "<scheme>://<serviceHost>:<servicePort>" | Tato adresa URL se používá při spuštění prohlížeče. Podporované náhradní tokeny pro tento řetězec jsou:                          |
|                      |                                                       | - <scheme> – v závislosti na tom, jestli se používá SSL, nahradí buď http nebo HTTPS.                                   |
|                      |                                                       | - <serviceHost> – obvykle nahrazuje "localhost".                                                                    |
|                      |                                                       | Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starší, nahradí se tím i IP adresou kontejneru.           |
|                      |                                                       | - <servicePort> – obvykle nahrazuje buď sslPort nebo httpPort, v závislosti na tom, zda se používá protokol SSL.                   |
|                      |                                                       | Pokud cílíte na kontejnery Windows ve Windows 10 RS3 nebo starším, je ale nahrazuje se buď "443", nebo "80".         |
|                      |                                                       | záleží na tom, jestli se používá protokol SSL.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Tento port na hostiteli je při spuštění kontejneru mapován na port 443 kontejneru.                               |
|                      |                                                       | Pokud tento parametr nezadáte, hodnota se převezme z hodnoty iisSettings.                                                          |
| useSSL               | "useSSL": true                                        | Určuje, zda se má při spuštění projektu použít protokol SSL. Pokud useSSL není zadaný, použije se SSL, když sslPort > 0. |

::: moniker-end

## <a name="next-steps"></a>Další kroky

Nakonfigurujte projekt nastavením [vlastností kontejnerových nástrojů](container-msbuild-properties.md).

## <a name="see-also"></a>Viz také:

[Docker Compose vlastnosti sestavení](docker-compose-properties.md)
