---
title: Práce s Gitem
description: Pomocí Git ve Visual Studio pro Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.openlocfilehash: 10d5b34ece7d093a42bafc1f0e410b670dd342f1
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296447"
---
# <a name="working-with-git"></a>Práce s Gitem

Git je distribuovaný systém správy verzí, který umožňuje týmům pracovat současně na stejném dokumenty. To znamená, že je centrálního serveru, který obsahuje všechny soubory, ale pokud úložiště je rezervován z tohoto centrální zdroje, je v místním počítači klonovat celé úložiště.

Následující části prozkoumá, jak lze použít Git pro správu verzí v sadě Visual Studio pro Mac.

## <a name="git-version-control-menu"></a>Nabídka řízení verzí Git

Následující obrázek ukazuje možnosti poskytovaný sadou Visual Studio for Mac pomocí položky nabídky správy verzí:

![Položka nabídky ovládací prvek verze](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Nabízená a vyžádaná instalace

Odesílání a stahování jsou dvě nejběžnější akce v rámci Git. Pokud chcete synchronizovat změny provedené jinými uživateli do vzdáleného úložiště, musíte **o přijetí změn** z něj. To se provádí v sadě Visual Studio pro Mac tak, že vyberete **verzí > aktualizace řešení**.

Po aktualizaci souborů, zkontrolovat a potvrzené je, pak musíte **Push** do vzdáleného úložiště umožňuje ostatním přístup k provedené změny. To se provádí v sadě Visual Studio pro Mac tak, že vyberete **verzí > Push změny**. To bude zobrazení dialogu, abyste mohli zobrazit potvrzené změny a vyberte této větve vložíte do:

![Dialogové okno zobrazující větve se zapsat do](media/version-control-gitPush.png)

Můžete také potvrďte a odešlete změny ve stejnou dobu, přes dialogové okno potvrzení:

![Možnost ukazující, jak potvrďte a odešlete ve stejnou dobu.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Příčin, protokolu a slučování

V dolní části okna je pět záložek, které se zobrazí, jak je znázorněno níže:

![Verze ovládacího prvku karty](media/version-control-gitTabs.png)

Tyto rutiny umožňují následující akce:

* **Zdroj** -zobrazí souboru zdrojového kódu.
* **Změny** -zobrazí změny v kódu mezi místním souborem a základního souboru. Můžete také porovnat různé verze souboru z různých hodnot hash:

    ![Karta změny](media/version-control-gitChange.png)

* **Jedná se o výsledek** -zobrazí uživatelské jméno uživatele spojené s každou část kódu.
* **Protokol** -zobrazí všechny potvrzení změn, časy, kalendářní data, zprávy a uživatele, kteří jsou zodpovědní za soubor:

    ![Karta protokolu](media/version-control-gitLog.png)

* **Sloučení** – to je možné, pokud máte konfliktu při slučování při práci. Zobrazí vizuální znázornění změny, které vás a ostatní vývojáři a díky tomu můžete kombinovat čistě oba oddíly kódu.

## <a name="switching-branches"></a>Přepínání větví

Ve výchozím nastavení, se nazývá první větev vytvořená v úložišti **hlavní** větve. Není technicky nic jiného mezi hlavní větve a jakékoli jiné, ale hlavní větev je ten, který je nejčastěji považovat za v vývojové týmy "live" nebo "produkční" větve.

Nezávislé řádku vývoje mohou vytvořit větvení Master (nebo jakékoli větve, k tomuto účelu). To poskytuje novou verzi hlavní větve v bodě v čase, umožňující vývoj bez ohledu na jejich, co je "live". Použití větví tímto způsobem se často používá pro funkce ve vývoji softwaru

Uživatelé můžou vytvářet libovolný počet větví, jako jsou pro každé úložiště, ale doporučuje se, že po jejich dokončení pomocí větev, odstraní se tak zachovat úložiště uspořádané.

Větve jsou zobrazeny v sadě Visual Studio pro Mac tak, že přejdete do **verzí > Spravovat větve a vzdálené větve...** :

![Zobrazit větve](media/version-control-gitBranch2.png)

Přepnout na jinou větev tak, že ji vyberete v seznamu a stisknutím klávesy **přepnout na větev** tlačítko.

Chcete-li vytvořit novou větev vyberte **nový** tlačítko v dialogu konfigurace úložiště Git. Zadejte nový název větve:

![Vytvořit novou větev](media/version-control-gitBranch.png)

Můžete také nastavit vzdálené větve vašeho _sledování_ větve. Další informace o sledování větví ve [dokumentace pro Git](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zobrazit aktuální větve v oblasti řešení, vedle názvu projektu:

 ![Aktuální větve, které jsou zobrazeny v oblasti řešení](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Kontrola a potvrzení

Zkontrolovat změny v souborech, použít změny, viny, protokol a sloučit kartách na jednotlivých dokumentů, které jsou znázorněné výše v tomto tématu.

Zkontrolujte všechny změny ve vašem projektu tak, že přejdete na **verzí > řešení zkontrolujte a potvrďte změny** položky nabídky:

![Zobrazení revize kódu](media/version-control-gitReviewCommit.png)

To umožňuje zobrazení všech změn v každém souboru projektu se možnost vrátit zpět, vytvořit opravu nebo použití.

Chcete-li zapsat soubor do vzdáleného úložiště, stiskněte **potvrzení**, zadejte zprávu potvrzení a potvrďte tlačítkem potvrzení:

![Potvrzují se soubor](media/version-control-gitCommit.png)

Jakmile máte potvrzené změny, jejich doručování do vzdáleného úložiště, chcete-li umožnit dalším uživatelům k jejich zobrazení.

## <a name="see-also"></a>Viz také:

* [Sdílení kódu pomocí sady Visual Studio 2017 a Azure úložišť Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)