---
title: 'Kurz Docker – část 6: aplikace s více kontejnery'
description: Jak nastavit síť mezi kontejnery a přidat kontejner pro databázi MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 9513a3414a38aa02f6a4607a8c95bbf02c0e1cf6
ms.sourcegitcommit: f4d734329c82f2c8005b36af4b2b5516d90e6c63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2020
ms.locfileid: "89039023"
---
# <a name="multi-container-apps"></a>Vícekontejnerové aplikace

Do tohoto okamžiku jste pracovali s aplikacemi s jedním kontejnerem. Teď ale přidáte MySQL do aplikačního zásobníku. K následující otázce často dochází – "kde se bude MySQL spouštět? Nainstalujte ji do stejného kontejneru nebo ho spouštějte samostatně? " Obecně platí, **že každý kontejner by měl dělat jednu věc a dělat dobře.** Několik důvodů:

- Je velmi pravděpodobné, že byste museli škálovat rozhraní API a front-endy odlišně než databáze.
- Samostatné kontejnery umožňují verzi a aktualizace verzí v izolaci.
- I když můžete použít kontejner pro databázi místně, možná budete chtít použít spravovanou službu pro databázi v produkčním prostředí. Do své aplikace nechcete dodávat databázový stroj.
- Spuštění více procesů bude vyžadovat správce procesů (kontejner spouští pouze jeden proces), což zvyšuje složitost spouštění a vypínání kontejneru.

A existují další důvody. Proto aktualizujete aplikaci tak, aby fungovala takto:

![Aplikace TODO připojená k kontejneru MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Sítě kontejnerů

Mějte na paměti, že kontejnery ve výchozím nastavení běží izolovaně a neznají nic o jiných procesech nebo kontejnerech na stejném počítači. Jak tedy umožníte komunikaci jednoho kontejneru s jiným? Odpověď je v **síti**. Teď nemusíte být pracovníkem sítě (radostných!). Jednoduše zapamatujte toto pravidlo...

> [!NOTE]
> Pokud jsou dva kontejnery ve stejné síti, mohou vzájemně komunikovat. Pokud nejsou, nemůžou.

## <a name="start-mysql"></a>Spustit MySQL

Existují dva způsoby, jak umístit kontejner do sítě: přiřaďte ho na začátek nebo připojte existující kontejner. Nyní nejprve vytvoříte síť a připojíte kontejner MySQL při spuštění.

1. Vytvořte síť.

    ```bash
    docker network create todo-app
    ```

1. Spusťte kontejner MySQL a připojte ho k síti. Také nadefinujeme několik proměnných prostředí, které bude databáze používat k inicializaci databáze (Další informace najdete v části proměnné prostředí v [seznamu rozbočovačů MySQL Docker](https://hub.docker.com/_/mysql/)) (nahraďte ` \ ` znaky `` ` `` ve Windows PowerShellu).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Uvidíte také, že jste zadali `--network-alias` příznak. Budeme se k němu vracet hned za chvilku.

    > [!TIP]
    > Všimněte si, že tady používáte název svazku `todo-mysql-data` a připojujete se `/var/lib/mysql` tam, kde MySQL ukládá svá data. Nikdy jste ale nespouštěli `docker volume create` příkaz. Docker rozpozná, že chcete použít pojmenovaný svazek a vytvořit ho automaticky pro vás.

1. Pokud chcete potvrdit, že máte databázi spuštěnou, připojte se k databázi a ověřte, že se připojuje.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Jakmile se zobrazí výzva k zadání hesla, zadejte **tajný kód**. V prostředí MySQL uveďte databáze a ověřte, že se zobrazuje `todos` databáze.

    ```cli
    mysql> SHOW DATABASES;
    ```

    Měl by se zobrazit výstup podobný tomuto:

    ```plaintext
    +--------------------+
    | Database           |
    +--------------------+
    | information_schema |
    | mysql              |
    | performance_schema |
    | sys                |
    | todos              |
    +--------------------+
    5 rows in set (0.00 sec)
    ```

    Radostných! Máte `todos` databázi a je připravená k použití.

## <a name="connect-to-mysql"></a>Připojení k MySQL

Teď, když víte, že je MySQL v provozu, pojďme použít! Ale otázka je... použití? Pokud spustíte jiný kontejner ve stejné síti, jak najít kontejner (pamatuje si, že každý kontejner má svou vlastní IP adresu)?

K tomu je potřeba použít kontejner [nicolaka/NetShoot](https://github.com/nicolaka/netshoot) , který je dodáván s *velkým množstvím* nástrojů, které jsou užitečné pro řešení potíží nebo ladění potíží se sítí.

1. Spusťte nový kontejner pomocí `nicolaka/netshoot` image. Nezapomeňte ho připojit ke stejné síti.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Uvnitř kontejneru použijte `dig` příkaz, který je užitečným nástrojem DNS. Vyhledejte IP adresu hostitele `mysql` .

    ```bash
    dig mysql
    ```

    A získáte výstup podobný tomuto...

    ```text
    ; <<>> DiG 9.14.1 <<>> mysql
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32162
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

    ;; QUESTION SECTION:
    ;mysql.             IN  A

    ;; ANSWER SECTION:
    mysql.          600 IN  A   172.23.0.2

    ;; Query time: 0 msec
    ;; SERVER: 127.0.0.11#53(127.0.0.11)
    ;; WHEN: Tue Oct 01 23:47:24 UTC 2019
    ;; MSG SIZE  rcvd: 44
    ```

    V části odpověď se zobrazí `A` záznam pro `mysql` překládání na `172.23.0.2` (vaše IP adresa bude mít pravděpodobně jinou hodnotu). I když `mysql` není obvykle platný název hostitele, Docker ho mohl přeložit na IP adresu kontejneru, který má tento alias sítě (zapamatuje si `--network-alias` příznak, který jste použili dříve?).

    Co to znamená... vaše aplikace jednoduše potřebuje připojit se k hostiteli s názvem `mysql` a bude komunikovat s databází! Neznamená to mnohem jednodušší.

## <a name="run-your-app-with-mysql"></a>Spuštění aplikace pomocí MySQL

Aplikace TODO podporuje nastavení několika proměnných prostředí, které určují nastavení připojení MySQL. Jedná se o tyto peeringy:

- `MYSQL_HOST` – název hostitele spuštěného serveru MySQL
- `MYSQL_USER` – uživatelské jméno, které se má použít pro připojení
- `MYSQL_PASSWORD` – heslo, které se má použít pro připojení
- `MYSQL_DB` – databáze, která se má použít po připojení

> [!WARNING]
> **Nastavení nastavení připojení prostřednictvím proměnných prostředí** Při používání proměnných prostředí k nastavení připojení je všeobecně dobré pro vývoj, ale při spouštění aplikací v produkčním prostředí se důrazně nedoporučuje. Informace o tom, proč [byste neměli používat proměnné prostředí pro tajná data](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/), najdete v tématu Proč.
> Bezpečnějším mechanismem je použití tajné podpory poskytované rozhraním orchestrace kontejnerů. Ve většině případů jsou tyto tajné klíče připojené jako soubory v běžícím kontejneru. Zobrazí se spousta aplikací (včetně image MySQL a aplikace TODO) taky podporuje proměnných ENV s `_FILE` příponou, která odkazuje na soubor, který obsahuje soubor.
> Například nastavení `MYSQL_PASSWORD_FILE` var způsobí, že aplikace použije obsah odkazovaného souboru jako heslo připojení. Docker nedělá cokoli k podpoře těchto ENV proměnných. Vaše aplikace bude potřebovat znát, aby vyhledala proměnnou a získala obsah souboru.

Po všech tom, co je vysvětleno, začněte svůj kontejner pro vývoj.

1. Zadejte každou z výše uvedených proměnných prostředí a připojte kontejner ke svojí aplikační síti (nahraďte ` \ ` znaky `` ` `` ve Windows PowerShellu).

    ```bash hl_lines="3 4 5 6 7"
    docker run -dp 3000:3000 \
      -w /app -v ${PWD}:/app \
      --network todo-app \
      -e MYSQL_HOST=mysql \
      -e MYSQL_USER=root \
      -e MYSQL_PASSWORD=secret \
      -e MYSQL_DB=todos \
      node:12-alpine \
      sh -c "yarn install && yarn run dev"
    ```

1. Pokud se podíváte na protokoly kontejneru ( `docker logs <container-id>` ), měla by se zobrazit zpráva s oznámením, že používá databázi MySQL.

    ```plaintext hl_lines="7"
    # Previous log messages omitted
    $ nodemon src/index.js
    [nodemon] 1.19.2
    [nodemon] to restart at any time, enter `rs`
    [nodemon] watching dir(s): *.*
    [nodemon] starting `node src/index.js`
    Connected to mysql db at host mysql
    Listening on port 3000
    ```

1. Otevřete aplikaci v prohlížeči a přidejte do seznamu úkolů několik položek.

1. Připojte se k databázi MySQL a prokázání, že se položky zapisují do databáze. Mějte na paměti, že heslo je **tajné**.

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    A v prostředí MySQL spusťte následující příkaz:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Tabulka bude vypadat jinak, protože obsahuje vaše položky. Ale měli byste vidět, že jsou tam uložené.

Pokud se podíváte na rozšíření Docker, uvidíte, že máte spuštěné dva kontejnery aplikací. Nejedná se ale o skutečnou indikaci, že se seskupují do jedné aplikace. Dozvíte se, jak to lépe udělat!

![Rozšíření Docker zobrazující dva neseskupené kontejnery aplikace](media/vs-multi-container-app.png)

## <a name="recap"></a>Rekapitulace

V tuto chvíli máte aplikaci, která teď ukládá svá data do externí databáze běžící v samostatném kontejneru. Dozvěděli jste se trochu o sítích s kontejnery a viděli, jak se dá zjišťování služby provádět pomocí DNS.

Je ale velmi pravděpodobné, že začínáte trochu zahlcením všeho, co potřebujete ke spuštění této aplikace. Musíte vytvořit síť, spouštěcí kontejnery, zadat všechny proměnné prostředí, zveřejnit porty a další. To je velké množství informací, které si zapamatujeme a je to docela těžké předat někomu jinému.

V další části budeme mluvit o Docker Compose. Pomocí Docker Compose můžete své zásobníky aplikací sdílet mnohem jednodušším způsobem a umožnit ostatním jejich otočení pomocí jediného (a jednoduchého) příkazu!

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Použití Docker Compose](use-docker-compose.md)
