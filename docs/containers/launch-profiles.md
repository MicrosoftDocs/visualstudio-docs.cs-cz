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
ms.openlocfilehash: 003205525f883b010f897e6e47d4cab92a31b8a1
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2021
ms.locfileid: "110018503"
---
# <a name="manage-launch-profiles-for-docker-compose-preview"></a>Správa spouštěcích profilů pro Docker Compose (Preview)

Pokud máte aplikaci, která se skládá z více služeb a používá Docker Compose, můžete nakonfigurovat, které služby se spouští a ladí, vytvořením nebo úpravou existujícího spouštěcího profilu v nastavení Docker Compose spuštění. Spouštěcí profily umožňují dynamicky spouštět jenom služby, které jsou pro váš aktuální scénář důležité. Můžete vytvořit a vybrat ze spouštěcích profilů, abyste si přizpůsobíte možnosti ladění a nastavili konkrétní akce spuštění, jako je `Browser Launch URL` . Budete mít také možnost zvolit každou službu samostatně nebo výběrem profilu Docker Compose, který se také podívá na váš soubor Compose a určí skupinu služeb, které se mají spustit.

Informace o profilech Docker Compose najdete v tématu [Použití profilů s psaním.](https://docs.docker.com/compose/profiles/)
 
## <a name="prerequisites"></a>Požadavky

- [Visual Studio 2019 verze 16.10 Preview](https://visualstudio.microsoft.com/vs/preview/) nebo novější
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

V následujícím příkladu je vybrán profil Psaní, který vyfiltruje seznam Služby jenom na tři z pěti součástí `web1` tohoto profilu: 

![Snímek obrazovky s dialogem nastavení spuštění](media/launch-settings/launch-settings-create-profile.png)

Část Profiles Docker Compose se zobrazí pouze v případě, že jsou v souborech *Docker-Compose. yml* definovány profily.

Další příklad ukazuje, jak vybrat jednotlivé služby místo filtrování do služeb ve vytváření profilu. Tady ukážeme, jak by dialogové okno vypadalo, pokud jste vytvořili nový profil spuštění s názvem `test2` , který spouští pouze dvě z pěti služeb `webapplication1` s laděním a `webapplication2` bez ladění.  Tento spouštěcí profil také spustí prohlížeč při spuštění aplikace a otevře se na domovské stránce `webapplication1` . 

![Snímek obrazovky dialogového okna pro nastavení spuštění s některými službami byl nevybraný.](media/launch-settings/launch-settings-selected.png)

A tyto informace budou uloženy v *launchSettings.js* , jak je uvedeno níže.

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

## <a name="create-a-launch-profile-that-uses-a-docker-compose-profile"></a>Vytvořit profil spuštění, který používá profil Docker Compose

Můžete také dále přizpůsobit chování při spuštění tím, že vytvoříte profily spuštění sady Visual Studio, které využívají profily pro vytváření.

Pokud chcete vytvořit jiný profil, který využívá profil pro vytváření, vyberte **použít Docker Compose profily** a zvolte `web1` . Teď profil spuštění zahrnuje tři služby – `webapplication1` (které patří do profilů i `web` `web1` vytváření) `external1` a `external2` . Ve výchozím nastavení služby bez zdrojového kódu, jako jsou `external1` a,  `external2` mají výchozí akci **Spustit bez ladění**. Aplikace .NET se zdrojovým kódem budou **spouštět ladění** jako výchozí.

> [!IMPORTANT]
> Pokud služba neurčí profil pro vytváření, bude se ve všech profilech vytváření implicitně zahrnovat.

![Snímek obrazovky s dialogem nastavení spuštění s jiným vytvořeným profilem](media/launch-settings/launch-settings-create-profile.png)

Tyto informace budou uloženy, jak je znázorněno v následujícím kódu. Konfigurace služby a její výchozí akce nebudou uloženy, pokud nezměníte výchozí akci.

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

Akci WebApplication1 můžete také změnit tak, aby se **spouštěla bez ladění**. Nastavení v *launchSettings.js* a pak vypadají jako následující kód:

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

Tady je popis každé vlastnosti v *launchSettings.js*:

|Vlastnost| Popis|
| - | - |
|commandName| Název příkazu. Výchozí hodnota je DockerCompose.|
|commandVersion (verze příkazu)| Číslo verze použité ke správě schématu profilu spuštění DockerCompose.|
|composeProfile| Nadřazená vlastnost, která definuje definici profilu spuštění. Podřízené vlastnosti jsou a . `includes``serviceActions`|
|composeProfile – zahrnuje | Seznam názvů profilů Compose, které tvoří spouštěcí profil|
|composeProfile – serviceActions | Vypíše vybrané profily, služby a akci spuštění každé služby.|
|akce služby | Vypíše vybrané služby a akci spuštění.|
|composeLaunchServiceName| Pokud jsou zadané DockerLaunchAction nebo DockerLaunchBrowser, dockerServiceName je název služby, která se má spustit. Pomocí této vlastnosti můžete určit, která služba Docker Compose se spustí.|
|composeLaunchAction| Určuje akci spuštění, která se má provést na **F5** nebo **Ctrl** + **F5.** Povolené hodnoty jsou None, LaunchBrowser a LaunchWCFTestClient.|
|composeLaunchUrl| Adresa URL, která se má použít při spuštění prohlížeče. Platné náhradní tokeny jsou {ServiceIPAddress}, {ServicePort} a {schéma}. Příklad: {schéma}://{ServiceIPAddress}: {ServicePort}|

## <a name="next-steps"></a>Další kroky

Další informace o fungování nástrojů kontejnerů najdete v tématu [Přehled sestavení a ladění sady Visual Studio Container Tools](container-build.md).

## <a name="see-also"></a>Viz také

- [Nastavení spuštění nástrojů kontejneru sady Visual Studio](container-launch-settings.md)

- [Docker Compose nastavení sestavení](docker-compose-properties.md)
