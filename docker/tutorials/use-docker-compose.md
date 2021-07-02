---
title: 'Kurz Dockeru – 7. část: Použití Docker Compose'
description: Popisuje, jak nainstalovat a používat Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 645d168aefe05040193d564d5c158acfb6688c11
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222744"
---
# <a name="use-docker-compose"></a>Použití Docker Compose

[Docker Compose](https://docs.docker.com/compose/) je nástroj, který byl vytvořen tak, aby vám pomohl definovat a sdílet více kontejnerové aplikace. Pomocí nástroje Compose můžete vytvořit soubor YAML, který definuje služby, a jediným příkazem můžete všechno zkompilovat nebo všechno zmátnout.

Hlavní *výhodou* použití funkce Compose je, že můžete definovat zásobník aplikace v souboru, ponechat ho v kořenovém adresáři vašeho projektového repo (teď je řízený verzí) a snadno umožnit, aby do vašeho projektu přispěl někdo jiný. Někdo by potřeboval jenom naklonovat vaše repo a spustit aplikaci pro psaní. Ve skutečnosti můžete vidět poměrně hodně projektů na GitHub/GitLabu, které to dělají právě teď.

Jak tedy začít?

## <a name="install-docker-compose"></a>Instalace Docker Compose

Pokud jste nainstalovali Docker Desktop pro Windows nebo Mac, máte už Docker Compose! Instance Dockeru už Docker Compose nainstalované. Pokud jste na počítači s Linuxem, budete si muset nainstalovat Docker Compose podle [těchto pokynů.](https://docs.docker.com/compose/install/)

Po instalaci byste měli být schopni spustit následující příkaz a zobrazit informace o verzi.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Vytvoření souboru pro psaní

1. V kořenovém adresáři projektu aplikace vytvořte soubor s názvem `docker-compose.yml` .

1. V souboru compose začneme definováním verze schématu. Ve většině případů je nejlepší použít nejnovější podporovanou verzi. Aktuální verze schématu a matici kompatibility najdete v referenčních odkazech na soubor [Compose.](https://docs.docker.com/compose/compose-file/)

    ```yaml
    version: "3.7"
    ```

1. Dále definujte seznam služeb (nebo kontejnerů), které chcete spustit jako součást vaší aplikace.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

Teď začnete službu migrovat do souboru compose.

## <a name="define-the-app-service"></a>Definování App Service

Připomeňme si, že se jedná o příkaz, který jste použili k definování kontejneru aplikace (nahraďte ` \ ` znaky v `` ` `` Windows PowerShell).

```bash
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

1. Nejprve definujte položku služby a image kontejneru. Pro službu můžete vybrat libovolný název. Název se automaticky stane aliasem sítě, který bude užitečný při definování služby MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Obvykle se příkaz zobrazí blízko definice, i když není při `image` řazení potřeba. Pokračujte a přesuňte ho do souboru .

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Část `-p 3000:3000` příkazu migrujte definováním `ports` pro službu . Tady použijete [krátkou syntaxi,](https://docs.docker.com/compose/compose-file/#short-syntax-1) ale k dispozici je také podrobnější dlouhá [syntaxe.](https://docs.docker.com/compose/compose-file/#long-syntax-1)

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Dále migrujte pomocí definic a jak pracovní adresář ( ), tak mapování `-w /app` svazku ( `-v ${PWD}:/app` `working_dir` `volumes` ). Svazky mají také [krátkou](https://docs.docker.com/compose/compose-file/#short-syntax-3) a [dlouhou](https://docs.docker.com/compose/compose-file/#long-syntax-3) syntaxi.

   Jednou z výhod Docker Compose svazků je, že můžete použít relativní cesty z aktuálního adresáře.

    ```yaml hl_lines="9 10 11"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
    ```

1. Nakonec pomocí klíče migrujte definice proměnných `environment` prostředí.

    ```yaml hl_lines="12 13 14 15 16"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
        working_dir: /app
        volumes:
          - ./:/app
        environment:
          MYSQL_HOST: mysql
          MYSQL_USER: root
          MYSQL_PASSWORD: secret
          MYSQL_DB: todos
    ```

### <a name="define-the-mysql-service"></a>Definování služby MySQL

Teď je čas definovat službu MySQL. Příkaz, který jste použili pro tento kontejner, byl následující (nahraďte ` \ ` znaky v `` ` `` souboru Windows PowerShell):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Nejprve definujte novou službu a pojmnujte ji, aby automaticky získá `mysql` alias sítě. Zadejte také image, která se má použít.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Dále definujte mapování svazků. Když jste kontejner spustili s `docker run` , pojmenovaný svazek se vytvořil automaticky. To se ale při spuštění s aplikací Compose nestane. Svazek je potřeba definovat v části nejvyšší úrovně a pak zadat `volumes:` přípojný bod v konfiguraci služby. Když jednoduše zadáte jenom název svazku, použije se výchozí možnosti. K dispozici [je ale mnoho dalších](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) možností.

    ```yaml hl_lines="8 9 10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
    
    volumes:
      todo-mysql-data:
    ```

1. Nakonec je potřeba zadat pouze proměnné prostředí.

    ```yaml hl_lines="10 11 12"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
        volumes:
          - todo-mysql-data:/var/lib/mysql
        environment: 
          MYSQL_ROOT_PASSWORD: secret
          MYSQL_DATABASE: todos
    
    volumes:
      todo-mysql-data:
    ```

V tuto chvíli by mělo dokončení `docker-compose.yml` vypadat takhle:

```yaml
version: "3.7"

services:
  app:
    image: node:12-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:5.7
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment: 
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

## <a name="run-the-application-stack"></a>Spuštění zásobníku aplikací

Teď, když máte `docker-compose.yml` soubor, ho můžete spustit.

1. Nejprve se ujistěte, že nejsou spuštěné žádné další kopie aplikace a databáze ( `docker ps` a `docker rm -f <ids>` ).

1. Spusťte zásobník aplikací pomocí `docker-compose up` příkazu . Přidejte `-d` příznak , který spustí všechno na pozadí. Případně můžete kliknout pravým tlačítkem na soubor  Compose a vybrat možnost Vytvořit na bočním VS Code panelu. 

    ```bash
    docker-compose up -d
    ```

    Po spuštění tohoto příkazu by se měl zobrazit výstup, jako je tento:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Všimněte si, že se svazek vytvořil i síť. Ve výchozím Docker Compose automaticky vytvoří síť specificky pro zásobník aplikací (proto jste ji v souboru pro psaní nedefinujte).

1. Prohlédněte si protokoly pomocí `docker-compose logs -f` příkazu . Uvidíte protokoly z jednotlivých služeb prokládané do jednoho datového proudu. To je neuvěřitelně užitečné, když chcete sledovat problémy související s časování. Příznak `-f` "sleduje" protokol, takže vám poskytne živý výstup při generování.

    Pokud to ještě nemáte, zobrazí se výstup, který vypadá jako tento:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Název služby se zobrazí na začátku řádku (často barevné), aby se zprávy rozlišují. Pokud chcete zobrazit protokoly pro konkrétní službu, můžete přidat název služby na konec příkazu logs (například `docker-compose logs -f app` ).

    > [!TIP]
    > **Čekání na databázi před spuštěním aplikace** Když se aplikace spouští, ve skutečnosti je v provozu a čeká, až bude MySQL připravený, než se zkusí připojit k it.Docker nemá žádnou integrovanou podporu, která by před spuštěním dalšího kontejneru čekala na úplné zsídky, spuštění a připravení dalšího kontejneru. Pro projekty založené na node můžete použít závislost [wait-port.](https://github.com/dwmkerr/wait-port) Podobné projekty existují i pro jiné jazyky nebo architektury.

1. V tuto chvíli byste měli být schopni otevřít aplikaci a vidět ji spuštěnou. A nazýtá se! Máte k dispozici jediný příkaz!

## <a name="see-the-app-stack-in-the-docker-extension"></a>Zobrazení zásobníku aplikací v rozšíření Dockeru

Pokud se podíváte na rozšíření Dockeru, můžete změnit možnosti seskupení pomocí skupin "cog" a "seskupit podle". V tomto případě chcete zobrazit kontejnery seskupené podle názvu Project:

![Rozšíření VS s compose](media/vs-app-project-collapsed.png)

Pokud síť twirl down, uvidíte dva kontejnery, které jste definovali v souboru compose.

![Rozšíření VS s rozbalenou příponou Compose](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Ztržení všech konců

Až budete připravení vše ztrhnout, jednoduše spusťte nebo klikněte pravým tlačítkem na aplikaci v seznamu kontejnerů v rozšíření dockeru VS Code a vyberte `docker-compose down` **Compose Down**(Sestavit dolů). Kontejnery se zastaví a síť se odebere.

> [!WARNING]
> **Odebrání svazků** Ve výchozím nastavení nejsou pojmenované svazky v souboru pro psaní při spuštění `docker-compose down` odebrány. Pokud chcete svazky odebrat, budete muset přidat příznak `--volumes` .

Po roztrhnout můžete přepnout na jiný projekt, spustit a být připraveni `docker-compose up` k přispívání do tohoto projektu. Ve skutečnosti to není o moc jednodušší!

## <a name="recap"></a>Rekapitulace

V této části jste se dozvěděli o Docker Compose a o tom, jak výrazně zjednodušuje definování a sdílení aplikací s více službami. Soubor Compose jste vytvořili překladem příkazů, které jste měli, do vhodného formátu pro psaní.

V tuto chvíli tento kurz začínáte sbalovat. Existuje však několik osvědčených postupů pro sestavení image, které je třeba pokrýt, protože u souboru Dockerfile, který používáte, existuje velký problém. Pojďme se na to podívat!

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Osvědčené postupy pro vytváření obrázků](image-building-best-practices.md)
