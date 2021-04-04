---
title: 'Kurz Docker – část 7: použití Docker Compose'
description: Popisuje, jak nainstalovat a používat Docker Compose.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 3bcf3a69dcf8053851e3d8519a25f61fe23ae7e3
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082562"
---
# <a name="use-docker-compose"></a>Použití Docker Compose

[Docker Compose](https://docs.docker.com/compose/) je nástroj, který byl vyvinutý tak, aby pomohla definovat a sdílet aplikace s více kontejnery. Pomocí nástroje pro psaní můžete vytvořit soubor YAML, který bude definovat služby a jediným příkazem, může vše úplně snížit nebo odtrhnout.

*Velkou* výhodou použití psaní je, že můžete v souboru definovat zásobník aplikace, ponechat ho v kořenu úložiště projektu (je teď řízený verzí) a snadno někomu jinému přispívat k vašemu projektu. Někdo by musel klonovat úložiště a spustit aplikaci pro vytváření. Ve skutečnosti se může stát, že na GitHubu nebo v GitLab se přesně zobrazuje několik projektů.

Jak můžete začít?

## <a name="install-docker-compose"></a>Nainstalovat Docker Compose

Pokud jste nainstalovali Docker Desktop pro Windows nebo Mac, už máte Docker Compose! Instance Play-with-Docker již mají nainstalované Docker Compose. Pokud používáte počítač se systémem Linux, budete ho muset nainstalovat Docker Compose podle [pokynů zde](https://docs.docker.com/compose/install/).

Po dokončení instalace byste měli být schopni spustit následující příkaz a zobrazit informace o verzi.

```bash
docker-compose version
```

## <a name="create-the-compose-file"></a>Vytvořit soubor s psaním

1. V kořenu projektu aplikace vytvořte soubor s názvem `docker-compose.yml` .

1. V souboru pro vytváření Začněte tím, že definujete verzi schématu. Ve většině případů je nejlepší použít nejnovější podporovanou verzi. Můžete se podívat na [odkaz na soubor pro sestavení](https://docs.docker.com/compose/compose-file/) pro aktuální verze schématu a na matici kompatibility.

    ```yaml
    version: "3.7"
    ```

1. Dále Definujte seznam služeb (nebo kontejnerů), které chcete spustit jako součást vaší aplikace.

    ```yaml hl_lines="3"
    version: "3.7"

    services:
    ```

A teď začnete migrovat službu současně do souboru pro vytváření.

## <a name="define-the-app-service"></a>Definovat App Service

Zapamatujte si, že se jednalo o příkaz, který jste použili k definování kontejneru aplikace (nahraďte ` \ ` znaky `` ` `` ve Windows PowerShellu).

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

1. Nejprve definujte položku služby a obrázek kontejneru. Můžete si vybrat libovolný název služby. Název se automaticky stane aliasem sítě, který bude užitečný při definování služby MySQL.

    ```yaml hl_lines="4 5"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
    ```

1. Obvykle se zobrazí příkaz blízko `image` definice, i když neexistují žádné požadavky na řazení. Pokračujte a přesuňte ho do souboru.

    ```yaml hl_lines="6"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
    ```

1. Migrujte `-p 3000:3000` část příkazu tak, že definujete `ports` pro službu. Sem použijete [krátkou syntaxi](https://docs.docker.com/compose/compose-file/#short-syntax-1) , ale zároveň je k dispozici také podrobná [dlouhá syntaxe](https://docs.docker.com/compose/compose-file/#long-syntax-1) .

    ```yaml hl_lines="7 8"
    version: "3.7"

    services:
      app:
        image: node:12-alpine
        command: sh -c "yarn install && yarn run dev"
        ports:
          - 3000:3000
    ```

1. Dále migrujte pracovní adresář ( `-w /app` ) i mapování svazků ( `-v ${PWD}:/app` ) pomocí `working_dir` `volumes` definic a. Svazky mají také [krátkou](https://docs.docker.com/compose/compose-file/#short-syntax-3) a [dlouhou](https://docs.docker.com/compose/compose-file/#long-syntax-3) syntaxi.

   Jednou z výhod Docker Composech definicí svazků je, že můžete použít relativní cesty z aktuálního adresáře.

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

1. Nakonec migrujte definice proměnných prostředí pomocí `environment` klíče.

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

Nyní je čas definovat službu MySQL. Příkaz, který jste použili pro tento kontejner, byl následující (nahraďte ` \ ` znaky `` ` `` ve Windows PowerShellu):

```bash
docker run -d \
  --network todo-app --network-alias mysql \
  -v todo-mysql-data:/var/lib/mysql \
  -e MYSQL_ROOT_PASSWORD=secret \
  -e MYSQL_DATABASE=todos \
  mysql:5.7
```

1. Nejdřív Definujte novou službu a pojmenujte ji `mysql` tak, aby automaticky dostala alias sítě. Zadejte také obrázek, který se má použít.

    ```yaml hl_lines="6 7"
    version: "3.7"

    services:
      app:
        # The app service definition
      mysql:
        image: mysql:5.7
    ```

1. Dále Definujte mapování svazků. Po spuštění kontejneru s nástrojem `docker run` byl vytvořen pojmenovaný svazek automaticky. To se ale nestane při spuštění s vytvářením. Svazek musíte definovat v části nejvyšší úrovně `volumes:` a pak v konfiguraci služby zadat přípojný bod. Pouhým zadáním jenom názvu svazku se použijí výchozí možnosti. [K dispozici je mnoho dalších možností](https://github.com/compose-spec/compose-spec/blob/master/spec.md#volumes-top-level-element) , ale.

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

1. Nakonec stačí zadat jenom proměnné prostředí.

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

V tomto okamžiku `docker-compose.yml` by to mělo vypadat takto:

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

## <a name="run-the-application-stack"></a>Spuštění aplikačního zásobníku

Teď, když máte `docker-compose.yml` soubor, můžete ho spustit.

1. Nejdřív se ujistěte, že nejsou spuštěné žádné jiné kopie aplikace a databáze ( `docker ps` a `docker rm -f <ids>` ).

1. Spusťte zásobník aplikace pomocí `docker-compose up` příkazu. Přidejte `-d` příznak, který spustí vše na pozadí. Případně můžete kliknout pravým tlačítkem myši na soubor s psaním a vybrat možnost **vytvořit** pro postranní panel vs Code. 

    ```bash
    docker-compose up -d
    ```

    Když to spustíte, měl by se zobrazit výstup podobný tomuto:

    ```plaintext
    Creating network "app_default" with the default driver
    Creating volume "app_todo-mysql-data" with default driver
    Creating app_app_1   ... done
    Creating app_mysql_1 ... done
    ```

    Všimnete si, že byl vytvořen svazek i síť. Ve výchozím nastavení Docker Compose automaticky vytvoří síť specificky pro sadu aplikací (což je důvod, proč jste ji nedefinovali v souboru pro vytváření).

1. Podívejte se na protokoly pomocí `docker-compose logs -f` příkazu. Zobrazí se protokoly z každé ze služeb, které se pronechají v jednom datovém proudu. To je neuvěřitelně užitečné, pokud chcete sledovat problémy související s časováním. `-f`Příznak "dodržuje" protokol, takže vám poskytne živý výstup, jak je vygenerován.

    Pokud ještě nemáte, zobrazí se výstup, který vypadá takto:

    ```plaintext
    mysql_1  | 2019-10-03T03:07:16.083639Z 0 [Note] mysqld: ready for connections.
    mysql_1  | Version: '5.7.27'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL Community Server (GPL)
    app_1    | Connected to mysql db at host mysql
    app_1    | Listening on port 3000
    ```

    Název služby se zobrazí na začátku řádku (často se jedná o barevný), aby bylo možné lépe odlišit zprávy. Pokud chcete zobrazit protokoly pro konkrétní službu, můžete přidat název služby na konec příkazu Logs (například `docker-compose logs -f app` ).

    > [!TIP]
    > **Čekání na databázi před spuštěním aplikace** Po spuštění aplikace se ve skutečnosti nachází a čeká se, až bude MySQL připraven a připravený, než se pokusíte připojit k it.Doc, nemá žádnou integrovanou podporu pro čekání na úplné, spuštěné a připravené další kontejnery před spuštěním jiného kontejneru. U projektů založených na uzlech můžete použít závislost na [portu čekání](https://github.com/dwmkerr/wait-port) . Podobné projekty existují pro jiné jazyky nebo architektury.

1. V tuto chvíli byste měli být schopni otevřít svou aplikaci a zobrazit její běh. A Ahoj! Nejste k disřádku na jeden příkaz!

## <a name="see-the-app-stack-in-the-docker-extension"></a>Zobrazit zásobník aplikace v rozšíření Docker

Pokud se podíváte na rozšíření Docker, můžete změnit možnosti seskupení pomocí ' ozubeného kola ' a ' Group by '. V této instanci si přejete zobrazit kontejnery seskupené podle názvu projektu sestavení:

![Rozšíření VS s psaním](media/vs-app-project-collapsed.png)

Pokud zaškrtnete síť, zobrazí se dva kontejnery, které jste definovali v souboru pro psaní.

![Rozšíření VS s rozbaleným sestavením](media/vs-app-project-expanded.png)

## <a name="tear-it-all-down"></a>Vytrhnout vše dolů

Až budete připraveni ho vytrhnout, stačí spustit `docker-compose down` nebo kliknout pravým tlačítkem myši na aplikaci v seznamu kontejnery v rozšíření vs Code Docker a vybrat možnost **vytvořit**. Kontejnery se zastaví a síť bude odebrána.

> [!WARNING]
> **Odebírají se svazky** Ve výchozím nastavení se pojmenované svazky ve vašem souboru pro psaní při spuštění neodstraňují `docker-compose down` . Pokud chcete odebrat svazky, budete muset přidat `--volumes` příznak.

Po roztržení můžete přepnout na jiný projekt, spustit `docker-compose up` a připravit se na tento projekt. Opravdu to není mnohem jednodušší.

## <a name="recap"></a>Rekapitulace

V této části jste se dozvěděli o Docker Compose a o tom, jak významně zjednodušuje definování a sdílení aplikací s více službami. Vytvořili jste soubor s psaním pomocí překladu příkazů, které jste používali, do vhodného formátu pro vytváření.

V tuto chvíli začínáte zabalit kurz. Existuje však několik osvědčených postupů, které se týkají vytváření imagí, protože existuje velký problém s souboru Dockerfile, které jste používali. Pojďme si to udělat!

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Osvědčené postupy při vytváření imagí](image-building-best-practices.md)
