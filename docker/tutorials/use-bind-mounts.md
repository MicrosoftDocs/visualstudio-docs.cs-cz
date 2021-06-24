---
title: 'Kurz Dockeru – část 5: Použití připojení vazeb'
description: Popisuje způsob použití vázání připojení k řízení přípojového bodu na hostiteli.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6a4aa7623f69f9b02f9649a1a66ade010a823669
ms.sourcegitcommit: 98d187abd9352d2255348b84d99d015e65caa0ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2021
ms.locfileid: "112574110"
---
# <a name="use-bind-mounts"></a>Použití připojení vazeb

V předchozí kapitole jste se dozvěděli o **pojmenovaném** svazku a použili ho k zachování dat v databázi. Pojmenované svazky jsou skvělé, pokud chcete jednoduše ukládat data,  protože si nemusíte dělat starosti s tím, kde jsou data uložená.

S **připojeními vazby** řídíte přesný přípojný bod na hostiteli. Můžete ho použít k uchování dat, ale často se používá k poskytování dalších dat do kontejnerů. Při práci s aplikací můžete použít vazbu připojení k připojení zdrojového kódu ke kontejneru, abyste mohli vidět změny kódu, reagovat a okamžitě zobrazit změny.

V případě aplikací založených na Node [je nástroj nodemon](https://npmjs.com/package/nodemon) skvělým nástrojem ke sledování změn souborů a následně restartování aplikace. Ve většině ostatních jazyků a architektur existují ekvivalentní nástroje.

## <a name="quick-volume-type-comparisons"></a>Rychlé porovnání typů svazků

Připojení vazeb a pojmenované svazky jsou dva hlavní typy svazků, které jsou součástí modulu Docker. K dispozici jsou ale další ovladače svazků pro podporu dalších případů použití ([SFTP,](https://github.com/vieux/docker-volume-sshfs) [Ceph,](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/) [NetApp,](https://netappdvp.readthedocs.io/en/stable/) [S3](https://github.com/elementar/docker-s3-volume)a další).

| Vlastnost | Pojmenované svazky | Připojení vazeb |
| -------- | ------------- | ----------- |
| Umístění hostitele | Docker chooses | Ovládací prvek |
| Příklad připojení (pomocí `-v` ) | my-volume:/usr/local/data | /path/to/data:/usr/local/data |
| Naplní nový svazek obsahem kontejneru. | Yes | No |
| Podporuje ovladače svazků. | Yes | No |

## <a name="start-a-dev-mode-container"></a>Spuštění kontejneru v režimu pro vývoj

Pokud chcete kontejner spustit pro podporu vývojového pracovního postupu, proveďte následující:

- Připojení zdrojového kódu ke kontejneru
- Instalace všech závislostí, včetně závislostí pro vývoj
- Spusťte nástroj nodemon, abyste sledovali změny systému souborů.

1. Ujistěte se, že nemáte spuštěné žádné předchozí `getting-started` kontejnery.

1. Spusťte následující příkaz (nahraďte ` \ ` znaky v `` ` `` souboru Windows PowerShell). Potom se dozvíte, co se děje:

    ```bash
    docker run -dp 3000:3000 \
        -w /app \
        -v "%cd%:/app" \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` – stejné jako předtím. Spuštění v odpojeném režimu (na pozadí) a vytvoření mapování portů
    - `-w /app` – nastaví "pracovní adresář" nebo aktuální adresář, ze které se příkaz spustí.
    - `-v "%cd%:/app"` – vytvořte vazbu na připojení aktuálního adresáře z hostitele v kontejneru k `/app` adresáři .
    - `node:12-alpine` – image, která se má použít. Všimněte si, že se jedná o základní image vaší aplikace ze souboru Dockerfile.
    - `sh -c "yarn install && yarn run dev"` – příkaz . Spouštíme prostředí pomocí příkazu (alpine nemá ) a spuštěním příkazu nainstalujeme všechny závislosti a `sh` `bash` pak `yarn install` spouštíme  `yarn run dev` . Pokud se podíváte do `package.json` , uvidíme, že `dev` skript spouští `nodemon` .

1. Protokoly můžete sledovat pomocí `docker logs -f <container-id>` příkazu . Až uvidíte toto, budete vědět, že jste připraveni na to:

    ```bash
    docker logs -f <container-id>
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Using sqlite database at /etc/todos/todo.db
    Listening on port 3000
    ```

    Až budete se sledováním protokolů hotovi, ukončete ho kliknutím na `Ctrl` + `C` .

1. Teď v aplikaci proveďte změnu. V souboru `src/static/js/app.js` změňte tlačítko **Přidat** položku tak, aby jednoduše řeklo **Přidat**. Tato změna bude na řádku 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Stačí stránku aktualizovat (nebo ji otevřít) a tato změna by se měla projevit téměř okamžitě v prohlížeči. Restartování serveru Node může trvat několik sekund, takže pokud se zobrazí chyba, zkuste aktualizaci za několik sekund.

    ![Snímek obrazovky s aktualizovaným popiskem tlačítka Přidat](media/updated-add-button.png)

1. Klidně proveďte všechny další změny, které byste chtěli udělat. Až budete hotovi, zastavte kontejner a sestavte novou image pomocí `docker build -t getting-started .` .

Použití připojení vazeb je *u místních* vývojových nastavení velmi běžné. Výhodou je, že vývojový počítač nemusí mít nainstalované všechny nástroje a prostředí sestavení. Jediným `docker run` příkazem se vývojové prostředí vyžádá a je připravené k vypravování. O těchto příkazech Docker Compose v dalším kroku, protože vám to pomůže zjednodušit příkazy (už máte spoustu příznaků).

## <a name="recap"></a>Rekapitulace

V tuto chvíli můžete databázi zachovat a rychle reagovat na potřeby a požadavky vašich investoři a zakladatelů. Hurá! Ale co? Obdrželi jste skvělé zprávy!

**Váš projekt byl vybrán pro budoucí vývoj!**

Abyste se mohli připravit na produkci, musíte databázi migrovat z práce v SQLite na něco, co dokáže škálovat o něco lépe. Kvůli zjednodušení budete používat relační databázi a přepnete aplikaci na mySQL. Jak byste ale mySQL měli spustit? Jak můžete kontejnerům umožnit vzájemnou vzájemnou rozhovory? O tom se dozvíte dále!

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Vícekontejnerové aplikace](multi-container-apps.md)