---
title: Vytváření nových projektů a řešení
description: Tento článek popisuje, jak vytvořit projekty a řešení v Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: fa77993892c79cf29d268aa942b8c77ccb7a2139
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183951"
---
# <a name="create-a-new-project"></a>Vytvořit nový projekt

## <a name="opening-the-project-creation-dialog"></a>Otevření dialogového okna pro vytvoření projektu

Existuje několik způsobů, jak vytvořit nový projekt v Visual Studio pro Mac. Při prvním otevření Visual Studio pro Mac se zobrazí okno Start. Odsud můžete zvolit **Nový** , který vás přesměruje na obrazovku pro vytvoření projektu.

> [!TIP]
> Kromě toho můžete z okna Start také otevřít a vyhledat poslední projekty a řešení. Můžete také otevřít poslední projekty tak, že na řádku nabídek kliknete a zvolíte **soubor > poslední řešení** .

![Spustit okno s vytvořením nového projektu](media/first-run-project.png)

Pokud je už Visual Studio pro Mac otevřený pomocí načtené řešení, můžete vytvořit nové řešení tak, že na řádku nabídek kliknete a zvolíte **soubor > nové řešení**. Vytvoření nového řešení tímto způsobem ukončí již načtené řešení.

## <a name="creating-a-new-project"></a>Vytvoření nového projektu

V dialogovém okně **Nový projekt** se ve výchozím nastavení zobrazí vaše naposledy použité šablony seřazené podle *naposledy použitých*šablon.

Pokud nechcete používat poslední šablonu, můžete vybrat z kategorií na levé straně dialogového okna. Každá kategorie obsahuje několik šablon projektů, ze kterých si můžete vybrat. Kliknutí na typ projektu umožňuje zobrazit popis na pravé straně obrazovky.

![Obrazovka nový projekt](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurace nového projektu

Jakmile zvolíte šablonu projektu, následující obrazovky vás provedou všemi kroky konfigurace potřebnými k nastavení projektu. může se lišit podle typu projektu.

Všechny projekty vyžadují nový projekt společně s umístěním pro uložení souborů. Pokud je projekt součástí nového řešení, místo aby ho bylo možné přidat k existujícímu řešení, bude také požadován název řešení.

Volitelně můžete v této fázi nakonfigurovat také možnosti správy zdrojového kódu Git. Následující obrázek je příkladem finálního kroku konfigurace pro projekt .NET Core:

![Konfigurace nového projektu](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Do řešení můžete přidat další projekty tak, že kliknete pravým tlačítkem na řešení v Oblast řešení a zvolíte buď **přidat > přidat nový projekt** , nebo **Přidat > přidat existující projekt**.

Přidání nového projektu vás provede vytvořením projektu, jak je znázorněno v [konfiguraci nového projektu](#configuring-your-new-project).

Zvolíte-li možnost Přidat existující projekt, budete moci na svém počítači vyhledat existující projekt a přidat ho do řešení.

## <a name="see-also"></a>Viz také

- [Vytváření řešení a projektů (Visual Studio ve Windows)](/visualstudio/ide/creating-solutions-and-projects)
