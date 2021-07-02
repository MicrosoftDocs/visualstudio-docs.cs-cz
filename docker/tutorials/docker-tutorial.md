---
title: 'Kurz: Začínáme s Docker & Visual Studio Code'
description: Vícekroový kurz, který se zabývá základy práce s Dockerem s Visual Studio Code.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: tutorial
ms.workload:
- azure
next_page: app.md
ms.openlocfilehash: 75a51f478e4e58700f6025dd6a87fcc38439ed87
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222653"
---
# <a name="tutorial-get-started-with-docker"></a>Kurz: Začínáme s Dockerem

V tomto kurzu se dozvíte o vytváření a nasazování aplikací Dockeru, včetně použití více kontejnerů s databází a použití Docker Compose. Kontejnerizovanou aplikaci také nasadíte do Azure.

## <a name="start-the-tutorial"></a>Zahájení kurzu

Pokud jste už s tímto kurzem začali, blahopřejeme!  Pokud ne, otevřete příkazový řádek nebo okno Bash a spusťte příkaz:

```cli
docker run -d -p 80:80 docker/getting-started
```

Všimněte si, že se používá několik příznaků. Tady je několik dalších informací:

- `-d` – spuštění kontejneru v odpojeném režimu (na pozadí)
- `-p 80:80` – namapování portu 80 hostitele na port 80 v kontejneru
- `docker/getting-started` – image, která se má použít

> [!TIP]
> Pokud chcete zkrátit celý příkaz, můžete kombinovat příznaky s jedním znakem.
> Například výše uvedený příkaz by mohl být napsán takto:
>
> ```cli
> docker run -dp 80:80 docker/getting-started
> ```

## <a name="the-vs-code-extension"></a>Rozšíření VS Code

Než zajdeme příliš daleko, chceme zvýraznit rozšíření Docker VS Code, které poskytuje rychlý přehled o kontejnerech spuštěných na vašem počítači. Poskytuje rychlý přístup k protokolům kontejnerů, umožňuje získat prostředí uvnitř kontejneru a umožňuje snadno spravovat životní cyklus kontejneru (zastavit, odebrat atd.).

Pokud chcete získat přístup k rozšíření, postupujte podle [těchto pokynů.](https://code.visualstudio.com/docs/containers/overview) Zobrazení Dockeru otevřete pomocí ikony Dockeru na levé straně. Pokud teď rozšíření otevřete, uvidíte, že tento kurz je spuštěný. Název kontejneru `angry_taussig` (níže) je náhodně vytvořený název. Pravděpodobně budete mít jiný název.

![Kurz kontejneru spuštěného v rozšíření Dockeru](media/vs-tutorial-in-extension.png)

## <a name="what-is-a-container"></a>Co je kontejner

Když jste teď spouštěi kontejner, co *je* kontejner? Jednoduše řečeno, kontejner je jednoduše jiný proces na vašem počítači, který je izolovaný od všech ostatních procesů na hostitelském počítači. Tato izolace využívá [obory názvů jádra](https://medium.com/@saschagrunert/demystifying-containers-part-i-kernel-space-2c53d6979504)a skupiny cgroup , funkce, které jsou v Linuxu už dlouhou dobu. Docker pracuje na tom, aby tyto možnosti byly přístupné a snadno použitelné.

> [!NOTE]
> **Vytváření kontejnerů od nuly** Pokud se chcete podívat, jak se kontejnery vytvářejí od nuly, Liz Sean ze společnosti Aqua Security obsahuje video, ve kterém v Go vytvoří kontejner od nuly:
>
> [!VIDEO https://www.youtube-nocookie.com/embed/8fi7uSYlOdc]

## <a name="what-is-a-container-image"></a>Co je image kontejneru

Při spuštění kontejneru používá izolovaný systém souborů. Tento vlastní systém souborů poskytuje image **kontejneru**. Vzhledem k tomu, že image obsahuje systém souborů kontejneru, musí obsahovat vše potřebné ke spuštění aplikace – všechny závislosti, konfigurace, skripty, binární soubory atd. Image obsahuje také další konfiguraci kontejneru, například proměnné prostředí, výchozí příkaz ke spuštění a další metadata.

Obrázky se budeme hlouběji ponořit do dalších témat, jako jsou vrstvení, osvědčené postupy a další.

> [!NOTE]
> Pokud jste obeznámeni s , kontejner si `chroot` představte jako rozšířenou verzi `chroot` . Systém souborů jednoduše pochází z image. Kontejner ale přidá další izolaci, která není dostupná, když jednoduše použijete chroot.

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Aplikace](your-application.md)
