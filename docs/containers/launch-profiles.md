---
title: Správa spouštěcích profilů pro Docker Compose projekty
description: Naučte se používat profily Docker Compose spouštění a řídit, které služby se spustí, když použijete Docker Compose v Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.devlang: dotnet
ms.topic: how-to
ms.date: 05/10/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: e740ea3b7950c14bf11522c4e438a105b09eb7f6
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433698"
---
# <a name="manage-launch-profiles-for-docker-compose"></a>Správa spouštěcích profilů pro Docker Compose

Pokud máte aplikaci, která se skládá z více služeb a používá Docker Compose, můžete nakonfigurovat, které služby se spouští a ladí, vytvořením nebo úpravou existujícího spouštěcího profilu v nastavení Docker Compose spuštění. Spouštěcí profily umožňují dynamicky spouštět jenom služby, které jsou pro váš aktuální scénář důležité. Můžete vytvořit a vybrat ze spouštěcích profilů, abyste přizpůsobíte prostředí ladění a nastavili konkrétní akce spuštění, jako je `Browser Launch URL` . Budete mít také možnost zvolit každou službu samostatně nebo výběrem profilu Docker Compose, který se také podívá na váš soubor Compose a určí skupinu služeb, které se mají spustit.

Informace o profilech Docker Compose naleznete v tématu [Using profiles with Compose](https://docs.docker.com/compose/profiles/).
 
## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019 verze 16.10](https://visualstudio.microsoft.com/vs/) nebo novější
- Řešení s [orchestrací kontejnerů s Docker Compose](tutorial-multicontainer.md)

## <a name="manage-launch-settings"></a>Správa nastavení spuštění

Představte si následující Docker Compose, ve kterém *má soubor docker-compose.yml* pět služeb a tři profily Compose (web, web1 a web2).

```yml
version: '3.9'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    profiles: [web, web1]
    build:
      context: .
      dockerfile: WebApplication1/Dockerfile

  webapplication2:
    image: ${DOCKER_REGISTRY-}webapplication2
    profiles: [web, web2]
    build:
      context: .
      dockerfile: WebApplication2/Dockerfile

  webapplication3:
    image: ${DOCKER_REGISTRY-}webapplication3
    profiles: [web]
    build:
      context: .
      dockerfile: WebApplication3/Dockerfile

  external1:
    image: redis

  external2:
    image: redis

```

Existuje několik možností, jak otevřít dialogové okno Docker Compose spuštění:
- V Visual Studio nastavení spuštění   >  **zvolte Docker Compose ladění:**

    ![Snímek obrazovky s položkou nabídky Debug Manage Compose Settings (Ladění a správa nastavení psaní)](media/launch-settings/debug-dropdown-manage-compose.png)

- Klikněte pravým tlačítkem na projekt Visual Studio `docker-compose` a vyberte Spravovat nastavení Docker Compose **spuštění.**

    ![Snímek obrazovky s položkou místní nabídky](media/launch-settings/launch-settings-context-menu.png)

- Pomocí Snadné spuštění (**Ctrl** Q ) a vyhledejte Docker Compose výše uvedený + příkaz. 

V následujícím příkladu je vybrán profil Psaní, který vyfiltruje seznam Služeb pouze na tři z pěti součástí `web1` tohoto profilu: 

![Snímek obrazovky s dialogem nastavení spuštění](media/launch-settings/launch-settings-create-profile.png)

Část Docker Compose profiles se zobrazí pouze v případě, že jsou v souborech *docker-compose.yml* definované profily.

Následující příklad ukazuje výběr mezi jednotlivými službami místo filtrování na služby v profilu Psaní. Tady si ukážeme, jak by dialogové okno vypadalo, pokud jste vytvořili nový profil spuštění s názvem , který spustí pouze dvě z pěti služeb s laděním a `test2` `webapplication1` bez `webapplication2` ladění.  Tento profil spuštění také spustí prohlížeč při spuštění aplikace a otevře ho na domovské stránce `webapplication1` . 

![Snímek obrazovky s dialogem nastavení spuštění a zrušenou výběrem některých služeb](media/launch-settings/launch-settings-selected.png)

Tyto informace se uloží v *launchSettings.js,* jak je znázorněno níže.

```json
{
    "profiles": {
      "test2": {
        "commandName": "DockerCompose",
        "composeLaunchServiceName": "webapplication1",
        "serviceActions": {
          "external1": "DoNotStart",
          "external2": "DoNotStart",
          "webapplication1": "StartDebugging",
          "webapplication2": "StartWithoutDebugging",
          "webapplication3": "DoNotStart"
        },
        "composeLaunchAction": "LaunchBrowser",
        "commandVersion": "1.0",
        "composeLaunchUrl": "{Scheme}://localhost:{ServicePort}"
      }
   }
}
```

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Vytvoření profilu spuštění, který používá profil Docker Compose profilu

Chování při spouštění můžete také dále přizpůsobit vytvořením Visual Studio spouštěcích profilů, které používají profily psaní.

Pokud chcete vytvořit další profil, který profil Psaní používá, vyberte Použít **Docker Compose profilů a** zvolte `web1` . Profil spuštění teď obsahuje tři služby (které patří do profilů i `webapplication1` `web` `web1` Compose) a `external1` `external2` . Ve výchozím nastavení mají služby bez zdrojového kódu, například a, výchozí `external1` akci Spustit bez  `external2` **ladění**. Aplikace .NET se zdrojovým kódem se ve výchozím nastavení spustí **ladění.**

> [!IMPORTANT]
> Pokud služba nezadá profil Psaní, zahrne se implicitně do všech profilů Psaní.

![Snímek obrazovky s dialogem nastavení spuštění s jiným vytvořeným profilem](media/launch-settings/launch-settings-create-profile.png)

Tyto informace se uloží, jak je znázorněno v následujícím kódu. Konfigurace služby a její výchozí akce se neuloží, pokud nezměníte výchozí akci.

```json
{
  "profiles": {
    "test1": {
      "commandName": "DockerCompose",
      "composeProfile": {
         "includes": [
            "web1"
         ]
      },
      "commandVersion": "1.0"
    }
  }
}
```

Akci webapplication1 můžete také změnit na Spustit **bez ladění.** Nastavení v *launchSettings.jspak* vypadají jako následující kód:

```json
{
  "profiles": {
    "test1": {
        "commandName": "DockerCompose",
        "composeProfile": {
          "includes": [
              "web1"
              ],
          "serviceActions": {
              "webapplication1": "StartWithoutDebugging"
          }
        },
    "commandVersion": "1.0"
    }
  }
}
```

## <a name="properties"></a>Vlastnosti

Tady je popis jednotlivých vlastností vlaunchSettings.js *na*:

|Vlastnost| Popis|
| - | - |
|Commandname| Název příkazu. Výchozí hodnota je DockerCompose.|
|commandVersion (verze příkazu)| Číslo verze použité ke správě schématu spouštěcího profilu DockerCompose.|
|composeProfile| Nadřazená vlastnost, která definuje definici spouštěcího profilu. Podřízené vlastnosti jsou a . `includes``serviceActions`|
|composeProfile – zahrnuje | Seznam názvů profilů Compose, které tvoří profil spuštění.|
|composeProfile – serviceActions | Vypíše vybrané profily, služby a akci spuštění každé služby.|
|akce služby | Vypíše vybrané služby a akci spuštění.|
|composeLaunchServiceName| Pokud jsou zadané DockerLaunchAction nebo DockerLaunchBrowser, dockerServiceName je název služby, která se má spustit. Pomocí této vlastnosti můžete určit, která služba Docker Compose se spustí.|
|composeLaunchAction| Určuje akci spuštění, která se má provést na **F5** nebo **Ctrl** + **F5.** Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient.|
|composeLaunchUrl| Adresa URL, která se má použít při spuštění prohlížeče. Platné náhradní tokeny jsou {ServiceIPAddress}, {ServicePort} a {Scheme}. Příklad: {Scheme}://{ServiceIPAddress}:{ServicePort}|

## <a name="next-steps"></a>Další kroky

Další informace o tom, jak nástroje Container Tools fungují, najdete [v Visual Studio přehledu](container-build.md)sestavení a ladění nástroje Container Tools.

## <a name="see-also"></a>Viz také

- [Visual Studio nastavení spuštění nástroje Container Tools](container-launch-settings.md)

- [Docker Compose nastavení sestavení](docker-compose-properties.md)
