---
title: 'Kurz Docker – část 8: vrstvení imagí'
description: Jak kontrolovat a spravovat vrstvy imagí v Docker imagí
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 8913c558c2860599fbfaaba03fa466d11931a528
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837954"
---
# <a name="image-layering"></a>Vrstvení obrázků

Věděli jste, že se můžete podívat na to, co tvoří obrázek? Pomocí `docker image history` příkazu můžete zobrazit příkaz, který byl použit k vytvoření jednotlivých vrstev v rámci obrázku.

1. Pomocí `docker image history` příkazu Zobrazte vrstvy v `getting-started` imagi, kterou jste vytvořili dříve v tomto kurzu.

    ```bash
    docker image history getting-started
    ```

    Měli byste získat výstup, který vypadá nějak takto (data nebo ID se můžou lišit).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Jednotlivé řádky představují vrstvu v obrázku. Tady se zobrazí základ v dolní části s nejnovější vrstvou v horní části. Díky tomu můžete také rychle zobrazit velikost jednotlivých vrstev, což pomáhá diagnostikovat velké obrázky.

1. Všimněte si, že několik řádků je zkráceno. Pokud přidáte `--no-trunc` příznak, získáte úplný výstup (Ano, použijete zkrácený příznak k získání nezkráceného výstupu).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Ukládání vrstev do mezipaměti

Teď, když jste viděli vrstvení v akci, je důležité, abyste se seznámili s tím, jak se dozvíte, jak zkrátit časy sestavení pro Image kontejnerů.

> Po změně vrstvy je nutné znovu vytvořit všechny podřízené vrstvy.

Pojďme se podívat na souboru Dockerfile, který jste použili ještě jednou...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Když se vrátíte zpátky na výstup historie imagí, uvidíte, že každý příkaz v souboru Dockerfile se v imagi bude zobrazovat jako nová vrstva. Můžete si uvědomit, že když jste provedli změnu v imagi, museli jste přeinstalovat závislosti příze. Existuje způsob, jak tento problém vyřešit? Nezáleží na tom, jak dodávat stejné závislosti pokaždé, když sestavíte, hned?

Chcete-li tento problém vyřešit, můžete změnit strukturu souboru Dockerfile tak, aby podporovala ukládání závislostí do mezipaměti. Pro aplikace založené na uzlech jsou tyto závislosti definovány v `package.json` souboru. Takže pokud jste nejdřív zkopírovali jenom tento soubor, nainstalujte závislosti a *pak* ho zkopírujte do všech ostatních? Pak znovu vytvořte pouze závislosti příze, pokud došlo ke změně `package.json` . Chcete dělat smysl?

1. Aktualizujte souboru Dockerfile tak, aby se zkopírovaly jako `package.json` první, nainstalujte závislosti a potom zkopírujte všechno ostatní v.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Sestavte novou image pomocí `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Měl by se zobrazit výstup podobný tomuto...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Uvidíte, že se všechny vrstvy znovu sestavily. Dokonale jemný, protože jste souboru Dockerfile trochu změnili.

1. Nyní provedete změnu v `src/static/index.html` souboru (například změňte `<title>` "na" aplikaci Super TODO ").

1. Sestavte image Docker a `docker build` znovu ji použijte. V tuto chvíli by měl výstup vypadat trochu jinak.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    Nejprve byste si měli všimnout, že sestavení bylo mnohem rychlejší. A uvidíte, že všechny kroky 1-4 `Using cache` . Radostných! Používáte mezipaměť sestavení. Vložení a odeslání tohoto obrázku a aktualizace na něj budou mnohem rychlejší. Radostných!

## <a name="multi-stage-builds"></a>Sestavení s více fázemi

I když nebudeme v tomto kurzu podrobně příliš mnoho, sestavení s více fázemi jsou neuvěřitelně výkonným nástrojem, který usnadňuje vytvoření Image pomocí několika fází. Pro ně je k dispozici několik výhod:

- Samostatné závislosti v době sestavování ze závislostí modulu runtime
- Zmenšete celkovou velikost obrazu tím, že dodáváte *jenom* to, co vaše aplikace potřebuje ke spuštění.

### <a name="maventomcat-example"></a>Příklad Maven/Tomcat

Při sestavování aplikací založených na jazyce Java je potřeba JDK ke kompilaci zdrojového kódu do bytového kódu Java. Tento JDK ale není potřeba v produkčním prostředí. K sestavení aplikace můžete také využít nástroje, jako je Maven nebo Gradle.
Ty nejsou také potřeba v konečné imagi. Podpora sestavení s více fázemi.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

Tento příklad používá jednu fázi (volanou `build` ) k provedení skutečného sestavení Java pomocí Maven. Druhá fáze (počínaje verzí `FROM tomcat` ) kopíruje soubory ze `build` fáze. Finální obrázek je pouze poslední vytvořenou fází (kterou lze přepsat pomocí `--target` příznaku).

### <a name="react-example"></a>Příklad reakce

Při sestavování reagujících aplikací potřebujete prostředí uzlů pro zkompilování kódu JS (obvykle JSX), SASS stylů a dalších do statických HTML, JS a CSS. Pokud neprovádíte vykreslování na straně serveru, nemusíte ani prostředí uzlů pro produkční sestavení. Proč se statické prostředky nedávají do statického kontejneru Nginx?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Tady se používá `node:12` Image k provedení sestavení (maximalizace ukládání do mezipaměti) a následného zkopírování výstupu do kontejneru Nginx. Studeno, huh?

## <a name="recap"></a>Rekapitulace

Když pochopíte, jak jsou image strukturované, můžete vytvářet image rychleji a dodávat méně změn. Víceprocesorové buildy také pomůžou snížit celkovou velikost obrázků a zvýšit konečné zabezpečení kontejneru tím, že oddělí závislosti doby sestavení od závislostí modulu runtime.

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Nasazení do cloudu](deploy-to-cloud.md)