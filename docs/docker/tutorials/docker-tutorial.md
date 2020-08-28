---
title: Kurz Docker – Začínáme s Docker
description: Podrobný kurz, který se zabývá základy práce s Docker a Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 9961810ad408a384db46439235b0b7acab325062
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039177"
---
# <a name="tutorial-get-started-with-docker"></a>Kurz: Začínáme s Docker

V tomto kurzu se naučíte vytvářet a nasazovat aplikace v Docker, včetně použití více kontejnerů s databází, a používání Docker Compose. Do Azure nasadíte také svou kontejnerovou aplikaci.

## <a name="start-the-tutorial"></a>Zahájení kurzu

Pokud jste již spustili příkaz, abyste mohli začít s kurzem, Blahopřejeme!  V takovém případě otevřete příkazový řádek nebo okno bash a spusťte příkaz:

```cli
docker run -d -p 80:80 docker/getting-started
```

Všimněte si, že se používá několik příznaků. Tady je několik dalších informací:

- `-d` -spustit kontejner v odpojeném režimu (na pozadí)
- `-p 80:80` – mapování portu 80 hostitele na port 80 v kontejneru
- `docker/getting-started` – obrázek, který se má použít

> [!TIP]
> Pro zkrácení celého příkazu můžete kombinovat příznaky s jedním znakem.
> Jako příklad můžete zapsat výše uvedený příkaz jako:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Rozšíření VS Code

Než bude příliš daleko, chceme zvýraznit rozšíření Docker VS Code, které vám poskytne rychlý přehled o kontejnerech spuštěných na vašem počítači. Poskytuje rychlý přístup k protokolům kontejnerů, umožňuje získat prostředí uvnitř kontejneru a umožňuje snadno spravovat životní cyklus kontejnerů (zastavit, odebrat atd.).

Pokud chcete získat přístup k rozšíření, postupujte podle pokynů uvedených [tady](https://code.visualstudio.com/docs/containers/overview). Pomocí ikony Docker na levé straně otevřete zobrazení Docker. Pokud teď rozšíření otevřete, zobrazí se tento kurz. Název kontejneru ( `angry_taussig` níže) je náhodně vytvořený název. To znamená, že budete mít pravděpodobně jiný název.

![Kontejner kurzu běžící v rozšíření Docker](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Co je kontejner

Teď, když jste spustili kontejner, co *je* kontejner? Jednoduše řečeno, kontejner je v počítači jednoduše jiný proces, který je izolovaný od všech ostatních procesů na hostitelském počítači. Tato izolace využívá [obory názvů kernel a cgroups](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504), funkce, které byly v systému Linux po dlouhou dobu. Docker pracoval za účelem zajištění přístupu k těmto funkcím a jejich snadnému používání.

> [!NOTE]
> **Vytváření kontejnerů od začátku** Pokud se chcete podívat, jak jsou kontejnery sestavené od začátku, má Lizá rýže z nástroje azurová Security video, ve kterém se vytvoří kontejner úplně od začátku v rámci služby přejděte:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Co je image kontejneru

Při spuštění kontejneru používá izolovaný systém souborů. Tento vlastní systém souborů je poskytován **imagí kontejneru**. Vzhledem k tomu, že bitová kopie obsahuje systém souborů kontejneru, musí obsahovat vše potřebné ke spuštění aplikace – všechny závislosti, konfigurace, skripty, binární soubory a tak dále. Obrázek obsahuje také další konfiguraci kontejneru, například proměnné prostředí, výchozí příkaz ke spuštění a další metadata.

Budeme podrobně hlouběji na obrázky, a to i na témata, jako je vrstvení, osvědčené postupy a další.

> [!NOTE]
> Pokud jste obeznámeni s `chroot` , můžete si kontejner představit jako rozšířenou verzi nástroje `chroot` . Systém souborů jednoduše přichází z obrázku. Kontejner ale přidává další izolaci, která není k dispozici, když jednoduše použijete chroot.

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Aplikace](your-application.md)
