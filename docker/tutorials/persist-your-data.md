---
title: 'Kurz Docker – část 4: uchování dat'
description: Naučte se uchovávat data v databázi a sdílet adresáře do kontejneru připojením svazku.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: c9408e099caaef097be3fc4eea26cee2b1889e8e
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222900"
---
# <a name="persist-your-data"></a>Uchování dat

V případě, že jste si nevšimli, vymaže se seznam TODO při každém spuštění kontejneru. Proč je to? Pojďme se podrobně na to, jak kontejner funguje.

## <a name="the-containers-filesystem"></a>Systém souborů kontejneru

Při spuštění kontejneru používá různé vrstvy z image pro svůj systém souborů. Každý kontejner také získá vlastní "pomocné místo" pro vytváření, aktualizaci nebo odebírání souborů. Jakékoli změny se neprojeví v jiném kontejneru, *i* když používají stejnou image.

### <a name="see-this-in-practice"></a>Projděte si toto v praxi.

Pokud to chcete vidět v akci, budete moct začít vytvářet dva kontejnery a v každém z nich vytvořit soubor. Uvidíte, že soubory vytvořené v jednom kontejneru nejsou k dispozici v jiném.

1. Spusťte `ubuntu` kontejner, který vytvoří soubor `/data.txt` s náhodným číslem v rozmezí 1 až 10000.

    ```bash
    docker run -d ubuntu bash -c "shuf -i 1-10000 -n 1 -o /data.txt && tail -f /dev/null"
    ```

    V případě, že jste zajímái o příkazu, spouštíte prostředí bash a vyvolali jste dva příkazy (proč má `&&` ). První část vybere jedno náhodné číslo a zapíše ho do `/data.txt` . Druhý příkaz jednoduše sleduje soubor, aby se zajistilo, že je kontejner spuštěný.

1. Ověření: výstup můžete zobrazit pomocí `exec` , abyste se dostali do kontejneru. provedete to tak, že otevřete rozšíření VS Code a kliknete na možnost **připojit prostředí** . tato akce slouží `exec` k otevření prostředí v kontejneru v rámci VS Code terminálu.

    ![VS Code otevřít CLI do kontejneru ubuntu](media/attach_shell.png)

    V kontejneru Ubuntu se zobrazí terminál, na kterém běží prostředí. Spusťte následující příkaz, který zobrazí obsah `/data.txt` souboru. Zavřete tento terminál později.

    ```bash
    cat /data.txt
    ```

    Pokud dáváte přednost příkazovému řádku, můžete `docker exec` k tomu použít příkaz. Musíte získat ID kontejneru (použít `docker ps` ho k získání) a získat obsah pomocí následujícího příkazu.

    ```bash
    docker exec <container-id> cat /data.txt
    ```

    Mělo by se zobrazit náhodné číslo.

1. Nyní spusťte jiný `ubuntu` kontejner (stejný obrázek) a uvidíte, že nemáte stejný soubor.

    ```bash
    docker run -it ubuntu ls /
    ```

    A hledejte! K dispozici není žádný `data.txt` soubor. To je proto, že byl zapsán do pomocné paměti pouze pro první kontejner.

1. Pokračujte a odeberte první kontejner pomocí `docker rm -f` příkazu.

## <a name="container-volumes"></a>Svazky kontejneru

S předchozím experimentem jste zjistili, že každý kontejner začíná při každém spuštění z definice image. I když kontejnery můžou vytvářet, aktualizovat a odstraňovat soubory, tyto změny se ztratí při odebrání kontejneru a všechny změny jsou izolované do tohoto kontejneru. Se svazky můžete změnit vše.

[Svazky](https://docs.docker.com/storage/volumes/) poskytují možnost spojit konkrétní cesty systému souborů kontejneru zpátky s hostitelským počítačem. Pokud je adresář v kontejneru připojen, změny v tomto adresáři jsou také zobrazeny na hostitelském počítači. Pokud připojíte stejný adresář mezi restartováním kontejneru, zobrazí se stejné soubory.

Existují dva hlavní typy svazků. nakonec použijete obojí, ale začnete s **pojmenovanými svazky**.

## <a name="persist-your-todo-data"></a>Uchování dat todo

Ve výchozím nastavení aplikace TODO ukládá svá data do [databáze SQLite](https://www.sqlite.org/index.html) na adrese `/etc/todos/todo.db` . Pokud nejste obeznámeni s SQLite, žádné obavy! Je to jednoduše relační databáze, ve které jsou všechna data uložená v jednom souboru. I když to není pro velké aplikace nejlepší, funguje to pro malé ukázky. Budeme mluvit o tom, jak toto přepínat na skutečný databázový stroj později.

Pokud se databáze nachází v jediném souboru, může se stát, že pokud tento soubor na hostiteli uložíte a zpřístupníte ho dalšímu kontejneru, měla by být schopná si vybrat, kde poslední z nich skončila. Vytvořením svazku a připojením (často nazývaného "připojení") do adresáře, ve kterém jsou uložena data, můžete zachovat data. V případě, že kontejner zapisuje do `todo.db` souboru, je trvalý pro hostitele ve svazku.

Jak už jsme uvedli, budete používat **pojmenovaný svazek**. Pojmenovaný svazek si můžete představit jako jednoduše jako datovým kontejnerem. Docker udržuje fyzické umístění na disku a stačí si pamatovat jenom název svazku. Pokaždé, když použijete svazek, Docker zajistí, že jsou k dispozici správná data.

1. Pomocí příkazu vytvořte svazek `docker volume create` .

    ```bash
    docker volume create todo-db
    ```

1. Znovu zastavte kontejner aplikace TODO v zobrazení Docker (nebo s `docker rm -f <id>` ), protože je stále spuštěn bez použití trvalého svazku.

1. Spusťte kontejner aplikace todo, ale přidejte `-v` příznak pro určení připojení svazku. použijete pojmenovaný svazek a připojíte ho ke službě `/etc/todos` , která bude zachytit všechny soubory vytvořené v cestě.

    ```bash
    docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
    ```

1. Po spuštění kontejneru otevřete aplikaci a přidejte do seznamu úkolů několik položek.

    ![Položky přidané do seznamu TODO](media/items-added.png)

1. Odeberte kontejner pro aplikaci todo. Pomocí zobrazení Docker nebo `docker ps` Získejte ID a pak `docker rm -f <id>` ho odeberte.

1. Spusťte nový kontejner pomocí stejného příkazu uvedeného výše.

1. Spusťte aplikaci. Měli byste vidět, že vaše položky jsou pořád v seznamu.

1. Až budete hotovi, Projděte si kontejner a odeberte ho.

Radostných! Nyní jste se naučili, jak uchovávat data!

> [!TIP]
> I když se pojmenované svazky a připojení k vazbě (které budeme mluvit za minutu), jsou dva hlavní typy svazků, které podporuje výchozí instalace modulu Docker, k dispozici je mnoho modulů plug-in ovladačů svazků pro podporu systému souborů NFS, SFTP, NetApp a dalších. To bude obzvláště důležité, když začnete spouštět kontejnery na více hostitelích v clusterovém prostředí s Swarm, Kubernetes a tak dále.

## <a name="dive-into-your-volume"></a>Podrobně se na svazek

Hodně lidí se často zeptat, kde je při použití pojmenovaného svazku *skutečně* ukládána data do Docker. Chcete-li znát, můžete použít `docker volume inspect` příkaz.

```bash
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/todo-db/_data",
        "Name": "todo-db",
        "Options": {},
        "Scope": "local"
    }
]
```

`Mountpoint`Je skutečné umístění na disku, kde jsou uložena data. Všimněte si, že ve většině počítačů budete muset mít rootový přístup pro přístup k tomuto adresáři z hostitele. Ale na to, kde to je!

> [!NOTE]
> **Přímý přístup k datům o svazcích v Docker desktopu** Při spuštění v Docker desktopu jsou příkazy Docker ve skutečnosti spuštěny v malém VIRTUÁLNÍm počítači v počítači. Pokud se chcete podívat na skutečný obsah adresáře *přípojný bod* , musíte nejdřív začít uvnitř virtuálního počítače. V WSL 2 se jedná o WSL 2 distribuce a dá se k nim dostat prostřednictvím Průzkumníka souborů.

## <a name="recap"></a>Rekapitulace

V tomto okamžiku máte funkční aplikaci, která může zamezit restartování. Můžete je zobrazit pro vaše investory a doufáme, že si vaše vize můžou zachytit!

Zjistili jsme si ale, že opakované vytváření imagí pro každou změnu trvá poměrně dlouho. Máte lepší způsob, jak provádět změny, hned? S připojením vazeb, které jsme poznamenali dříve, existuje lepší způsob. Pojďme se podívat, jak teď!

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Použití připojení vazeb](use-bind-mounts.md)
