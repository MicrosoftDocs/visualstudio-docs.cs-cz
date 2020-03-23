---
title: Vytváření nových projektů a řešení
description: Tento článek popisuje, jak vytvářet projekty a řešení v Sadě Visual Studio pro Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/23/2019
ms.assetid: 5880BB10-0A12-47E2-8A82-7A2D59C4D579
ms.openlocfilehash: 10fcb52a8e1311f3e8128361ee835f6ddcb3670d
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75678879"
---
# <a name="create-a-new-project"></a>Vytvoření nového projektu

## <a name="opening-the-project-creation-dialog"></a>Otevření dialogového okna Vytvoření projektu

Existuje několik způsobů, jak vytvořit nový projekt v Visual Studiu pro Mac. Při prvním otevření visual studia pro Mac se zobrazí počáteční okno. Zde si můžete vybrat **Nový,** který vás přenese na obrazovku tvorby projektu.

> [!TIP]
> Kromě toho můžete z počátečního okna také otevřít a vyhledat nedávné projekty a řešení. Nedávné projekty můžete otevřít také tak, že přejdete na řádek nabídek a zvolíte **Soubor > poslední řešení.**

![Počáteční okno s vytvořením nového projektu](media/first-run-project.png)

Pokud je Visual Studio pro Mac již otevřené s načteným řešením, můžete vytvořit nové řešení tak, že přejdete na řádek nabídek a zvolíte **Soubor > nové řešení**. Vytvoření nového řešení tímto způsobem zavře řešení, které je již načteno.

## <a name="creating-a-new-project-from-a-template"></a>Vytvoření nového projektu ze šablony

V dialogovém okně **Nový projekt** se ve výchozím nastavení zobrazí naposledy použité šablony seřazené podle *naposledy použitých šablon*.

Pokud nechcete používat poslední šablonu, můžete si vybrat z kategorií nalevé straně dialogového okna. Každá kategorie obsahuje několik šablon projektu, ze kterých si můžete vybrat. Kliknutím na typ projektu můžete zobrazit popis na pravé straně obrazovky.

![Obrazovka Nového projektu](media/project-creation-screen.png)

## <a name="configuring-your-new-project"></a>Konfigurace nového projektu

Po výběru šablony projektu vás následující obrazovky provedou všemi konfiguračními kroky potřebnými k nastavení projektu. to se může lišit podle typu projektu.

Všechny projekty vyžadují nový projekt, spolu s umístěním pro uložení souborů. Pokud je projekt součástí nového řešení, nikoli přidání mů e existující řešení, bude také vyžadován název řešení.

Volitelně můžete v této fázi také nakonfigurovat možnosti správy zdrojového kódu Git. Následující obrázek je příkladem konečného kroku konfigurace pro projekt .NET Core:

![Konfigurace nového projektu](media/configure-new-project.png)

## <a name="adding-additional-projects-to-a-solution"></a>Přidání dalších projektů do řešení

Další projekty můžete přidat do řešení tak, že kliknete pravým tlačítkem myši na řešení v panelu řešení a zvolíte **přidat > Přidat nový projekt** nebo Přidat > Přidat existující **projekt**.

Přidánínového projektu vás provede vytvořením projektu, jak je znázorněno v [na obrázku Konfigurace nového projektu](#configuring-your-new-project).

Pokud se rozhodnete přidat existující projekt, umožníte vám vyhledat existující projekt v počítači a přidat jej do řešení.

## <a name="see-also"></a>Viz také

- [Vytváření řešení a projektů (Visual Studio ve Windows)](/visualstudio/ide/creating-solutions-and-projects)
