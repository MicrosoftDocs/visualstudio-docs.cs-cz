---
title: 'Kurz Docker – část 2: aktualizace aplikace'
description: Popisuje, jak aktualizovat aplikaci Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: df2102c38250aa5c1bda52b4324cba808501db3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841741"
---
# <a name="update-the-app"></a>Aktualizace aplikace

Jako malý požadavek na funkci jste požádali o změnu prázdného textu, pokud nemáte žádné položky seznamu úkolů. Budou chtít přejít na následující:

> Ještě nemáte žádné položky ToDo. Přidejte ho výše.

Hodně jednoduché, vpravo? Pojďme udělat změnu.

## <a name="update-the-source-code"></a>Aktualizace zdrojového kódu

1. V `src/static/js/app.js` souboru aktualizujte řádek 56 na použití nového prázdného textu.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Sestavte aktualizovanou verzi Image pomocí stejného příkazu, který jste použili dříve.

    ```bash
    docker build -t getting-started .
    ```

1. Spusťte nový kontejner pomocí aktualizovaného kódu.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Uh – Oh!** Pravděpodobně jste viděli chybu (ID se budou lišit):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Co se stalo? Nový kontejner se nepovedlo spustit, protože váš starý kontejner pořád běží. Důvodem je problém, protože tento kontejner používá port hostitele 3000 a pouze jeden proces na počítači (zahrnuté kontejnery) může naslouchat konkrétnímu portu. Chcete-li tento problém vyřešit, odeberte starý kontejner.

## <a name="replace-the-old-container"></a>Nahradit starý kontejner

Chcete-li odebrat kontejner, je nutné nejprve zastavit. Po jeho zastavení je možné ho odebrat. Starý kontejner můžete odebrat dvěma způsoby. Nebojte se zvolit cestu, se kterou jste nejvíc spokojeni.

### <a name="remove-a-container-using-the-cli"></a>Odebrání kontejneru pomocí rozhraní příkazového řádku

1. Získejte ID kontejneru pomocí `docker ps` příkazu.

    ```bash
    docker ps
    ```

1. Pomocí `docker stop` příkazu zastavte kontejner.

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Jakmile se kontejner zastaví, můžete ho odebrat pomocí `docker rm` příkazu.

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Kontejner můžete zastavit a odebrat jediným příkazem přidáním příznaku "vynutit" do `docker rm` příkazu. Příklad: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Odebrání kontejneru pomocí zobrazení Docker

Pokud otevřete rozšíření VS Code, můžete kontejner odebrat dvěma kliknutími! Je to mnohem jednodušší než při hledání ID kontejneru a jeho odebrání.

1. Po otevření rozšíření přejděte do kontejneru a klikněte pravým tlačítkem myši.

1. Klikněte na možnost **Odebrat** .

1. Potvrďte odebrání a Vy jste hotovi!

![Zobrazení Docker – odebrání kontejneru](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Spuštění aktualizovaného kontejneru aplikace

1. Nyní spusťte aktualizovanou aplikaci.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aktualizujte si prohlížeč v [http://localhost:3000](http://localhost:3000) a měli byste vidět aktualizovaný text v nápovědě!

![Aktualizovaná aplikace s aktualizovaným prázdným textem](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Rekapitulace

I když jste si mohli vytvořit aktualizaci, zjistili jsme dvě věci, které jste si všimli:

- Všechny existující položky ve vašem seznamu TODO se odešlou! To není velmi dobrá aplikace! Budeme s tím brzy mluvit.
- Došlo k *velkému množství* kroků týkajících se takových malých změn. V nadcházející části se dozvíte, jak zobrazit aktualizace kódu bez nutnosti opětovného sestavení a spuštění nového kontejneru pokaždé, když provedete změnu.

Než se dozvíte o persistenci, rychle zjistíte, jak tyto image sdílet s ostatními.

## <a name="next-steps"></a>Další kroky

Pokračujte v tomto kurzu.

> [!div class="nextstepaction"]
> [Sdílení aplikace](share-your-app.md)
