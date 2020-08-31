---
title: 'Kurz Docker – část 5: použití připojení vazby'
description: Popisuje způsob použití připojení BIND k řízení přípojného bodu na hostiteli.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 6474179a0714f2407ac37e724b997139206a91fb
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2020
ms.locfileid: "89178238"
---
# <a name="use-bind-mounts"></a>Použít připojení vazeb

V předchozí kapitole jste se dozvěděli o a použili jste **pojmenovaný svazek** pro zachování dat ve vaší databázi. Pojmenované svazky jsou skvělé, pokud chcete jenom ukládat data, protože se nemusíte starat o *to, kde* se data ukládají.

S **připojením k vazbám**řídíte přesnou přípojný bod na hostiteli. Tuto možnost můžete použít k uchovávání dat, ale často se používá k poskytnutí dalších dat do kontejnerů. Při práci na aplikaci můžete použít připojení BIND pro připojení zdrojového kódu do kontejneru, aby viděli změny kódu, odpověděli a umožnili vám zobrazit změny hned.

Pro aplikace založené na uzlech je [nodemon](https://npmjs.com/package/nodemon) skvělým nástrojem ke sledování změn souborů a následnému restartování aplikace. Pro většinu ostatních jazyků a platforem existují ekvivalentní nástroje.

## <a name="quick-volume-type-comparisons"></a>Rychlé porovnávání typů svazků

Připojení k vazbám a pojmenované svazky jsou dva hlavní typy svazků, které jsou dodávány s modulem Docker. K dispozici jsou ale další ovladače svazků, které podporují jiné případy použití ([SFTP](https://github.com/vieux/docker-volume-sshfs), [CEPH](https://ceph.com/geen-categorie/getting-started-with-the-docker-rbd-volume-plugin/), [NetApp](https://netappdvp.readthedocs.io/en/stable/), [S3](https://github.com/elementar/docker-s3-volume)a další).

| Vlastnost | Pojmenované svazky | Připojení vazeb |
| -------- | ------------- | ----------- |
| Umístění hostitele | Výběry Docker | Řídíte |
| Příklad připojení (using `-v` ) | můj svazek:/usr/local/data | /path/to/data:/usr/local/data |
| Naplní nový svazek obsahem kontejneru. | Ano | Ne |
| Podporuje ovladače svazků | Ano | Ne |

## <a name="start-a-dev-mode-container"></a>Spuštění kontejneru vývojového režimu

Pokud chcete svůj kontejner spustit pro podporu vývojového pracovního postupu, proveďte následující:

- Připojit zdrojový kód do kontejneru
- Nainstalovat všechny závislosti, včetně závislostí pro vývoj
- Spusťte nodemon a sledujte změny systému souborů.

1. Ujistěte se, že nemáte spuštěné žádné předchozí `getting-started` kontejnery.

1. Spusťte následující příkaz (nahraďte ` \ ` znaky `` ` `` ve Windows PowerShellu). Dozvíte se, co se stane dál:

    ```bash
    docker run -dp 3000:3000 \
        -w /app -v ${PWD}:/app \
        node:12-alpine \
        sh -c "yarn install && yarn run dev"
    ```

    - `-dp 3000:3000` – stejné jako předtím. Spustit v odpojeném režimu (na pozadí) a vytvořit mapování portů
    - `-w /app` -Nastaví "pracovní adresář" nebo aktuální adresář, ze kterého bude příkaz spuštěn.
    - `-v ${PWD}:/app` -BIND připojí aktuální adresář od hostitele v kontejneru do `/app` adresáře.
    - `node:12-alpine` – obrázek, který se má použít Všimněte si, že toto je základní image vaší aplikace z souboru Dockerfile.
    - `sh -c "yarn install && yarn run dev"` – příkaz. Spouštíme prostředí pomocí `sh` (Alpine není `bash` ) a běží `yarn install` na instalaci *všech* závislostí a následném spuštění `yarn run dev` . Pokud se podíváte na `package.json` , uvidíme, že se `dev` skript spouští `nodemon` .

1. Protokoly můžete sledovat pomocí `docker logs -f <container-id>` . Víte, že jste připraveni přejít na toto:

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

    Až budete s sledováním protokolů hotovi, ukončete činnost `Ctrl` + `C` .

1. Nyní proveďte v aplikaci změnu. V `src/static/js/app.js` souboru změňte tlačítko **Přidat položku** tak, aby jednoduše vyslovení příkazu **Přidat**. Tato změna bude na řádku 109.

    ```diff
    -                         {submitting ? 'Adding...' : 'Add Item'}
    +                         {submitting ? 'Adding...' : 'Add'}
    ```

1. Jednoduše aktualizujte stránku (nebo ji otevřete) a měli byste vidět, že se změna v prohlížeči projeví téměř okamžitě. Restartování serveru Node může trvat několik sekund, takže pokud se zobrazí chyba, stačí zkusit aktualizaci po několika sekundách.

    ![Snímek obrazovky s aktualizovaným popiskem pro tlačítko Přidat](media/updated-add-button.png)

1. Nebojte se udělat jakékoli další změny, které byste chtěli udělat. Až skončíte, zastavte kontejner a sestavte novou image pomocí `docker build -t getting-started .` .

Použití připojení BIND je *velmi* běžné pro místní vývojové nastavení. Výhodou je, že vývojového počítače nemusí mít nainstalované všechny nástroje sestavení a prostředí. Jediným `docker run` příkazem je vývojové prostředí vyžádáno a připraveno k použití. Dozvíte se o Docker Compose v budoucím kroku, protože to pomůže zjednodušit příkazy (už se vám zobrazuje spousta příznaků).

## <a name="recap"></a>Rekapitulace

V tuto chvíli můžete databázi uchovávat a rychle reagovat na potřeby a požadavky vašich investorů a nalezených uživatelů. Radostných! Ale odhadujte, co? Dostali jsme skvělé novinky!

**Váš projekt byl vybrán pro budoucí vývoj.**

Aby bylo možné připravit se na produkční prostředí, je nutné migrovat databázi z práce v SQLite na něco, co může škálovat trochu lépe. V zájmu jednoduchosti zůstanete v relační databázi a přepněte svou aplikaci, aby používala MySQL. Ale jak byste měli používat MySQL? Jak umožníte, aby kontejnery navzájem komunikovaly? Dozvíte se o této další službě!

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Vícekontejnerové aplikace](multi-container-apps.md)