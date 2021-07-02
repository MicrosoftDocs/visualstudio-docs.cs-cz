---
title: 'Kurz Dockeru – Část 2: Aktualizace aplikace'
description: Popisuje, jak aktualizovat aplikaci Dockeru.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jmartens
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: 43034ff2e65564cc8af2710b796b76996f21f4c8
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222770"
---
# <a name="update-the-app"></a>Aktualizace aplikace

Produktový tým vás požádal, abyste změnili "prázdný text", když nemáte žádné položky seznamu úkolů. Chtějí ho pře přechodu na následující:

> Ještě nemáte žádné položky seznamu todo! Přidejte jeden výše!

Poměrně jednoduché, že? Pojďme udělat změnu.

## <a name="update-the-source-code"></a>Aktualizace zdrojového kódu

1. V souboru `src/static/js/app.js` aktualizujte řádek 56 tak, aby se nový prázdný text.

    ```diff
    -                <p className="text-center">No items yet! Add one above!</p>
    +                <p className="text-center">You have no todo items yet! Add one above!</p>
    ```

1. Sestavte aktualizovanou verzi image pomocí stejného příkazu, který jste použili dříve.

    ```bash
    docker build -t getting-started .
    ```

1. Spusťte nový kontejner pomocí aktualizovaného kódu.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

**Ach,** Pravděpodobně jste viděli chybu, jako je tato (ID se budou lišit):

```bash
docker: Error response from daemon: driver failed programming external connectivity on endpoint laughing_burnell 
(bb242b2ca4d67eba76e79474fb36bb5125708ebdabd7f45c8eaf16caaabde9dd): Bind for 0.0.0.0:3000 failed: port is already allocated.
```

Co se tedy stalo? Nový kontejner se nepokusí spustit, protože starý kontejner je stále spuštěný. Důvodem tohoto problému je to, že kontejner používá port 3000 hostitele a na počítači může naslouchat jenom jeden proces (zahrnuté kontejnery). Pokud chcete tento problém vyřešit, odeberte starý kontejner.

## <a name="replace-the-old-container"></a>Nahrazení starého kontejneru

Pokud chcete kontejner odebrat, je potřeba ho nejprve zastavit. Jakmile se zastaví, můžete ho odebrat. Starý kontejner můžete odebrat dvěma způsoby. Můžete si zvolit cestu, se kterou se vám bude nejpohodlnější.

### <a name="remove-a-container-using-the-cli"></a>Odebrání kontejneru pomocí rozhraní příkazového řádku

1. Získejte ID kontejneru pomocí `docker ps` příkazu .

    ```bash
    docker ps
    ```

1. K `docker stop` zastavení kontejneru použijte příkaz .

    ```bash
    # Swap out <the-container-id> with the ID from docker ps
    docker stop <the-container-id>
    ```

1. Jakmile se kontejner zastaví, můžete ho odebrat pomocí `docker rm` příkazu .

    ```bash
    docker rm <the-container-id>
    ```

> [!TIP]
> Kontejner můžete zastavit a odebrat v jednom příkazu přidáním příznaku force do `docker rm` příkazu. Příklad: `docker rm -f <the-container-id>`

### <a name="remove-a-container-using-the-docker-view"></a>Odebrání kontejneru pomocí zobrazení Dockeru

Pokud otevřete rozšíření VS Code, můžete kontejner odebrat dvěma kliknutími. Je to určitě mnohem jednodušší než vyhledávání ID kontejneru a jeho odebrání.

1. Po otevření rozšíření přejděte do kontejneru a klikněte na něj pravým tlačítkem.

1. Klikněte na **možnost Odebrat.**

1. Potvrďte odebrání a jste hotovi.

![Zobrazení Dockeru – odebrání kontejneru](media/vs-removing-container.png)

### <a name="start-the-updated-app-container"></a>Spuštění aktualizovaného kontejneru aplikace

1. Teď spusťte aktualizovanou aplikaci.

    ```bash
    docker run -dp 3000:3000 getting-started
    ```

1. Aktualizujte prohlížeč na a [http://localhost:3000](http://localhost:3000) měli byste vidět aktualizovaný text nápovědy.

![Aktualizovaná aplikace s aktualizovaným prázdným textem](media/todo-list-updated-empty-text.png)

## <a name="recap"></a>Rekapitulace

I když jste dokázali vytvořit aktualizaci, možná jste si všimli dvou věcí:

- Všechny existující položky v seznamu úkolů jsou pryč. To není moc dobrá aplikace! Za chvíli si o tom promluvme.
- Pro takovou *malou* změnu bylo zapojeno mnoho kroků. V nadcházející části se dozvíte, jak zobrazit aktualizace kódu bez nutnosti opětovného sestavení a spuštění nového kontejneru pokaždé, když něco změníte.

Než se začnete učit o trvalosti, rychle uvidíte, jak tyto obrázky sdílet s ostatními.

## <a name="next-steps"></a>Další kroky

Pokračujte kurzem!

> [!div class="nextstepaction"]
> [Sdílení aplikace](share-your-app.md)
