---
title: 'Kurz Dockeru – 6. část: Více kontejnerové aplikace'
description: Jak nastavit sítě mezi kontejnery a přidat kontejner pro databázi MySQL.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: d23d1f5d94729741630ee76263fd5b32041e9cfd
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222913"
---
# <a name="multi-container-apps"></a>Vícekontejnerové aplikace

Až do této doby jste pracovali s aplikacemi s jedním kontejnerem. Teď ale přidáte MySQL do zásobníku aplikací. Často vyvstává následující otázka: "Kde bude MySQL spuštěný? Nainstalujte ho do stejného kontejneru nebo ho spusťte samostatně?" Obecně platí, **že každý kontejner by měl udělat jednu věc a udělat to dobře.** Několik důvodů:

- Existuje dobrá šance, že budete muset škálovat rozhraní API a front-ends jinak než databáze.
- Samostatné kontejnery umožňují izolovanou verzi verzí a aktualizaci verzí.
- I když můžete použít kontejner pro databázi místně, můžete chtít použít spravovanou službu pro databázi v produkčním prostředí. Nechcete dodát databázový stroj s vaší aplikací.
- Spuštění více procesů bude vyžadovat správce procesů (kontejner spustí jenom jeden proces), což zvyšuje složitost spouštění a vypínání kontejneru.

A existuje více důvodů. Aplikaci tedy aktualizujete tak, aby fungovala takhle:

![Aplikace todo připojená ke kontejneru MySQL](media/multi-app-architecture.png)

## <a name="container-networking"></a>Sítě kontejnerů

Mějte na paměti, že kontejnery ve výchozím nastavení běží izolovaně a neví nic o jiných procesech nebo kontejnerech na stejném počítači. Jak tedy jednomu kontejneru umožníte, aby s jiným mluvil? Odpovědí je **síť**. Teď už nemusíte být síťový inženýr (hooray!). Stačí si toto pravidlo zapamatovat...

> [!NOTE]
> Pokud jsou dva kontejnery ve stejné síti, mohou spolu vzájemně mluvit. Pokud ne, nemůže.

## <a name="start-mysql"></a>Spuštění MySQL

Existují dva způsoby, jak umístit kontejner do sítě: přiřadit ho při spuštění nebo připojit existující kontejner. Teď nejprve vytvoříte síť a při spuštění připojíte kontejner MySQL.

1. Vytvořte síť.

    ```bash
    docker network create todo-app
    ```

1. Spusťte kontejner MySQL a připojte ho k síti. Také definujeme několik proměnných prostředí, které databáze použije k inicializaci databáze (viz část Proměnné prostředí v seznamu Docker Hub [MySQL)](https://hub.docker.com/_/mysql/)(nahraďte znaky v souboru ` \ ` `` ` `` Windows PowerShell).

    ```bash
    docker run -d \
        --network todo-app --network-alias mysql \
        -v todo-mysql-data:/var/lib/mysql \
        -e MYSQL_ROOT_PASSWORD=secret \
        -e MYSQL_DATABASE=todos \
        mysql:5.7
    ```

    Uvidíte také, že jste zadali `--network-alias` příznak . K tomu se vrátíme za chvíli.

    > [!TIP]
    > Všimněte si, že tady používáte název svazku a připojte ho na adrese , kde `todo-mysql-data` `/var/lib/mysql` MySQL ukládá data. Nikdy jste ale nespustili `docker volume create` příkaz . Docker rozpozná, že chcete použít pojmenovaný svazek, a automaticky ho vytvoří za vás.

1. Abyste potvrdili, že máte databázi spuštěnou, připojte se k databázi a ověřte, že se připojuje.

    ```bash
    docker exec -it <mysql-container-id> mysql -p
    ```

    Až se zobrazí výzva k zadání hesla, zadejte tajný **kód**. V prostředí MySQL zobrazte seznam databází a ověřte, že se databáze `todos` zobrazí.

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

    Hurá! Máte svou `todos` databázi a je připravená k použití.

## <a name="connect-to-mysql"></a>Připojení do MySQL

Teď, když víte, že MySQL je v provozu, použijeme ho! Otázkou ale je... Jak? Pokud ve stejné síti spustíte jiný kontejner, jak kontejner najdete (nezapomeňte, že každý kontejner má svou vlastní IP adresu)?

Abyste to zjistili, využijete kontejner [s](https://github.com/nicolaka/netshoot) řešeními s mnoha nástroji, které jsou užitečné při řešení potíží se sítí nebo při ladění problémů se sítí. 

1. Spusťte nový kontejner pomocí `nicolaka/netshoot` image. Nezapomeňte ho připojit ke stejné síti.

    ```bash
    docker run -it --network todo-app nicolaka/netshoot
    ```

1. Uvnitř kontejneru použijte příkaz `dig` , což je užitečný nástroj DNS. Vyhledejte IP adresu pro název hostitele `mysql` .

    ```bash
    dig mysql
    ```

    A získáte výstup, jako je tento...

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

    V části ANSWER SECTION (ODPOVĚĎ) se zobrazí záznam, který se překládá na (vaše IP adresa bude mít `A` `mysql` pravděpodobně jinou `172.23.0.2` hodnotu). Přestože obvykle není platný název hostitele, Docker ho dokázal přeložit na IP adresu kontejneru, který měl tento síťový alias (zapamatovat si příznak, který `mysql` `--network-alias` jste použili dříve).)

    To znamená... Vaše aplikace se stačí jenom připojit k hostiteli s názvem a `mysql` bude mluvit s databází. Není to o moc jednodušší!

## <a name="run-your-app-with-mysql"></a>Spuštění aplikace pomocí MySQL

Aplikace seznamu úkolů podporuje nastavení několika proměnných prostředí a určuje nastavení připojení MySQL. Jsou to tyto:

- `MYSQL_HOST` – název hostitele pro spuštěný server MySQL
- `MYSQL_USER` – uživatelské jméno, které se má použít pro připojení
- `MYSQL_PASSWORD` – heslo, které se má použít pro připojení
- `MYSQL_DB` – databáze, která se má použít po připojení

> [!WARNING]
> **Nastavení připojení Nastavení prostřednictvím proměnných prostředí** Přestože použití proměnných prostředí k nastavení připojení je obecně pro vývoj v pořádku, při spouštění aplikací v produkčním prostředí se důrazně nedoporučuje. Pokud chcete pochopit, proč, [podívejte se na důvody,](https://diogomonica.com/2017/03/27/why-you-shouldnt-use-env-variables-for-secret-data/)proč byste neměli používat proměnné prostředí pro tajná data .
> Bezpečnějším mechanismem je použití podpory tajných klíčů poskytované architekturou orchestrace kontejnerů. Ve většině případů jsou tyto tajné kódy připojené jako soubory ve spuštěném kontejneru. Uvidíte, že mnoho aplikací (včetně image MySQL a aplikace seznamu todo) také podporuje vary env s příponou odkazovat na soubor obsahující `_FILE` soubor.
> Například nastavení var způsobí, že aplikace jako heslo připojení použije `MYSQL_PASSWORD_FILE` obsah odkazovaného souboru. Docker pro podporu těchto vacích nic neudělal. Vaše aplikace bude muset vědět, že má hledat proměnnou a získat obsah souboru.

Všechno, co jsme si vysvětlili, začněte s kontejnerem připraveným pro vývoj.

1. Zadejte všechny výše uvedené proměnné prostředí a připojte kontejner k vaší síti aplikací (nahraďte ` \ ` znaky v `` ` `` souboru Windows PowerShell).

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

1. Pokud se podíváte na protokoly kontejneru ( ), měla by se zobrazit zpráva s oznámením, že se používá `docker logs <container-id>` databáze MySQL.

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

1. Otevřete aplikaci v prohlížeči a přidejte několik položek do seznamu úkolů.

1. Připojení databázi MySQL a prokažte, že se položky zapisovány do databáze. Nezapomeňte, že heslo je **tajné.**

    ```bash
    docker exec -ti <mysql-container-id> mysql -p todos
    ```

    V prostředí MySQL spusťte následující příkaz:

    ```plaintext
    mysql> select * from todo_items;
    +--------------------------------------+--------------------+-----------+
    | id                                   | name               | completed |
    +--------------------------------------+--------------------+-----------+
    | c906ff08-60e6-44e6-8f49-ed56a0853e85 | Do amazing things! |         0 |
    | 2912a79e-8486-4bc3-a4c5-460793a575ab | Be awesome!        |         0 |
    +--------------------------------------+--------------------+-----------+
    ```

    Vaše tabulka bude samozřejmě vypadat jinak, protože obsahuje vaše položky. Ale měli byste je tam vidět uložené!

Pokud se rychle podíváte na rozšíření Docker, uvidíte, že máte spuštěné dva kontejnery aplikací. Neexistuje ale žádná skutečná indikace, že jsou seskupené dohromady v jedné aplikaci. Za chvíli uvidíte, jak to udělat lépe!

![Rozšíření Dockeru zobrazující dva kontejnery aplikací bez seskupení](media/vs-multi-container-app.png)

## <a name="recap"></a>Rekapitulace

V tuto chvíli máte aplikaci, která teď ukládá data do externí databáze spuštěné v samostatném kontejneru. Trochu jste se dozvěděli o sítích kontejnerů a zjistili jste, jak je možné zjišťování služeb provádět pomocí DNS.

Je ale dobrá šance, že se začínáte cítit trochu zahlcený vším, co musíte udělat, abyste tuto aplikaci s aplikací skoncovat. Musíte vytvořit síť, spustit kontejnery, zadat všechny proměnné prostředí, zveřejnit porty a další. Je toho hodně, co si zapamatovat a určitě ztěžuje předání věci někomu jinému.

V další části si promluvme o Docker Compose. Díky Docker Compose můžete sdílet zásobníky aplikací mnohem jednodušším způsobem a nechat ostatní, aby je s jejich pomocí jednoho (a jednoduchého) příkazu roztáhli.

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Pomocí Docker Compose](use-docker-compose.md)
