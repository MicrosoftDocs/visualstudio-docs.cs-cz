---
title: Práce s úložištěm Git
description: Použití Gitu v Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 852B6A9D-AEFA-4EF4-A5DD-94A506019D20
ms.custom: video
ms.openlocfilehash: 31e38d728eb3c336b1d3160a920ef18055de1b1f
ms.sourcegitcommit: d485b18e46ec4cf08704b5a8d0657bc716ec8393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/17/2020
ms.locfileid: "97616298"
---
# <a name="working-with-git"></a>Práce s úložištěm Git

Git je distribuovaný systém správy verzí, který umožňuje týmům současně pracovat na stejných dokumentech. To znamená, že je k dispozici centrální server, který obsahuje všechny soubory, ale v případě, že je úložiště rezervováno z tohoto centrálního zdroje, je celé úložiště naklonováno na místní počítač.

V následujících částech se dozvíte, jak se Git dá použít pro správu verzí v Visual Studio pro Mac.

## <a name="git-version-control-menu"></a>Nabídka správy verzí Git

Následující obrázek znázorňuje možnosti poskytované Visual Studio pro Mac položkou nabídky správy verzí:

![Položka nabídky správy verzí](media/version-control-gitVersionControlMenu.png)

## <a name="push-and-pull"></a>Vložení a vyžádání

Doručování a přijímání je dvě z nejčastěji používaných akcí v rámci Gitu. Pokud chcete synchronizovat změny provedené jinými uživateli na vzdáleném úložišti, musíte si je **vyžádat** . To se provádí v Visual Studio pro Mac tak, že vyberete možnost Správa **verzí > aktualizace řešení**.

Po aktualizaci souborů, jejich Zkontrolování a potvrzení je musíte **Odeslat** do vzdáleného úložiště a umožnit tak ostatním uživatelům přístup k vašim změnám. To se provádí v Visual Studio pro Mac tím, že vyberete **řízení verze > nabízených změn**. Tím se zobrazí dialogové okno pro vložení, které vám umožní zobrazit potvrzené změny a vybrat větev, do které se má vložit:

![Dialog zobrazující větev, do které se má zapisovat](media/version-control-gitPush.png)

Změny můžete také potvrdit a nasdílet současně pomocí dialogového okna potvrzení:

![Možnost ukazující, jak provést současně zápis a nabízené oznámení.](media/version-control-commitPush.png)

## <a name="blame-log-and-merge"></a>Viny, log a Merge

V dolní části okna se zobrazí pět karet, jak je znázorněno níže:

![Karty správy verzí](media/version-control-gitTabs.png)

Tyto akce umožňují následující akce:

* **Source** – zobrazí soubor zdrojového kódu.
* **Změny** – zobrazí změnu kódu mezi místním souborem a základním souborem. Můžete také porovnat různé verze souboru z různých hodnot hash:

    ![Karta změny](media/version-control-gitChange.png)

* **Viny** – zobrazí uživatelské jméno uživatele přidruženého k jednotlivým oddílům kódu.
* **Log** – zobrazí všechna potvrzení, časy, kalendářní data, zprávy a uživatele zodpovědné za daný soubor:

    ![Karta protokol](media/version-control-gitLog.png)

* **Sloučení** – Tato možnost se dá použít, pokud při potvrzování práce dojde ke konfliktu sloučení. Zobrazuje vizuální znázornění změn provedených vámi a dalším vývojářem, což umožňuje čistě kombinovat oddíly kódu.

## <a name="switching-branches"></a>Přepínání větví

Ve výchozím nastavení se první větev vytvořená v úložišti nazývá **Hlavní** větev. Mezi hlavní větví a žádnou jinou není nic jiného, ale hlavní větev je ta, která se nejčastěji myslela ve vývojových týmech jako "živá" nebo "produkční" větev.

Nezávislá čára vývoje se dá vytvořit vyskočím z hlavního (nebo jakékoli jiné větve) pro danou problematiku. To poskytuje novou verzi hlavní větve v určitém časovém okamžiku, což umožňuje vývoj nezávisle na tom, co je Live. Použití větví tímto způsobem se často používá k funkcím vývoje softwaru.

Uživatelé můžou pro každé úložiště vytvořit libovolný počet větví, ale doporučuje se, aby po dokončení používání větve ho odstranili, aby se úložiště zachovalo.

Větve se zobrazují v Visual Studio pro Mac procházením **správy verzí > správě větví a vzdálených...**:

![Zobrazení větví](media/version-control-gitBranch2.png)

Přepněte na jinou větev tak, že ji vyberete v seznamu a stisknete tlačítko **Přepnout na větev** .

Pokud chcete vytvořit novou větev, vyberte v dialogovém okně konfigurace úložiště Git tlačítko **Nový** . Zadejte název nové větve:

![Vytvořit novou větev](media/version-control-gitBranch.png)

Můžete také nastavit vzdálenou větev na _sledovací_ větev. Přečtěte si další informace o sledovacích větvích v [dokumentaci k Gitu](https://git-scm.com/book/en/v2/Git-Branching-Remote-Branches#Tracking-Branches).

Zobrazit aktuální větev v Oblast řešení vedle názvu projektu:

 ![Aktuální větev zobrazená na panelu řešení](media/version-control-gitBranchName.png)

## <a name="reviewing-and-committing"></a>Kontrola a potvrzování

Chcete-li zkontrolovat změny v souborech, použijte karty změny, viny, protokol a sloučení u každého dokumentu, který je znázorněn dříve v tomto tématu.

Zkontrolujte všechny změny v projektu, a to tak, že přejdete na **řízení verze > revize řešení a potvrzení** položky nabídky:

![Zkontrolovat zobrazení kódu](media/version-control-gitReviewCommit.png)

To umožňuje zobrazení všech změn v každém souboru projektu s možností vrácení, vytvoření opravy nebo potvrzení změn.

Pokud chcete soubor potvrdit do vzdáleného úložiště, stiskněte **Potvrdit**, zadejte potvrzovací zprávu a potvrďte tlačítko Potvrdit:

![Potvrzení souboru](media/version-control-gitCommit.png)

Jakmile provedete změny, nahrajte je do vzdáleného úložiště a umožněte ostatním uživatelům, aby je viděli.

## <a name="related-video"></a>Související video

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Manage-Projects-with-Git/player]

## <a name="see-also"></a>Viz také

* [Sdílejte kód se sadou Visual Studio 2017 a Azure Repos Git](/azure/devops/repos/git/share-your-code-in-git-vs-2017)